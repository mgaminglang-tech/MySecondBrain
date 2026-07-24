---
type: test-results
status: active
completion: incomplete
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - testing
  - incomplete
---

# Test Results

## Current Status

The inactive DEV workflow has been created. All 25 Core Release Suite tests passed using dummy data, with 0 failed and 0 blocked. This satisfies the approved controlled-demo acceptance gate. The remaining 88 v0.1 tests form the not-run Extended Regression Suite and are required before production deployment or after a major workflow change. All ten v0.2 integration cases remain `deferred`.

## Demo Acceptance Decision

- Demo phase: complete.
- Production readiness: not approved.
- Full project closure: not applicable.
- Workflow state: inactive.
- Data: dummy only.
- Credentials, external integrations, and side effects: none.
- Complete v0.1 output contract: demonstrated.
- Known limitations and deferred work: disclosed.
- Remaining before live deployment: operational review, recovery evidence, client/owner approval, Extended Regression when required, integration testing, and production smoke testing.

## Controlled DEV Test Run

- Environment: DEV
- Workflow name: `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`
- Workflow ID: `Or7VHPFQakcY3l0Q`
- Version: `v0.1.0`
- Test ID: `TC-001`
- Result: `passed`
- Execution ID: not supplied in the documentation update request
- Evidence basis: user-confirmed controlled DEV execution
- Data classification: dummy only
- Credentials: none
- External integrations: none
- Workflow state after execution: inactive

## TC-001 Result

| Check | Expected | Actual | Result |
|---|---|---|---|
| Score | `100` | `100` | passed |
| Qualification status | `qualified` | `qualified` | passed |
| Assigned queue | `APAC Sales Queue` | `APAC Sales Queue` | passed |
| Human review | `false` | `false` | passed |
| Validation errors | none | none | passed |
| Normalization warnings | none | none | passed |
| Identity hash | `9d496fb34cf92660ac93d1de30328c4bef2417dc3cabc7c7ba54eddfc160956c` | matched | passed |
| Lead ID | `lead_9d496fb34cf92660` | matched | passed |

The test used the approved 12-field TC-001 dummy fixture. Storage and notification payloads remained inert; no credential or external integration was used.

## Controlled DEV Validation Batch

- Date: 2026-07-24
- Workflow state: inactive and unchanged before and after the batch
- Fixture isolation: temporary pin data at Set Sample Lead; no pin data was saved to the workflow
- Data classification: dummy only
- Credentials: none
- External integrations: none
- Real data: none

| Test | Execution | Expected validation errors | Actual validation errors | Expected / actual status | Expected / actual score | Expected / actual review | Queue / reason | Result |
|---|---:|---|---|---|---|---|---|---|
| TC-070 | `7026` | `[{"field":"full_name","code":"REQUIRED_FIELD","message":"full_name is required."}]` | `[{"field":"full_name","code":"REQUIRED_FIELD","message":"full_name is required."}]` | `invalid` / `invalid` | `null` / `null` | `true` / `true` | `APAC Sales Queue` / `REGION_APAC` | passed |
| TC-056 | `7027` | `[{"field":"email","code":"INVALID_EMAIL_FORMAT","message":"email format is invalid."}]` | `[{"field":"email","code":"INVALID_EMAIL_FORMAT","message":"email format is invalid."}]` | `invalid` / `invalid` | `null` / `null` | `true` / `true` | `APAC Sales Queue` / `REGION_APAC` | passed |
| TC-082 | `7028` | `[{"field":"consent","code":"CONSENT_NOT_TRUE","message":"consent must be true."}]` | `[{"field":"consent","code":"CONSENT_NOT_TRUE","message":"consent must be true."}]` | `invalid` / `invalid` | `null` / `null` | `true` / `true` | `APAC Sales Queue` / `REGION_APAC` | passed |
| TC-104 | `7029` | `[{"field":"region","code":"INVALID_ENUM","message":"region is not an approved value."}]` | `[{"field":"region","code":"INVALID_ENUM","message":"region is not an approved value."}]` | `invalid` / `invalid` | `null` / `null` | `true` / `true` | `General Sales Queue` / `REGION_FALLBACK_REVIEW` | passed |
| TC-086 | `7030` | `[{"field":"submitted_at","code":"INVALID_TIMESTAMP_UTC","message":"submitted_at must be a valid ISO-8601 UTC timestamp ending in Z."}]` | `[{"field":"submitted_at","code":"INVALID_TIMESTAMP_UTC","message":"submitted_at must be a valid ISO-8601 UTC timestamp ending in Z."}]` | `invalid` / `invalid` | `null` / `null` | `true` / `true` | `APAC Sales Queue` / `REGION_APAC` | passed |

