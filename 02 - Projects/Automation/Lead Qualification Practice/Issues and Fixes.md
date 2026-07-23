---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - issues
---

# Issues and Fixes

## Current Status

Two DEV runtime defects were identified and resolved before the user-confirmed TC-001 PASS. The workflow remained inactive, used dummy data only, and contained no credentials or external integrations.

## Issue Register

| ID | Environment | Summary | Severity | Status | Owner | Version |
|---|---|---|---|---|---|---|
| ISSUE-001 | DEV | Set Sample Lead `jsonOutput` used the wrong stored type | medium | resolved | Automation Engineer | v0.1.0 |
| ISSUE-002 | DEV | Normalize Input contained an invalid JavaScript Unicode regex escape | medium | resolved | Automation Engineer | v0.1.0 |

## Resolved Issues

### ISSUE-001 - Set Sample Lead JSON-mode type mismatch

- Environment: DEV
- Workflow: `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`
- Sanitized evidence: Edit Fields / Set v3.4 received `jsonOutput` as an object instead of the serialized JSON string required by JSON mode.
- Impact: TC-001 could not proceed beyond Set Sample Lead.
- Confirmed root cause: Incorrect stored parameter type.
- Resolution: Changed `jsonOutput` to the serialized JSON-string format required by Edit Fields / Set v3.4 while preserving the exact 12-field TC-001 dummy fixture.
- DEV verification: The saved node configuration validated, all 12 fields were preserved, and the subsequent controlled execution proceeded beyond Set Sample Lead.
- Status: resolved

### ISSUE-002 - Normalize Input invalid Unicode regex escape

- Environment: DEV
- Workflow: `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`
- Sanitized evidence: `/[<>&\`\[\]*_]/u` raised `SyntaxError: Invalid regular expression — Invalid escape`.
- Impact: TC-001 stopped at Normalize Input before validation, scoring, routing, identity generation, or final output.
- Confirmed root cause: The backtick was unnecessarily escaped in a Unicode regular-expression literal.
- Resolution: Replaced the invalid expression with the valid equivalent `/[<>&`\[\]*_]/gu`, preserving the channel-markup warning intent and all other normalization behavior.
- DEV verification: The saved Code node and complete workflow validated; the user-confirmed controlled TC-001 execution subsequently passed with the documented score, status, queue, identity values, and empty error and warning arrays.
- Status: resolved

## Issue Record Template

### ISSUE-XXX - Title

- Detected date:
- Environment:
- Workflow and version:
- Execution ID:
- Sanitized evidence:
- Business impact:
- Data impact:
- Confirmed root cause:
- Assumption requiring verification:
- Proposed fix:
- DEV verification:
- Regression cases:
- PROD approval required:
- Rollback trigger and steps:

## Rules

- Record confirmed facts separately from assumptions.
- Use sanitized evidence only.
- Verify every fix in DEV before any release proposal.
- Do not change PROD or assign PROD credentials without explicit approval.
- Update [[Known Limitations]] when a defect is accepted rather than fixed.

## Related Notes

- [[Test Results]]
- [[Known Limitations]]
- [[Backup and Restore]]
