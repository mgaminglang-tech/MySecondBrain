---
type: project-note
status: active
client: CLIENT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - issues
---

# Issues and Fixes

## Issue Register

| ID | Environment | Summary | Severity | Status | Owner | Version |
|---|---|---|---|---|---|---|
| ISSUE-001 | DEV |  |  | open |  |  |

## Issue Detail

### ISSUE-001 - ISSUE_TITLE

- Detected date:
- Detected by:
- Workflow and version:
- Environment:
- Execution ID:
- Client impact:
- Data impact:

#### Evidence

Record sanitized evidence only. Never include secrets or unredacted client payloads.

#### Root Cause

- Confirmed fact:
- Assumption requiring verification:

#### Fix

- Proposed change:
- DEV implementation version:
- Owner:

#### Verification

- [ ] Fix tested in DEV.
- [ ] Regression tests passed.
- [ ] Failure path retested.
- [ ] No PROD data or credentials used in DEV.
- [ ] Reviewer approved the result.

#### PROD Gate

- [ ] Current PROD backup exists.
- [ ] Rollback plan is ready.
- [ ] Explicit PROD approval is recorded.
- [ ] Smoke test is defined.

#### Rollback

- Trigger:
- Steps:
- Owner:

## Related Notes

- [[Templates/Client Automation/Test Results|Test Results]]
- [[Templates/Client Automation/Known Limitations|Known Limitations]]
- [[30 Systems/n8n/Handle a Failed Production Workflow|Handle a Failed Production Workflow]]
