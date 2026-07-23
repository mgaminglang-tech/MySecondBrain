---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - testing
  - lead-qualification
---

# Test Plan

## Objective

Define exact, repeatable v0.1 DEV tests and keep all v0.2 integration tests visibly deferred.

## v0.1 Test Environment

- Environment: DEV only.
- Workflow state: Inactive; manual execution only.
- Workflow version: `v0.1.0`.
- Data: Dummy only.
- Credentials and external destinations: None.
- Volume: Up to 100 test leads per day.
- Processing target: Under two seconds per lead.
- Execution-log retention: Seven days.
- Current execution status: All tests `not-run`.

## Base Dummy Fixture

Unless a case overrides a field:

```json
{
  "full_name": "Alex Rivera",
  "email": "alex.rivera@acme.example",
  "company": "Acme Demo Company",
  "role": "other",
  "budget_usd": 0,
  "timeframe_days": 365,
  "product_interest": "automation",
  "region": "APAC",
  "message": "We need workflow automation for sales reporting operations.",
  "consent": true,
  "source": "referral",
  "submitted_at": "2026-07-23T12:00:00Z"
}
```

This base fixture scores 40: role 5 + budget 0 + timeframe 5 + clear need 20 + business email 10.

## Core and Schema Tests

| ID | Override or scenario | Exact expected result |
|---|---|---|
| TC-001 | `role: owner`, `budget_usd: 5000`, `timeframe_days: 30` | `score: 100`; five reasons `ROLE_SENIOR_25`, `BUDGET_5000_PLUS_25`, `TIMEFRAME_1_30_20`, `NEED_CLEAR_20`, `BUSINESS_EMAIL_10`; `qualified`; APAC Sales Queue; review false |
| TC-002 | TC-001 complete output | Exactly the 16 top-level keys defined in [[Architecture]]; correct types; `workflow_version: v0.1.0` |
| TC-003 | Email `" ALEX.RIVERA@ACME.EXAMPLE "` and padded name/company | Email becomes `alex.rivera@acme.example`; strings trim/collapse; warning codes identify each normalization |
| TC-004 | TC-001 identity | `idempotency_key: email:alex.rivera@acme.example`; deterministic dummy `lead_id` contains normalized email and compact submitted UTC |
| TC-005 | Any invalid fixture | `validation_status: invalid`; `score: null`; only score reason `SCORING_SKIPPED_INVALID_INPUT`; `qualification_status: invalid`; review true |
| TC-006 | Valid qualified fixture payloads | Storage has `operation: prepare_only`, `write_requested: false`, `destination: null`; notification has `operation: prepare_only`, `send_requested: false`, `channel: null`, `content_type: text/plain`, `notification_required: true`, and `priority: high` |

## Role Scoring Tests

All other base fields remain unchanged. Expected total equals role points plus 35.

| ID | Role | Role reason | Exact total |
|---|---|---|---:|
| TC-010 | owner | `ROLE_SENIOR_25` | 60 |
| TC-011 | founder | `ROLE_SENIOR_25` | 60 |
| TC-012 | executive | `ROLE_SENIOR_25` | 60 |
| TC-013 | director | `ROLE_SENIOR_25` | 60 |
| TC-014 | manager | `ROLE_MANAGER_15` | 50 |
| TC-015 | staff | `ROLE_OTHER_5` | 40 |
| TC-016 | other | `ROLE_OTHER_5` | 40 |

## Budget Scoring Tests

All other base fields remain unchanged. Expected total equals budget points plus 40.

| ID | Budget | Budget reason | Exact total |
|---|---:|---|---:|
| TC-020 | 5000 | `BUDGET_5000_PLUS_25` | 65 |
| TC-021 | 1000000 | `BUDGET_5000_PLUS_25` | 65 |
| TC-022 | 4999 | `BUDGET_2000_4999_15` | 55 |
| TC-023 | 2000 | `BUDGET_2000_4999_15` | 55 |
| TC-024 | 1999 | `BUDGET_500_1999_5` | 45 |
| TC-025 | 500 | `BUDGET_500_1999_5` | 45 |
| TC-026 | 499 and 0 | `BUDGET_BELOW_500_0` | 40 |

## Timeframe Scoring Tests

All other base fields remain unchanged except timeframe. Expected total equals timeframe points plus 35.

