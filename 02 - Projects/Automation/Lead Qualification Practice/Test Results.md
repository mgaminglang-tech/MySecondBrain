---
type: test-results
status: draft
completion: incomplete
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - testing
  - incomplete
---

# Test Results

## Current Status

The inactive DEV workflow has been created. TC-001 has one user-confirmed controlled DEV PASS using dummy data. No other executable v0.1 test is marked passed, and all v0.2 integration cases remain `deferred`.

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

## Results

| Test group | Cases | Status | Evidence |
|---|---:|---|---|
| Core and schema | 9 | 1 passed; 8 not-run | TC-001 user-confirmed controlled DEV result |
| Role scoring | 7 | not-run | None |
| Budget scoring | 10 | not-run | None |
| Timeframe scoring | 8 | not-run | None |
| Need clarity | 5 | not-run | None |
| Email scoring | 6 | not-run | None |
| Email validation | 4 | not-run | None |
| Status boundaries | 4 | not-run | None |
| Individual missing fields | 12 | not-run | None |
| Consent, timestamp, type, and range | 13 | not-run | None |
| Routing | 5 | not-run | None |
| String length, enum, injection, and safety | 19 | not-run | None |
| Identity fallback and determinism | 6 | not-run | None |
| Output, runtime, and environment | 5 | not-run | None |
| v0.2 integration and fault tests | 10 | deferred | Not part of v0.1 |

Executable v0.1 tests use only `passed`, `failed`, `blocked`, or `not-run`. Future v0.2 tests use `deferred`. Do not mark a test passed without execution evidence.

## Summary

- Passed: 1
- Failed: 0
- Blocked: 0
- Not run: 112
- Deferred to v0.2: 10
- Approval: TC-001 result supplied for documentation; further execution requires approval

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
