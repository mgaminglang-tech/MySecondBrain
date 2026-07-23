---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - requirements
  - lead-qualification
---

# Requirements

## Discovery Summary

- Business problem: Manual completeness review, qualification, and forwarding slows lead handling and creates inconsistent decisions.
- Current process: A salesperson reviews each lead and decides what to do.
- Desired v0.1 outcome: Return a consistent, side-effect-free qualification result plus prepared routing, storage, and notification payloads.
- Stakeholders: Project Owner, Automation Engineer, and future sales operations users.
- Decision owners: Project Owner and Automation Engineer.
- Expected DEV volume: Up to 100 dummy test leads per day.
- Processing target: Under two seconds per lead.

## Scope

### Included

- Manual Trigger and dummy data in an inactive DEV workflow.
- Normalization, validation, scoring, status assignment, queue routing, payload preparation, and final output.
- Deterministic `lead_id` and email-derived `idempotency_key`.
- Explainable validation, normalization, scoring, assignment, and review reason codes.

### Not Included

- Airtable or Google Sheets writes.
- Email or Telegram sends.
- Historical duplicate lookup or persistent state.
- External API retries, concurrency controls, automatic triggers, STAGING, PROD, enrichment, or CRM synchronization.
- Real personal or client data.

## Functional Requirements

| ID | Requirement | Priority | Acceptance criterion | Owner |
|---|---|---|---|---|
| FR-001 | Accept one complete dummy lead through Manual Trigger and Set Sample Lead. | high | One object reaches Normalize Input; no external trigger exists. | Automation Engineer |
| FR-002 | Normalize approved string and enum fields without inventing missing values or coercing invalid types. | high | Output follows the normalization rules below and emits warning codes. | Automation Engineer |
| FR-003 | Validate every required input against the approved contract. | high | Output contains `validation_status` and machine-readable `validation_errors`. | Project Owner |
| FR-004 | Generate `lead_id` and `idempotency_key`. | high | Key equals `email:<normalized_email>`; no lookup is performed. | Automation Engineer |
| FR-005 | Score only valid leads using the approved 100-point model. | high | Score equals the sum of five rule results and includes exact reason codes. | Project Owner |
| FR-006 | Assign `invalid`, `qualified`, `nurture`, or `unqualified`. | high | Status follows validation first, then the approved score ranges. | Project Owner |
| FR-007 | Route by normalized region. | high | Approved regions map to the exact queue; unsupported or missing regions use General Sales Queue and human review. | Project Owner |
| FR-008 | Prepare a destination-neutral storage payload without writing it. | high | `operation` is `prepare_only` and `write_requested` is `false`. | Automation Engineer |
| FR-009 | Prepare a plain-text notification payload without sending it. | high | `operation` is `prepare_only`, `send_requested` is `false`, and no channel credential is referenced. | Automation Engineer |
| FR-010 | Return the complete final output contract. | high | All required top-level fields in [[Architecture]] are present with approved types. | Automation Engineer |
| FR-011 | Remain inactive and side-effect free. | high | Execution uses dummy data, no credentials, no persistent lookup, no write, and no send. | Project Owner |

## Required Input Contract

All fields are required. Invalid types are not coerced into valid types.

| Field | Required type and rule | Normalization |
|---|---|---|
| `full_name` | String, 2–100 characters after trimming | Trim and collapse repeated internal whitespace |
| `email` | String, valid email, maximum 254 characters | Trim and lowercase |
| `company` | String, 2–120 characters after trimming | Trim and collapse repeated internal whitespace |
| `role` | `owner`, `founder`, `executive`, `director`, `manager`, `staff`, or `other` | Trim and lowercase before enum validation |
| `budget_usd` | Number from 0 through 1,000,000 | No string-to-number coercion |
| `timeframe_days` | Integer from 1 through 365 | No string-to-number coercion |
| `product_interest` | `automation`, `website`, `ai-agent`, `consulting`, or `other` | Trim and lowercase |
| `region` | `APAC`, `North America`, `Europe`, or `Other` | Trim and case-insensitively canonicalize approved values |
| `message` | String, 20–2,000 characters after trimming | Trim; preserve meaningful internal whitespace |
| `consent` | Boolean literal `true` | No truthy or string coercion |
| `source` | `website`, `referral`, `email`, `social`, or `other` | Trim and lowercase |
| `submitted_at` | Valid ISO-8601 UTC timestamp ending in `Z` | Parse and output canonical UTC ISO string |

Character counts use Unicode characters after the documented trimming step.

## Validation Contract

`validation_status` is `valid` or `invalid`. Each error is:

```json
{"field":"FIELD_NAME","code":"REASON_CODE","message":"SAFE_DESCRIPTION"}
```

Approved reason codes are `REQUIRED_FIELD`, `INVALID_TYPE`, `STRING_LENGTH_OUT_OF_RANGE`, `INVALID_EMAIL_FORMAT`, `INVALID_ENUM`, `NUMBER_OUT_OF_RANGE`, `INTEGER_REQUIRED`, `INVALID_TIMESTAMP_UTC`, and `CONSENT_NOT_TRUE`.

Normalization warnings use `{field, code}` with approved codes `TRIMMED_WHITESPACE`, `COLLAPSED_WHITESPACE`, `LOWERCASED_VALUE`, `CANONICALIZED_ENUM`, `CANONICALIZED_TIMESTAMP`, `POTENTIAL_SPREADSHEET_FORMULA`, and `POTENTIAL_CHANNEL_MARKUP`.