| ID | Days | Timeframe reason | Exact total |
|---|---:|---|---:|
| TC-030 | 1 | `TIMEFRAME_1_30_20` | 55 |
| TC-031 | 30 | `TIMEFRAME_1_30_20` | 55 |
| TC-032 | 31 | `TIMEFRAME_31_60_15` | 50 |
| TC-033 | 60 | `TIMEFRAME_31_60_15` | 50 |
| TC-034 | 61 | `TIMEFRAME_61_90_10` | 45 |
| TC-035 | 90 | `TIMEFRAME_61_90_10` | 45 |
| TC-036 | 91 | `TIMEFRAME_91_365_5` | 40 |
| TC-037 | 365 | `TIMEFRAME_91_365_5` | 40 |

## Need-Clarity Tests

| ID | Message condition | Need reason | Exact score |
|---|---|---|---:|
| TC-040 | 40+ characters containing whole-word `automation` | `NEED_CLEAR_20` | 40 |
| TC-041 | 40+ characters containing uppercase `WORKFLOW` | `NEED_CLEAR_20` | 40 |
| TC-042 | 40+ characters with no approved keyword | `NEED_NOT_CLEAR_5` | 25 |
| TC-043 | 20–39 characters containing `sales` | `NEED_NOT_CLEAR_5` | 25 |
| TC-044 | Contains `automated` but no approved whole-word keyword | `NEED_NOT_CLEAR_5` | 25 |

## Email Scoring Tests

| ID | Domain | Email reason | Exact score |
|---|---|---|---:|
| TC-050 | gmail.com | `FREE_EMAIL_0` | 30 |
| TC-051 | yahoo.com | `FREE_EMAIL_0` | 30 |
| TC-052 | outlook.com | `FREE_EMAIL_0` | 30 |
| TC-053 | hotmail.com | `FREE_EMAIL_0` | 30 |
| TC-054 | icloud.com | `FREE_EMAIL_0` | 30 |
| TC-055 | acme.example | `BUSINESS_EMAIL_10` | 40 |

## Status Boundary Tests

Every fixture is valid. Scores 69 and 39 are not attainable because all approved increments are multiples of five.

| ID | Score composition | Exact status |
|---|---|---|
| TC-060 | 25 + 15 + 15 + 5 + 10 = 70 | `qualified` |
| TC-061 | 25 + 15 + 10 + 5 + 10 = 65 | `nurture` |
| TC-062 | 5 + 0 + 5 + 20 + 10 = 40 | `nurture` |
| TC-063 | 15 + 0 + 5 + 5 + 10 = 35 | `unqualified` |

## Individual Missing-Field Tests

Each case removes exactly one field. Expected for every case: `invalid`, `score: null`, `SCORING_SKIPPED_INVALID_INPUT`, review true, and one `{field, code: REQUIRED_FIELD}` error.

| ID | Missing field |
|---|---|
| TC-070 | `full_name` |
| TC-071 | `email` |
| TC-072 | `company` |
| TC-073 | `role` |
| TC-074 | `budget_usd` |
| TC-075 | `timeframe_days` |
| TC-076 | `product_interest` |
| TC-077 | `region`; additionally General Sales Queue and `REGION_FALLBACK_REVIEW` |
| TC-078 | `message` |
| TC-079 | `consent` |
| TC-080 | `source` |
| TC-081 | `submitted_at` |

## Consent, Timestamp, Type, and Range Tests

| ID | Input | Exact expected error |
|---|---|---|
| TC-082 | `consent: false` | `consent / CONSENT_NOT_TRUE` |
| TC-083 | `consent: "true"` | `consent / INVALID_TYPE` |
| TC-084 | `consent: 1` | `consent / INVALID_TYPE` |
| TC-085 | `submitted_at: 2026-07-23T12:00:00Z` | Valid; normalized to `2026-07-23T12:00:00.000Z` |
| TC-086 | Timestamp with `+08:00` offset | `submitted_at / INVALID_TIMESTAMP_UTC` |
| TC-087 | Date only or malformed timestamp | `submitted_at / INVALID_TIMESTAMP_UTC` |
| TC-088 | Impossible calendar date | `submitted_at / INVALID_TIMESTAMP_UTC` |
| TC-089 | Numeric fields supplied as strings | `budget_usd / INVALID_TYPE` and/or `timeframe_days / INVALID_TYPE` |
| TC-090 | `budget_usd: -1` or `1000001` | `budget_usd / NUMBER_OUT_OF_RANGE` |
| TC-091 | `timeframe_days: 1.5` | `timeframe_days / INTEGER_REQUIRED` |
| TC-092 | `timeframe_days: 0` or `366` | `timeframe_days / NUMBER_OUT_OF_RANGE` |

