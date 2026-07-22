---
type: policy
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - n8n
  - environments
---

# Development and Production Policy

## Purpose

Define the controls that separate automation development from live client operations.

## Environment Model

| Environment | Purpose | Data | Credentials | Activation |
|---|---|---|---|---|
| DEV | Build, debug, and verify changes | Dummy or sanitized | Test credentials | Manual or isolated test execution only |
| STAGING | Optional production-like validation | Sanitized or specifically approved | Separate non-production credentials | Controlled and project-specific |
| PROD | Live client operations | Minimum approved production data | Production credentials | Controlled activation after approval |

STAGING is optional. Its use, ownership, data rules, and acceptance criteria must be documented in the project.

## Naming Standards

- DEV workflow: `DEV - Client or Project - Workflow Name`
- PROD workflow: `PROD - Client or Project - Workflow Name`
- DEV credential: `DEV - Service - Purpose`
- PROD credential: `PROD - Service - Purpose`

## Versioning Standard

| Version | Meaning |
|---|---|
| `v0.1.0` | Initial development version |
| `v0.2.0` | Development feature update |
| `v0.2.1` | Development bug fix |
| `v1.0.0` | First approved production release |

Later versions should follow semantic versioning: major for breaking changes, minor for backward-compatible features, and patch for backward-compatible fixes.

## Responsibilities

| Role | Responsibility |
|---|---|
| Project owner | Own scope, risk, client communication, and final acceptance. |
| Developer | Build in DEV, document changes, and collect test evidence. |
| Reviewer | Review architecture, tests, security, failure handling, and rollback readiness. |
| PROD approver | Explicitly authorize the named release and activation window. |
| Operator | Perform the approved deployment, smoke test, and monitoring. |
| Codex or MCP | Assist within the approved environment and scope; never modify PROD without explicit approval. |

One person may hold multiple roles, but the approval decision must still be recorded.

## DEV Requirements

- Use dummy or sanitized client data.
- Use test credentials separated from PROD credentials.
- Keep workflows inactive unless an isolated test requires a temporary trigger.
- Test expected, empty, duplicate, invalid, retry, and failure paths where applicable.
- Document assumptions, limitations, node ownership, and expected outputs.
- Do not represent DEV results as production verification.

## PROD Approval Gate

Before any PROD modification or activation, confirm:

- [ ] Scope and release version are approved.
- [ ] DEV tests passed with recorded evidence.
- [ ] Security and client-data handling were reviewed.
- [ ] A current export or backup exists and is restorable.
- [ ] Rollback steps, owner, and decision threshold are documented.
- [ ] Credentials and environment-specific identifiers were reviewed without copying secrets into documentation.
- [ ] A deployment window and monitoring owner are assigned.
- [ ] Smoke-test steps and success criteria are defined.
- [ ] Explicit PROD approval is recorded.

## Controlled Activation

1. Confirm the approved version and backup.
2. Apply only the approved change.
3. Verify node configuration and connections before activation.
4. Activate during the approved window.
5. Run the minimum safe smoke test.
6. Monitor initial executions and error alerts.
7. Roll back if a documented threshold is reached.
8. Record the result, approver, operator, timestamps, and remaining risks.

## Failure and Rollback

- Stop or deactivate the affected PROD workflow when continued execution could cause harm.
- Preserve execution evidence before changing configuration when safe.
- Restore the last approved version according to [[06 - SOPs/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]].
- Revalidate credentials, triggers, connections, and downstream side effects.
- Obtain approval before reactivation unless an approved incident plan explicitly delegates that authority.

## Related Notes

- [[03 - Areas/Automation Operations/Automation Operations|Automation Operations]]
- [[03 - Areas/Automation Operations/Backup Policy|Backup Policy]]
- [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]]
- [[06 - SOPs/n8n/Promote DEV Workflow to PROD|Promote DEV Workflow to PROD]]
- [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
