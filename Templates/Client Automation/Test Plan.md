---
type: project-note
status: draft
client: CLIENT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - testing
---

# Test Plan

## Objective

Define repeatable tests and acceptance criteria before execution.

## Test Environment

- Environment: DEV
- Workflow name: `DEV - Client or Project - Workflow Name`
- Workflow version:
- Credentials: Test credentials only
- Data: Dummy or sanitized
- Optional STAGING use:

## Test Data

| Fixture | Purpose | Sanitization confirmed | Owner |
|---|---|---|---|
| TEST_RECORD_001 | Happy path | Yes |  |

## Test Cases

| ID | Scenario | Input | Expected result | Side effect | Priority |
|---|---|---|---|---|---|
| TC-001 | Happy path | TEST_INPUT |  | Test destination only | High |
| TC-002 | Missing required field | TEST_INPUT | Validation failure | None | High |
| TC-003 | Empty result | TEST_INPUT | Controlled empty output | None | Medium |
| TC-004 | Duplicate input | TEST_INPUT | No duplicate side effect | None | High |
| TC-005 | Dependency failure | TEST_INPUT | Retry or alert | None or controlled | High |

## Error and Recovery Tests

- [ ] Invalid input is contained.
- [ ] Retry limits prevent loops.
- [ ] Error alerts reach the test destination.
- [ ] Partial failures preserve recoverable context safely.
- [ ] Manual recovery steps are clear.
- [ ] Rollback restores the last validated DEV version.

## Output Verification

- Required fields:
- Data types:
- Expected ordering:
- Expected downstream records:
- Prohibited fields:

## Entry Criteria

- [ ] Requirements approved.
- [ ] DEV build ready.
- [ ] Fixtures are dummy or sanitized.
- [ ] Test credentials and destinations confirmed.
- [ ] Side effects are controlled.

## Exit Criteria

- [ ] Critical test cases passed.
- [ ] Failures are fixed or accepted explicitly.
- [ ] Evidence is recorded in [[Templates/Client Automation/Test Results|Test Results]].
- [ ] Known limitations are updated.
- [ ] Reviewer decision is recorded.

## Approval

- Test owner:
- Reviewer:
- Approved date:

## Related Notes

- [[Templates/Client Automation/Requirements|Requirements]]
- [[Templates/Client Automation/Issues and Fixes|Issues and Fixes]]
- [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
