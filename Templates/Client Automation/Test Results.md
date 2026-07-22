---
type: test-results
status: testing
client: CLIENT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - testing
---

# Test Results

## Test Run

- Environment:
- Workflow name:
- Workflow ID:
- Version:
- Tester:
- Date:
- Test data classification: Dummy or sanitized

## Results

| Test ID | Execution ID | Expected | Observed | Status | Evidence reference |
|---|---|---|---|---|---|
| TC-001 |  |  |  | not-run |  |

Use `passed`, `failed`, `blocked`, or `not-run`. Do not mark a test passed without execution evidence.

## Output Evidence

```json
{
  "example_field": "TEST_VALUE"
}
```

Do not paste secrets or unredacted client data.

## Failure-Path Results

- Invalid input:
- Empty data:
- Duplicate input:
- Retry exhaustion:
- Dependency outage:
- Alert delivery:
- Manual recovery:

## Issues Found

| Issue | Severity | Owner | Fix version | Retest status |
|---|---|---|---|---|
|  |  |  |  |  |

## Summary

- Passed:
- Failed:
- Blocked:
- Not run:
- Remaining limitations:

## Approval

- Tester:
- Reviewer:
- Project owner decision:
- Date:

## Related Notes

- [[Templates/Client Automation/Test Plan|Test Plan]]
- [[Templates/Client Automation/Issues and Fixes|Issues and Fixes]]
- [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
