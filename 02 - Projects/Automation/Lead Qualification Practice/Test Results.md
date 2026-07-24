---
type: test-results
status: draft
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

The inactive DEV workflow has been created. Eleven controlled v0.1 DEV tests have passed using dummy data: TC-001, TC-021, TC-022, TC-023, TC-024, TC-026, TC-056, TC-070, TC-082, TC-086, and TC-104. No other executable v0.1 test is marked passed, and all v0.2 integration cases remain `deferred`.

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

## Results

| Test group | Cases | Status | Evidence |
|---|---:|---|---|
| Core and schema | 9 | 1 passed; 8 not-run | TC-001 user-confirmed controlled DEV result |
| Role scoring | 7 | not-run | None |
| Budget scoring | 10 | 5 passed; 5 not-run | TC-021 / 7031; TC-022 / 7032; TC-023 / 7033; TC-024 / 7034; TC-026 / 7035 |
| Timeframe scoring | 8 | not-run | None |
| Need clarity | 5 | not-run | None |
| Email scoring | 6 | not-run | None |
| Email validation | 4 | 1 passed; 3 not-run | TC-056 / execution 7027 |
| Status boundaries | 4 | not-run | None |
| Individual missing fields | 12 | 1 passed; 11 not-run | TC-070 / execution 7026 |
| Consent, timestamp, type, and range | 13 | 2 passed; 11 not-run | TC-082 / execution 7028; TC-086 / execution 7030 |
| Routing | 5 | 1 passed; 4 not-run | TC-104 / execution 7029 |
| String length, enum, injection, and safety | 19 | not-run | None |
| Identity fallback and determinism | 6 | not-run | None |
| Output, runtime, and environment | 5 | not-run | None |
| v0.2 integration and fault tests | 10 | deferred | Not part of v0.1 |

Executable v0.1 tests use only `passed`, `failed`, `blocked`, or `not-run`. Future v0.2 tests use `deferred`. Do not mark a test passed without execution evidence.

## Summary

- Passed: 11
- Failed: 0
- Blocked: 0
- Not run: 102
- Deferred to v0.2: 10
- Approval: further execution requires approval

## Evidence Rules

- Record dummy inputs, expected output, observed output, execution ID, workflow version, and reviewer.
- Do not include credentials, secret values, real client data, or unnecessary personal data.
- Link any defect to [[Issues and Fixes]].
- Do not convert deferred v0.2 tests into v0.1 failures or passes.

## Related Notes

- [[Test Plan]]
- [[Issues and Fixes]]
- [[Deployment Checklist]]
- [[Lessons Learned]]
