---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - incident-response
---

# Handle a Failed Production Workflow

## Purpose

Contain, diagnose, recover, and document a failed production automation with minimal additional impact.

## When to Use

Use for repeated errors, missed processing, incorrect side effects, data exposure, performance degradation, or unavailable dependencies in PROD.

## Requirements

- Incident owner and communication channel
- Workflow name, ID, owner, and current version
- Approved access to execution metadata and logs
- Current backup and rollback instructions
- Client escalation and severity criteria

## Safety Considerations

- Protect client data while collecting evidence.
- Do not paste production payloads, secrets, or credentials into notes or assistant prompts.
- Stop continued harmful processing according to the approved incident authority.
- Diagnose and fix in DEV whenever possible.
- Codex and MCP must not modify, execute, deactivate, restore, or reactivate PROD without explicit approval unless an approved incident plan grants that exact authority.

## Ownership and Approval Gates

| Role | Responsibility |
|---|---|
| Incident owner | Coordinates severity, decisions, communication, and closure. |
| Operator | Contains the workflow and gathers approved evidence. |
| Developer | Reproduces and fixes the issue in DEV. |
| Reviewer | Validates the fix, tests, and rollback readiness. |
| PROD approver | Approves production change and reactivation. |

## Procedure

1. Record detection time, affected workflow, symptoms, and known impact.
2. Assign severity using the client-approved criteria.
3. Contain the issue: pause inputs, deactivate the workflow, or disable the harmful path as authorized.
4. Preserve execution IDs, error messages, timestamps, and affected record references without copying sensitive payloads.
5. Determine whether retries could duplicate or worsen side effects before retrying.
6. Notify required stakeholders according to severity.
7. Reproduce the failure in DEV with dummy or sanitized data.
8. Identify the root cause, affected scope, and recovery needs.
9. Implement and test the fix in DEV, including regression and failure paths.
10. Decide whether to restore a backup, deploy a fix, replay records, or perform manual recovery.
11. Prepare backup, rollback, smoke test, and explicit PROD approval.
12. Apply the approved recovery action.
13. Verify downstream state and reconcile missed or duplicate records.
14. Monitor the recovery window and communicate status.
15. Record root cause, timeline, resolution, prevention actions, and owner.

## Verification

- [ ] Harmful processing is contained.
- [ ] Impact and affected records are understood.
- [ ] Evidence is preserved without exposing sensitive data.
- [ ] Fix or restore path passed DEV verification.
- [ ] Backup and rollback are ready.
- [ ] PROD approval is recorded.
- [ ] Smoke test and reconciliation passed.
- [ ] Monitoring and client communication are complete.

## Failure Handling

If the first recovery attempt fails, return to containment, stop repeated retries, and reassess the root cause. Escalate when impact exceeds documented authority or recovery targets.

## Rollback

Deactivate the failed release as authorized and restore the last approved version using [[06 - SOPs/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]]. Obtain approval before reactivation and reconcile records affected during the incident.

## Troubleshooting

- **Retries create duplicates:** Stop retries and add idempotency or reconciliation controls in DEV.
- **Dependency is unavailable:** Contain processing, preserve inputs safely, and follow the client continuity plan.
- **Cause cannot be reproduced:** Increase safe logging in DEV and compare environment configuration without exposing secrets.
- **Client data may be exposed:** Follow [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]] immediately.

## Related Notes

- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[03 - Areas/Automation Operations/Backup Policy|Backup Policy]]
- [[Templates/Client Automation/Issues and Fixes|Issues and Fixes]]
- [[Templates/Client Automation/Maintenance Guide|Maintenance Guide]]