## Routing Tests

| ID | Region | Exact queue and reason | Review |
|---|---|---|---|
| TC-100 | APAC | APAC Sales Queue / `REGION_APAC` | false |
| TC-101 | North America | North America Sales Queue / `REGION_NORTH_AMERICA` | false |
| TC-102 | Europe | Europe Sales Queue / `REGION_EUROPE` | false |
| TC-103 | Other | General Sales Queue / `REGION_OTHER` | false |
| TC-104 | Unknown or unsupported | General Sales Queue / `REGION_FALLBACK_REVIEW`; invalid enum | true |

## Length, Injection, and Safety Tests

| ID | Scenario | Exact expected result |
|---|---|---|
| TC-110 | Message length 19 | `message / STRING_LENGTH_OUT_OF_RANGE`; invalid; score null |
| TC-111 | Message length 20 | Valid; need reason `NEED_NOT_CLEAR_5` unless the complete clarity rule is met |
| TC-112 | Message length 2000 | Valid |
| TC-113 | Message length 2001 | `message / STRING_LENGTH_OUT_OF_RANGE`; invalid; score null |
| TC-114 | Company or message begins with `=`, `+`, `-`, or `@` | `POTENTIAL_SPREADSHEET_FORMULA`; storage `requires_destination_escaping: true`; text is not evaluated |
| TC-115 | Message contains HTML or Markdown control characters | `POTENTIAL_CHANNEL_MARKUP`; notification `requires_channel_escaping: true`; raw message absent from notification summary |
| TC-116 | Apostrophes, accents, hyphens, and non-Latin names within length | Preserved; no false validation error |

## Output, Determinism, and Failure Tests

| ID | Scenario | Exact expected result |
|---|---|---|
| TC-120 | Run the same valid fixture twice | Same normalized fields, ID, idempotency key, score, reasons, status, queue, and payload content; only runtime metadata may differ |
| TC-121 | Empty object | Twelve `REQUIRED_FIELD` errors; invalid; score null; General Sales Queue; review true |
| TC-122 | Null for every field | Twelve type or consent errors; invalid; score null; review true |
| TC-123 | Performance measurement | Each manual lead completes in under 2.000 seconds |
| TC-124 | Workflow inspection | Inactive; zero credentials; zero external trigger, lookup, write, or send nodes |
| TC-125 | Forced unexpected transformation exception | Manual execution fails; sanitized issue evidence recorded; no automatic retry |

## Deferred v0.2 Integration Tests

These are not executable v0.1 exit criteria and remain `deferred`.

| ID | Deferred test |
|---|---|
| DTC-001 | Airtable write, schema mapping, formula escaping, and upsert |
| DTC-002 | Google Sheets write, schema mapping, formula escaping, and upsert |
| DTC-003 | Email rendering, send, delivery evidence, escaping, and retry |
| DTC-004 | Telegram rendering, send, delivery evidence, escaping, and retry |
| DTC-005 | Historical duplicate lookup and duplicate policy |
| DTC-006 | Concurrent submissions and race control |
| DTC-007 | External API timeout, retry success, backoff, and exhaustion |
| DTC-008 | Permanent API error with no inappropriate retry |
| DTC-009 | Partial failure, reconciliation, and safe replay |

## Output Verification

- Exact score equals the sum represented by the five reason codes.
- Invalid input has `score: null` and cannot receive a valid-lead status.
- All 16 required top-level output keys and approved types are present.
- Storage and notification payloads explicitly disable writes and sends.
- Notification excludes the raw lead message.
- No credential, external destination, or real data is present.

## Entry Criteria

- [ ] [[Requirements]] and [[Architecture]] approved.
- [ ] Inactive DEV workflow is ready.
- [ ] Fixtures reviewed as dummy data.
- [ ] Expected values are calculated independently.
- [ ] Workflow contains no credentials or external destinations.

## Exit Criteria

- [ ] All executable TC cases pass with evidence.
- [ ] Failures are fixed or accepted explicitly.
- [ ] Results are recorded in [[Test Results]].
- [ ] [[Known Limitations]] and [[Issues and Fixes]] are current.
- [ ] Project Owner and Automation Engineer decisions are recorded.
- [ ] DTC cases remain deferred and do not block v0.1.

## Related Notes

- [[Requirements]]
- [[Architecture]]
- [[Test Results]]
- [[Issues and Fixes]]