All five executions completed successfully and reached Final Output. Expected and actual values matched exactly.

## Controlled DEV Budget-Boundary Batch

- Date: 2026-07-24
- Workflow state: inactive and unchanged before and after the batch
- Workflow changes: none
- Fixture isolation: temporary execution-scoped pin data at Set Sample Lead
- Pin-data cleanup: completed; no pin data persisted to the saved workflow
- Data classification: dummy only
- Credentials: none
- External integrations: none
- Real data: none

| Test | Execution | Expected / actual score | Expected and actual reason codes | Expected / actual status | Expected / actual queue | Assignment reason | Expected / actual review | Result |
|---|---:|---|---|---|---|---|---|---|
| TC-021 | `7031` | `40` / `40` | `ROLE_OTHER_5`, `BUDGET_BELOW_500_0`, `TIMEFRAME_91_365_5`, `NEED_CLEAR_20`, `BUSINESS_EMAIL_10` | `nurture` / `nurture` | `APAC Sales Queue` / `APAC Sales Queue` | `REGION_APAC` | `false` / `false` | passed |
| TC-022 | `7032` | `45` / `45` | `ROLE_OTHER_5`, `BUDGET_500_1999_5`, `TIMEFRAME_91_365_5`, `NEED_CLEAR_20`, `BUSINESS_EMAIL_10` | `nurture` / `nurture` | `APAC Sales Queue` / `APAC Sales Queue` | `REGION_APAC` | `false` / `false` | passed |
| TC-023 | `7033` | `45` / `45` | `ROLE_OTHER_5`, `BUDGET_500_1999_5`, `TIMEFRAME_91_365_5`, `NEED_CLEAR_20`, `BUSINESS_EMAIL_10` | `nurture` / `nurture` | `APAC Sales Queue` / `APAC Sales Queue` | `REGION_APAC` | `false` / `false` | passed |
| TC-024 | `7034` | `55` / `55` | `ROLE_OTHER_5`, `BUDGET_2000_4999_15`, `TIMEFRAME_91_365_5`, `NEED_CLEAR_20`, `BUSINESS_EMAIL_10` | `nurture` / `nurture` | `APAC Sales Queue` / `APAC Sales Queue` | `REGION_APAC` | `false` / `false` | passed |
| TC-026 | `7035` | `65` / `65` | `ROLE_OTHER_5`, `BUDGET_5000_PLUS_25`, `TIMEFRAME_91_365_5`, `NEED_CLEAR_20`, `BUSINESS_EMAIL_10` | `nurture` / `nurture` | `APAC Sales Queue` / `APAC Sales Queue` | `REGION_APAC` | `false` / `false` | passed |

All five executions completed successfully and reached Final Output. Expected and actual scores, reason-code order, statuses, queues, assignment reasons, and human-review values matched exactly.

## Core Release Suite Completion Batch

- Date: 2026-07-24
- New tests executed: 14
- Executions created: 16 because TC-134 and TC-135 each require two executions
- Result: 14 passed; 0 failed; 0 blocked
- Workflow state: inactive and unchanged before and after the batch
- Workflow changes: none
- Fixture isolation: temporary execution-scoped pin data
- Pin-data cleanup: completed; no pin data persisted
- Credentials, integrations, network requests, and real data: none