## Proposed Scoring Rules

Scoring applies only after validation output exists. An invalid lead remains `invalid` regardless of points.

| Rule | Condition | Points |
|---|---|---:|
| Role | `owner`, `founder`, `executive`, or `director` = 25; `manager` = 15; `staff` or `other` = 5 | 5–25 |
| Budget | 5,000+ = 25; 2,000–4,999 = 15; 500–1,999 = 5; below 500 = 0 | 0–25 |
| Timeframe | 1–30 = 20; 31–60 = 15; 61–90 = 10; over 90 = 5 | 5–20 |
| Need clarity | At least 40 characters and contains an approved keyword = 20; otherwise = 5 | 5 or 20 |
| Business email | Domain is not on the free-email list = 10; listed free-email domain = 0 | 0 or 10 |

Approved business-need keywords, matched case-insensitively as whole words: `automation`, `automate`, `workflow`, `integration`, `leads`, `sales`, `support`, `reporting`, `booking`, `operations`.

Approved free-email domains, matched exactly after lowercasing: `gmail.com`, `yahoo.com`, `outlook.com`, `hotmail.com`, `icloud.com`.

Approved score reason codes:

- Role: `ROLE_SENIOR_25`, `ROLE_MANAGER_15`, `ROLE_OTHER_5`
- Budget: `BUDGET_5000_PLUS_25`, `BUDGET_2000_4999_15`, `BUDGET_500_1999_5`, `BUDGET_BELOW_500_0`
- Timeframe: `TIMEFRAME_1_30_20`, `TIMEFRAME_31_60_15`, `TIMEFRAME_61_90_10`, `TIMEFRAME_91_365_5`
- Need: `NEED_CLEAR_20`, `NEED_NOT_CLEAR_5`
- Email: `BUSINESS_EMAIL_10`, `FREE_EMAIL_0`
- Invalid input: `SCORING_SKIPPED_INVALID_INPUT`

Proposed statuses:

- `invalid`: A required field is missing or invalid, or consent is not explicitly true.
- `qualified`: Valid and score is 70–100.
- `nurture`: Valid and score is 40–69.
- `unqualified`: Valid and score is 0–39.

For invalid leads, `score` is `null`, `score_reasons` contains only `SCORING_SKIPPED_INVALID_INPUT`, and `needs_human_review` is `true`.

Because every valid lead earns at least 15 points and each scoring increment is divisible by five, some values inside the status ranges are not attainable. The ranges remain authoritative; boundary tests use attainable values 70, 65, 40, and 35.

## Routing and Review Contract

| Normalized region | Assigned queue | Assignment reason |
|---|---|---|
| `APAC` | `APAC Sales Queue` | `REGION_APAC` |
| `North America` | `North America Sales Queue` | `REGION_NORTH_AMERICA` |
| `Europe` | `Europe Sales Queue` | `REGION_EUROPE` |
| `Other` | `General Sales Queue` | `REGION_OTHER` |
| Missing or unsupported | `General Sales Queue` | `REGION_FALLBACK_REVIEW` |

Missing or unsupported routing is also invalid under the input contract and sets `needs_human_review: true`. All other valid leads set `needs_human_review: false`.

## Non-Functional Requirements

- Determinism: Same normalized input and workflow version produces the same validation, score, status, queue, and payload content except `processed_at`.
- Performance: Under two seconds per lead at up to 100 manual DEV test leads per day.
- Security: No credentials, integrations, real client data, or side effects in v0.1.
- Privacy: Dummy data only; DEV execution logs retained for seven days.
- Recovery: Simulated RTO four hours and simulated RPO 24 hours.
- Ownership: Project Owner and Automation Engineer approve and operationally review v0.1.

## Error and Exception Requirements

- Missing or invalid input: Return a complete final object with `invalid`, `score: null`, validation errors, General Sales Queue where routing is unavailable, and human review.
- Empty input: Return controlled `REQUIRED_FIELD` errors for all required fields.
- Transformation exception: Stop the manual DEV execution and record a sanitized issue; v0.1 has no automatic retry.
- Potential spreadsheet formula or channel markup: Preserve the normalized value as data, emit a normalization warning, and set the relevant payload escape flag.
- Historical duplicate lookup, storage failure, delivery failure, retries, concurrency, and reconciliation are deferred to v0.2.

## Success and Acceptance Criteria

- [ ] Every executable v0.1 case in [[Test Plan]] passes with recorded evidence.
- [ ] Exact scoring fixtures return the documented totals and reason codes.
- [ ] Invalid fixtures return `score: null`, machine-readable errors, and human review.
- [ ] Every final output contains all required top-level fields and correct types.
- [ ] Every prepared storage payload has `write_requested: false`.
- [ ] Every prepared notification payload has `send_requested: false`.
- [ ] No credentials, persistent lookup, external calls, STAGING, or PROD resources exist in v0.1.
- [ ] Measured DEV processing time is under two seconds per lead.
- [ ] Project Owner and Automation Engineer record their review decision.

## Deferred to v0.2

- Select Airtable or Google Sheets and define schemas, escaping, upsert, and historical duplicate behavior.
- Select Email or Telegram and define channel escaping, recipients, delivery evidence, and retries.
- Add persistent duplicate lookup, concurrency control, side effects, external API retry policy, reconciliation, and integration-specific error handling.
- Decide whether v0.2 needs STAGING and PROD.

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[Architecture]]
- [[Test Plan]]
- [[Credentials Checklist]]
- [[Known Limitations]]
