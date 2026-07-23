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
  "submitted_at": "2026-07-23T12:00:00.000Z"
}
```

This base fixture scores 40: role 5 + budget 0 + timeframe 5 + clear need 20 + business email 10.

## Core and Schema Tests

| ID | Override or scenario | Exact expected result |
|---|---|---|
| TC-001 | Base plus `role: owner`, `budget_usd: 5000`, `timeframe_days: 30`; fixed clock `2026-07-23T12:00:01.000Z` | Exact authoritative JSON in [[Architecture]]; score 100; qualified; APAC Sales Queue; review false |
| TC-002 | TC-001 fixture and fixed clock | Exactly 16 top-level keys; storage keys exactly `destination`, `operation`, `record`; notification keys exactly `channel`, `notification_required`, `priority`, `subject`, `message`; nested values exactly match [[Architecture]] |
| TC-003 | Base plus `full_name: "  Alex   Rivera  "`, `email: "  ALEX.RIVERA@ACME.EXAMPLE  "`, `company: "  Acme   Demo Company  "`, `role: " OWNER "`, `product_interest: " AUTOMATION "`, `region: " apac "`, `source: " REFERRAL "`, `submitted_at: " 2026-07-23T12:00:00Z "` | Normalized values equal the base fixture; warnings in order: `full_name/TRIMMED_WHITESPACE`, `full_name/COLLAPSED_WHITESPACE`, `email/TRIMMED_WHITESPACE`, `email/LOWERCASED_VALUE`, `company/TRIMMED_WHITESPACE`, `company/COLLAPSED_WHITESPACE`, `role/TRIMMED_WHITESPACE`, `role/LOWERCASED_VALUE`, `role/CANONICALIZED_ENUM`, `product_interest/TRIMMED_WHITESPACE`, `product_interest/LOWERCASED_VALUE`, `product_interest/CANONICALIZED_ENUM`, `region/TRIMMED_WHITESPACE`, `region/CANONICALIZED_ENUM`, `source/TRIMMED_WHITESPACE`, `source/LOWERCASED_VALUE`, `source/CANONICALIZED_ENUM`, `submitted_at/TRIMMED_WHITESPACE`, `submitted_at/CANONICALIZED_TIMESTAMP` |
| TC-004 | Base fixture | `idempotency_key: 9d496fb34cf92660ac93d1de30328c4bef2417dc3cabc7c7ba54eddfc160956c`; `lead_id: lead_9d496fb34cf92660` |
| TC-005 | Base plus `role: "intern"` | `normalized_lead.role: null`; one `role/INVALID_ENUM` error; invalid; score null; only `SCORING_SKIPPED_INVALID_INPUT`; APAC Sales Queue; review true |
| TC-006 | TC-001 qualified fixture | Notification: `internal-preview`, required true, priority high, non-empty subject/message exactly matching [[Architecture]] |
| TC-007 | Base plus `role: owner`, `budget_usd: 2000`, `timeframe_days: 61`, `message: "Need sales workflow."` | Score 65; nurture; notification required false, priority none, subject null, message null |
| TC-008 | Base plus `role: manager`, `message: "Need sales workflow."`, `email: "alex.rivera@gmail.com"` | Score 25; unqualified; notification required false, priority none, subject null, message null |
| TC-009 | Base plus `role: "intern"` | Invalid; review true; notification required true, priority high, subject `Lead invalid: Acme Demo Company [lead_9d496fb34cf92660]`; non-empty message uses `not-scored` and excludes raw lead message |

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
| TC-020 | 0 | `BUDGET_BELOW_500_0` | 40 |
| TC-021 | 499.99 | `BUDGET_BELOW_500_0` | 40 |
| TC-022 | 500 | `BUDGET_500_1999_5` | 45 |
| TC-023 | 1999.99 | `BUDGET_500_1999_5` | 45 |
| TC-024 | 2000 | `BUDGET_2000_4999_15` | 55 |
| TC-025 | 4999.99 | `BUDGET_2000_4999_15` | 55 |
| TC-026 | 5000 | `BUDGET_5000_PLUS_25` | 65 |
| TC-027 | 1000000 | `BUDGET_5000_PLUS_25` | 65 |
| TC-028 | -0.01 | `budget_usd/NUMBER_OUT_OF_RANGE`; normalized budget null | score null; invalid |
| TC-029 | 1000000.01 | `budget_usd/NUMBER_OUT_OF_RANGE`; normalized budget null | score null; invalid |

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
| TC-040 | `"automation " + "x".repeat(29)`; exactly 40 characters | `NEED_CLEAR_20` | 40 |
| TC-041 | `"WORKFLOW " + "x".repeat(31)`; exactly 40 characters | `NEED_CLEAR_20` | 40 |
| TC-042 | `"x".repeat(40)` | `NEED_NOT_CLEAR_5` | 25 |
| TC-043 | `"Need sales workflow."`; exactly 20 characters | `NEED_NOT_CLEAR_5` | 25 |
| TC-044 | `"automated " + "x".repeat(30)`; exactly 40 characters | `NEED_NOT_CLEAR_5` because `automated` is not an approved whole word | 25 |

## Email Scoring Tests

| ID | Domain | Email reason | Exact score |
|---|---|---|---:|
| TC-050 | `alex.rivera@gmail.com` | `FREE_EMAIL_0` | 30 |
| TC-051 | `alex.rivera@yahoo.com` | `FREE_EMAIL_0` | 30 |
| TC-052 | `alex.rivera@outlook.com` | `FREE_EMAIL_0` | 30 |
| TC-053 | `alex.rivera@hotmail.com` | `FREE_EMAIL_0` | 30 |
| TC-054 | `alex.rivera@icloud.com` | `FREE_EMAIL_0` | 30 |
| TC-055 | `alex.rivera@acme.example` | `BUSINESS_EMAIL_10` | 40 |

## Email Validation Tests

| ID | Exact email fixture | Exact expected result |
|---|---|---|
| TC-056 | `not-an-email` | `email/INVALID_EMAIL_FORMAT`; normalized email null; invalid; score null |
| TC-057 | `"a".repeat(64) + "@" + "b".repeat(63) + "." + "c".repeat(63) + "." + "d".repeat(61)`; exactly 254 characters | Valid business email; `BUSINESS_EMAIL_10`; score 40 |
| TC-058 | `"a".repeat(64) + "@" + "b".repeat(63) + "." + "c".repeat(63) + "." + "d".repeat(62)`; exactly 255 characters | `email/STRING_LENGTH_OUT_OF_RANGE`; normalized email null; invalid; score null |
| TC-059 | `a..b@acme.example` | `email/INVALID_EMAIL_FORMAT`; normalized email null; invalid; score null |

## Status Boundary Tests

Every fixture is valid. Scores 69 and 39 are not attainable because all approved increments are multiples of five.

| ID | Score composition | Exact status |
|---|---|---|
| TC-060 | Base plus `role: owner`, `budget_usd: 2000`, `timeframe_days: 31`, `message: "Need sales workflow."`; score 70 | `qualified` |
| TC-061 | Base plus `role: owner`, `budget_usd: 2000`, `timeframe_days: 61`, `message: "Need sales workflow."`; score 65 | `nurture` |
| TC-062 | Unchanged base fixture; score 40 | `nurture` |
| TC-063 | Base plus `role: manager`, `message: "Need sales workflow."`; score 35 | `unqualified` |

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
| TC-086 | `submitted_at: "2026-07-23T20:00:00+08:00"` | `submitted_at/INVALID_TIMESTAMP_UTC`; normalized timestamp null; invalid; fallback identity |
| TC-087 | `submitted_at: "2026-07-23"` | `submitted_at/INVALID_TIMESTAMP_UTC`; normalized timestamp null; invalid; fallback identity |
| TC-088 | `submitted_at: "2026-02-30T12:00:00.000Z"` | `submitted_at/INVALID_TIMESTAMP_UTC`; normalized timestamp null; invalid; fallback identity |
| TC-089 | `budget_usd: "5000"` | `budget_usd/INVALID_TYPE`; normalized budget null; invalid; score null |
| TC-090 | `timeframe_days: "30"` | `timeframe_days/INVALID_TYPE`; normalized timeframe null; invalid; score null |
| TC-091 | `timeframe_days: 1.5` | `timeframe_days/INTEGER_REQUIRED`; normalized timeframe null; invalid; score null |
| TC-092 | `timeframe_days: 0` | `timeframe_days/NUMBER_OUT_OF_RANGE`; normalized timeframe null; invalid; score null |
| TC-093 | `timeframe_days: 366` | `timeframe_days/NUMBER_OUT_OF_RANGE`; normalized timeframe null; invalid; score null |
| TC-094 | `submitted_at: "not-a-timestamp"` | `submitted_at/INVALID_TIMESTAMP_UTC`; normalized timestamp null; invalid; fallback identity |

## Routing Tests

| ID | Region | Exact queue and reason | Review |
|---|---|---|---|
| TC-100 | APAC | APAC Sales Queue / `REGION_APAC` | false |
| TC-101 | North America | North America Sales Queue / `REGION_NORTH_AMERICA` | false |
| TC-102 | Europe | Europe Sales Queue / `REGION_EUROPE` | false |
| TC-103 | Other | General Sales Queue / `REGION_OTHER` | false |
| TC-104 | `region: "Africa"` | General Sales Queue / `REGION_FALLBACK_REVIEW`; `region/INVALID_ENUM`; normalized region null | true |

## String-Length, Enum, Injection, and Safety Tests

| ID | Scenario | Exact expected result |
|---|---|---|
| TC-110 | `full_name: "Al"` | Valid; normalized `Al`; score 40; nurture |
| TC-111 | `full_name: "A".repeat(100)` | Valid; normalized length 100; score 40; nurture |
| TC-112 | `full_name: "A"` | `full_name/STRING_LENGTH_OUT_OF_RANGE`; normalized full name null; invalid; score null |
| TC-113 | `full_name: "A".repeat(101)` | `full_name/STRING_LENGTH_OUT_OF_RANGE`; normalized full name null; invalid; score null |
| TC-114 | `company: "AB"` | Valid; normalized `AB`; score 40; nurture |
| TC-115 | `company: "A".repeat(120)` | Valid; normalized length 120; score 40; nurture |
| TC-116 | `company: "A"` | `company/STRING_LENGTH_OUT_OF_RANGE`; normalized company null; invalid; score null |
| TC-117 | `company: "A".repeat(121)` | `company/STRING_LENGTH_OUT_OF_RANGE`; normalized company null; invalid; score null |
| TC-118 | `message: "Need sales workflow."` | Valid length 20; `NEED_NOT_CLEAR_5`; score 25; unqualified |
| TC-119 | `message: "x".repeat(2000)` | Valid length 2000; `NEED_NOT_CLEAR_5`; score 25; unqualified |
| TC-120 | `message: "x".repeat(19)` | `message/STRING_LENGTH_OUT_OF_RANGE`; normalized message null; invalid; score null |
| TC-121 | `message: "x".repeat(2001)` | `message/STRING_LENGTH_OUT_OF_RANGE`; normalized message null; invalid; score null |
| TC-122 | `role: "intern"` | `role/INVALID_ENUM`; normalized role null; invalid; score null |
| TC-123 | `product_interest: "crm"` | `product_interest/INVALID_ENUM`; normalized product interest null; invalid; score null |
| TC-124 | `region: "Africa"` | `region/INVALID_ENUM`; normalized region null; General Sales Queue; `REGION_FALLBACK_REVIEW`; invalid; score null |
| TC-125 | `source: "phone"` | `source/INVALID_ENUM`; normalized source null; invalid; score null |
| TC-126 | `company: "=1+1 Demo Company"` | Valid; `company/POTENTIAL_SPREADSHEET_FORMULA`; storage record preserves the string as data; score 40; nurture |
| TC-127 | `message: "<script>alert(1)</script> automation workflow for sales operations"` | Valid; `message/POTENTIAL_CHANNEL_MARKUP`; score 40; nurture; notification subject/message null and raw message absent |
| TC-128 | `full_name: "Élodie 王"` | Valid; exact Unicode value preserved; score 40; nurture |

## Identity Fallback and Determinism Tests

Canonical raw-input strings use the alphabetical key order documented in [[Requirements]].

| ID | Exact fixture | Exact expected identity and normalized values |
|---|---|---|
| TC-130 | Base with `email` omitted | `email: null`; `email/REQUIRED_FIELD`; key `9ea5f0ef1911efe760e15571f7bbf4a40c2305c9c292aa01d033e415f213dc7f`; ID `invalid_lead_9ea5f0ef1911efe7` |
| TC-131 | Base with `email: "not-an-email"` | `email: null`; `email/INVALID_EMAIL_FORMAT`; key `6931fb6060986f2b4469a5132e0b7f33945515c474caa94d884522038edf2631`; ID `invalid_lead_6931fb6060986f2b` |
| TC-132 | Base with `submitted_at` omitted | `submitted_at: null`; `submitted_at/REQUIRED_FIELD`; key `c8f0b70eb49e4166904490f120722be4c9e42aa6b73d5edc9d6d8db676a4e322`; ID `invalid_lead_c8f0b70eb49e4166` |
| TC-133 | Base with `submitted_at: "2026-07-23T20:00:00+08:00"` | `submitted_at: null`; `submitted_at/INVALID_TIMESTAMP_UTC`; key `c9d4e0388a0180c08e82b2d43e69d906d7d2393a78d8c68fa942c137077412d0`; ID `invalid_lead_c9d4e0388a0180c0` |
| TC-134 | Execute the unchanged base fixture twice | Both executions return key `9d496fb34cf92660ac93d1de30328c4bef2417dc3cabc7c7ba54eddfc160956c` and ID `lead_9d496fb34cf92660`; each `processed_at` independently matches canonical UTC format |
| TC-135 | Execute the TC-130 fixture twice | Both executions return key `9ea5f0ef1911efe760e15571f7bbf4a40c2305c9c292aa01d033e415f213dc7f` and ID `invalid_lead_9ea5f0ef1911efe7`; each `processed_at` independently matches canonical UTC format |

## Output, Runtime, and Environment Tests

| ID | Exact fixture | Exact expected result |
|---|---|---|
| TC-140 | Empty object `{}` | All 12 normalized keys are null; 12 ordered `REQUIRED_FIELD` errors; key `30c57614e9166c05d9dda9b6503edbbfef1109a6dce99722c399b4dca3fbe541`; ID `invalid_lead_30c57614e9166c05`; invalid; score null; General Sales Queue; review true; invalid notification preview is non-empty/high |
| TC-141 | Object containing all 12 keys with explicit `null` | All 12 normalized keys are null; 12 ordered `INVALID_TYPE` errors except consent also uses `INVALID_TYPE`; same key and ID as TC-140; invalid; score null; General Sales Queue; review true |
| TC-142 | Unfixed runtime clock with base fixture | Top-level `processed_at` matches `YYYY-MM-DDTHH:mm:ss.sssZ`, parses as a real UTC instant, and exactly equals `storage_payload.record.processed_at` |
| TC-143 | One base-fixture manual execution | End-to-end duration is strictly less than 2.000 seconds |
| TC-144 | Workflow inspection | Workflow is inactive; Manual Trigger is the only trigger; credential count, external lookup count, write-node count, send-node count, and external API node count are all zero |

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
| DTC-010 | Controlled transformation fault injection and automated failure handling |

## Output Verification

- Exact score equals the sum represented by the five reason codes.
- Invalid input has `score: null` and cannot receive a valid-lead status.
- All 16 required top-level output keys and approved types are present.
- Storage payload uses `deferred-v0.2` and `none`; notification uses `internal-preview`.
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
