---
type: project-note
status: active
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
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
| FR-004 | Generate deterministic v0.1 `lead_id` and `idempotency_key` values for every result. | high | Valid identity inputs use the approved email/timestamp SHA-256 rule; missing or invalid identity inputs use the canonical raw-input fallback. | Automation Engineer |
| FR-005 | Score only valid leads using the approved 100-point model. | high | Score equals the sum of five rule results and includes exact reason codes. | Project Owner |
| FR-006 | Assign `invalid`, `qualified`, `nurture`, or `unqualified`. | high | Status follows validation first, then the approved score ranges. | Project Owner |
| FR-007 | Route by normalized region. | high | Approved regions map to the exact queue; unsupported or missing regions use General Sales Queue and human review. | Project Owner |
| FR-008 | Prepare a destination-neutral storage payload without writing it. | high | Payload uses `destination: deferred-v0.2`, `operation: none`, and the complete prepared record. | Automation Engineer |
| FR-009 | Prepare an internal notification preview without sending it. | high | Payload uses `channel: internal-preview` and the exact status-based required, priority, subject, and message rules. | Automation Engineer |
| FR-010 | Return the complete final output contract. | high | All required top-level fields in [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] are present with approved types. | Automation Engineer |
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

For v0.1, a valid email has exactly one `@`; a 1–64 character local part composed of non-empty dot-separated segments using ASCII letters, digits, or `!#$%&'*+/=?^_{}|~-`; and a domain containing at least two labels separated by dots. Each domain label is 1–63 ASCII letters, digits, or hyphens and cannot begin or end with a hyphen. The complete address cannot exceed 254 characters.

## Normalized Lead Contract

`normalized_lead` always contains all 12 input keys in the documented order. A missing field or a field that fails type, format, enum, range, timestamp, or consent validation is represented as `null`; fields are never omitted.

Normalization warnings are non-blocking only. A field that becomes `null` because it is invalid must have an exact validation error and must not be represented as successfully normalized.

Validation errors are ordered by the input contract field order. Normalization warnings are ordered first by input contract field order and then by event order: trim, collapse whitespace, lowercase, canonicalize enum, canonicalize timestamp, formula warning, channel-markup warning.

## Lead Identity Contract

SHA-256 outputs are lowercase 64-character hexadecimal strings.

When normalized email and normalized `submitted_at` are both valid:

```text
idempotency_key = SHA-256(normalized_email + "|" + submitted_at)
lead_id = "lead_" + first 16 hexadecimal characters of idempotency_key
```

When email or `submitted_at` is missing or invalid:

1. Create a canonical raw-input object containing all 12 input keys.
2. Sort keys alphabetically, including nested object keys if an invalid value is an object.
3. Trim string values but do not lowercase or otherwise normalize them.
4. Preserve explicit `null`; represent every missing field as `null`.
5. Serialize as compact UTF-8 JSON with no insignificant whitespace.

```text
idempotency_key = SHA-256("invalid|" + canonical_raw_input)
lead_id = "invalid_lead_" + first 16 hexadecimal characters of idempotency_key
```

These identifiers are deterministic for v0.1 tests only. They do not perform historical duplicate detection or provide concurrency protection.

## Validation Contract

`validation_status` is `valid` or `invalid`. Each error is:

```json
{"field":"FIELD_NAME","code":"REASON_CODE","message":"SAFE_DESCRIPTION"}
```

Approved reason codes are `REQUIRED_FIELD`, `INVALID_TYPE`, `STRING_LENGTH_OUT_OF_RANGE`, `INVALID_EMAIL_FORMAT`, `INVALID_ENUM`, `NUMBER_OUT_OF_RANGE`, `INTEGER_REQUIRED`, `INVALID_TIMESTAMP_UTC`, and `CONSENT_NOT_TRUE`.

Normalization warnings use `{field, code}` with approved codes `TRIMMED_WHITESPACE`, `COLLAPSED_WHITESPACE`, `LOWERCASED_VALUE`, `CANONICALIZED_ENUM`, `CANONICALIZED_TIMESTAMP`, `POTENTIAL_SPREADSHEET_FORMULA`, and `POTENTIAL_CHANNEL_MARKUP`.

## Approved Scoring Rules

Scoring applies only after validation output exists. An invalid lead remains `invalid` regardless of points.

| Rule | Condition | Points |
|---|---|---:|
| Role | `owner`, `founder`, `executive`, or `director` = 25; `manager` = 15; `staff` or `other` = 5 | 5–25 |
| Budget | `budget_usd >= 5000` = 25; `>= 2000 and < 5000` = 15; `>= 500 and < 2000` = 5; `>= 0 and < 500` = 0 | 0–25 |
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

Approved statuses:

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

## Prepared Payload Contract

`storage_payload` always contains exactly:

- `destination: "deferred-v0.2"`
- `operation: "none"`
- `record`: the complete prepared storage record defined in [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]]

`notification_payload` always contains `channel: "internal-preview"`, `notification_required`, `priority`, `subject`, and `message`.

| Qualification status | Required | Priority | Subject | Message |
|---|---|---|---|---|
| `qualified` | `true` | `high` | Non-empty string | Non-empty string |
| `invalid` | `true` | `high` | Non-empty string | Non-empty string |
| `nurture` | `false` | `none` | `null` | `null` |
| `unqualified` | `false` | `none` | `null` | `null` |

Every invalid result has `needs_human_review: true`. The notification preview never includes the raw lead `message`.

For qualified and invalid previews, use `Unknown Company` when normalized company is `null` and `unknown` when normalized product interest is `null`. The deterministic subject and message templates are defined in [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]].

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
- Potential spreadsheet formula or channel markup: Preserve a valid normalized value as data and emit the applicable non-blocking normalization warning. Destination-specific escaping remains deferred to v0.2.
- Historical duplicate lookup, storage failure, delivery failure, retries, concurrency, and reconciliation are deferred to v0.2.

## Success and Acceptance Criteria

### Controlled Demo Acceptance

- [x] The 25-test Core Release Suite in [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]] passed with recorded evidence.
- [x] Core results are 25 passed, 0 failed, and 0 blocked.
- [x] Exact demonstrated scoring fixtures returned the documented totals and reason codes.
- [x] Demonstrated invalid fixtures returned `score: null`, machine-readable errors, and human review.
- [x] The complete 16-key final-output contract and nested payload contracts were demonstrated.
- [x] Storage and notification payloads remained inert.
- [x] The workflow remained inactive and used dummy data, zero credentials, and no external integrations or side effects.
- [x] [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]] and deferred features are disclosed.

The 88-test Extended Regression Suite is not part of the controlled demo acceptance gate. It remains required before production deployment or after a major workflow change. The ten v0.2 integration tests remain deferred.

### Production and Project-Closure Requirements

- **Deferred:** Complete the Extended Regression Suite when required by the production or major-change gate.
- **Future production gate:** Verify the under-two-second target and seven-day log-retention configuration.
- **Future production gate:** Complete operational review and recovery evidence.
- **Future production gate:** Obtain client/owner approval.
- **Deferred:** Complete integration testing and production smoke testing for any future live design.
- **Future production gate:** Approve a separate production architecture, credentials plan, and deployment decision.

## Deferred to v0.2

- Select Airtable or Google Sheets and define schemas, escaping, upsert, and historical duplicate behavior.
- Select Email or Telegram and define channel escaping, recipients, delivery evidence, and retries.
- Add persistent duplicate lookup, concurrency control, side effects, external API retry policy, reconciliation, and integration-specific error handling.
- Decide whether v0.2 needs STAGING and PROD.

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]]
- [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]]