| Test | Execution evidence | Actual evidence | Result |
|---|---|---|---|
| TC-002 | `7037` | 16 exact top-level keys; exact storage and notification keys; nested record matched; runtime timestamp canonical and mirrored | passed |
| TC-006 | `7038` | Score 100; qualified; exact high-priority qualified notification preview | passed |
| TC-009 | `7039` | Invalid role; score null; review true; exact invalid notification using `not-scored`; raw lead message excluded | passed |
| TC-035 | `7040` | Score 45; `TIMEFRAME_61_90_10`; nurture | passed |
| TC-036 | `7041` | Score 40; `TIMEFRAME_91_365_5`; nurture | passed |
| TC-060 | `7042` | Score 70; qualified; exact five reason codes | passed |
| TC-063 | `7043` | Score 35; unqualified; manager role reason | passed |
| TC-101 | `7044` | North America Sales Queue / `REGION_NORTH_AMERICA`; review false | passed |
| TC-102 | `7045` | Europe Sales Queue / `REGION_EUROPE`; review false | passed |
| TC-103 | `7046` | General Sales Queue / `REGION_OTHER`; review false | passed |
| TC-134 | `7047`, `7048` | Both returned key `9d496fb34cf92660ac93d1de30328c4bef2417dc3cabc7c7ba54eddfc160956c` and ID `lead_9d496fb34cf92660` | passed |
| TC-135 | `7049`, `7050` | Both returned key `9ea5f0ef1911efe760e15571f7bbf4a40c2305c9c292aa01d033e415f213dc7f` and ID `invalid_lead_9ea5f0ef1911efe7` | passed |
| TC-141 | `7051` | Twelve ordered `INVALID_TYPE` errors; 12 null normalized fields; fallback identity, queue, and review matched | passed |
| TC-127 | `7052` | `message/POTENTIAL_CHANNEL_MARKUP`; score 40; nurture; notification omitted suspicious raw text | passed |

No expected-versus-actual differences were observed.

## Results

| Test group | Cases | Status | Evidence |
|---|---:|---|---|
| Core and schema | 9 | 4 passed; 5 not-run | TC-001, TC-002 / 7037, TC-006 / 7038, TC-009 / 7039 |
| Role scoring | 7 | not-run | None |
| Budget scoring | 10 | 5 passed; 5 not-run | TC-021 / 7031; TC-022 / 7032; TC-023 / 7033; TC-024 / 7034; TC-026 / 7035 |
| Timeframe scoring | 8 | 2 passed; 6 not-run | TC-035 / 7040; TC-036 / 7041 |
| Need clarity | 5 | not-run | None |
| Email scoring | 6 | not-run | None |
| Email validation | 4 | 1 passed; 3 not-run | TC-056 / execution 7027 |
| Status boundaries | 4 | 2 passed; 2 not-run | TC-060 / 7042; TC-063 / 7043 |
| Individual missing fields | 12 | 1 passed; 11 not-run | TC-070 / execution 7026 |
| Consent, timestamp, type, and range | 13 | 2 passed; 11 not-run | TC-082 / execution 7028; TC-086 / execution 7030 |
| Routing | 5 | 4 passed; 1 not-run | TC-101 / 7044; TC-102 / 7045; TC-103 / 7046; TC-104 / 7029 |
| String length, enum, injection, and safety | 19 | 1 passed; 18 not-run | TC-127 / 7052 |
| Identity fallback and determinism | 6 | 2 passed; 4 not-run | TC-134 / 7047, 7048; TC-135 / 7049, 7050 |
| Output, runtime, and environment | 5 | 1 passed; 4 not-run | TC-141 / 7051 |
| v0.2 integration and fault tests | 10 | deferred | Not part of v0.1 |

Executable v0.1 tests use only `passed`, `failed`, `blocked`, or `not-run`. Future v0.2 tests use `deferred`. Do not mark a test passed without execution evidence.

## Summary

- Passed: 25
- Failed: 0
- Blocked: 0
- Not run: 88
- Deferred to v0.2: 10
- Core Release Suite remaining: 0
- Extended Regression Suite remaining: 88
- Demo acceptance gate: satisfied
- Production approval: not granted

## Evidence Rules

- Record dummy inputs, expected output, observed output, execution ID, workflow version, and reviewer.
- Do not include credentials, secret values, real client data, or unnecessary personal data.
- Link any defect to [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]].
- Do not convert deferred v0.2 tests into v0.1 failures or passes.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]]
- [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]]
- [[02 - Projects/Automation/Lead Qualification Practice/Lessons Learned|Lessons Learned]]
