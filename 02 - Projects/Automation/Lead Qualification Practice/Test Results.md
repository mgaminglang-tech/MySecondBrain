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

No workflow has been created and no tests have been executed. All executable v0.1 cases are `not-run`; all v0.2 integration cases are `deferred`.

## Planned Test Run

- Environment: DEV
- Workflow name: `DEV - Demo Sales Company - Lead Qualification Practice`
- Workflow ID: not-created
- Version: `v0.1.0` planned
- Tester: to be assigned
- Date: not-run
- Data classification: dummy only
- Credentials: none
- External integrations: none

## Results

| Test group | Cases | Status | Evidence |
|---|---:|---|---|
| Core and schema | 6 | not-run | None |
| Role scoring | 7 | not-run | None |
| Budget scoring | 7 | not-run | None |
| Timeframe scoring | 8 | not-run | None |
| Need clarity | 5 | not-run | None |
| Email scoring | 6 | not-run | None |
| Status boundaries | 4 | not-run | None |
| Individual missing fields | 12 | not-run | None |
| Consent, timestamp, type, and range | 11 | not-run | None |
| Routing | 5 | not-run | None |
| Length, injection, and safety | 7 | not-run | None |
| Output, determinism, and failure | 6 | not-run | None |
| v0.2 integration tests | 9 | deferred | Not part of v0.1 |

Use only `passed`, `failed`, `blocked`, or `not-run`. Do not mark a test passed without execution evidence.

## Summary

- Passed: 0
- Failed: 0
- Blocked: 0
- Not run: 84
- Deferred to v0.2: 9
- Approval: not requested

## Evidence Rules

- Record sanitized inputs, expected output, observed output, execution ID, workflow version, and reviewer.
- Do not include credentials, secret values, real client data, or unnecessary personal data.
- Link any defect to [[Issues and Fixes]].
- Do not convert deferred v0.2 tests into v0.1 failures or passes.

## Related Notes

- [[Test Plan]]
- [[Issues and Fixes]]
- [[Deployment Checklist]]
- [[Lessons Learned]]
