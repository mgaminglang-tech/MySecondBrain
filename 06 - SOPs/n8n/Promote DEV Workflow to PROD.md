---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - deployment
---

# Promote DEV Workflow to PROD

## Purpose

Promote an approved DEV workflow into PROD through a controlled, reversible release.

## When to Use

Use for the first production release and every subsequent production change.

## Requirements

- Approved DEV test results
- Reviewed architecture, error handling, security, and limitations
- Release version and change summary
- Current PROD backup or confirmed first-release baseline
- Rollback plan and owner
- Smoke-test plan and monitoring owner
- Explicit approval for the specific PROD change and activation window

## Safety Considerations

- Never convert or rename the only DEV workflow into PROD.
- Use a separate workflow named `PROD - Client or Project - Workflow Name`.
- Never copy DEV credentials into PROD; reference approved credentials named `PROD - Service - Purpose`.
- Codex and MCP must not create, update, publish, unpublish, execute, or restore PROD without explicit approval.
- Keep the PROD workflow inactive until configuration review is complete.

## Ownership and Approval Gates

| Gate | Required owner |
|---|---|
| Release readiness | Developer and reviewer |
| Data and credential approval | Client data owner and credential owner |
| Backup and rollback readiness | Operator and reviewer |
| PROD modification | PROD approver |
| Activation | PROD approver and operator |
| Release acceptance | Project owner or client approver |

## Procedure

1. Freeze the approved DEV version and label the first production release `v1.0.0`.
2. Complete [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]].
3. Export the approved DEV workflow and verify the file.
4. Back up the current PROD workflow before any change.
5. Create or update the separate PROD workflow while it remains inactive.
6. Replace DEV credential references and resource identifiers with approved PROD references without exposing values.
7. Review triggers, recipients, database targets, URLs, schedules, time zones, retries, timeouts, and error workflow settings.
8. Confirm rollback steps and the condition that triggers rollback.
9. Obtain explicit activation approval.
10. Activate during the approved window.
11. Run the smallest safe smoke test using an approved test record.
12. Verify execution status, expected side effects, logs, alerts, and downstream records.
13. Monitor the initial production period defined by the project.
14. Record release version, approver, operator, timestamps, smoke-test result, and remaining risks.

## Verification

- [ ] PROD workflow name follows the standard.
- [ ] Release version is approved.
- [ ] Backup is current and recovery-ready.
- [ ] PROD credentials and identifiers are correct.
- [ ] Workflow was inactive during configuration review.
- [ ] Explicit activation approval is recorded.
- [ ] Smoke test passed with expected side effects only.
- [ ] Monitoring and failure alerts are working.
- [ ] Handover or maintenance records were updated.

## Failure Handling

If activation or smoke testing fails, stop further tests, contain side effects, preserve execution evidence, notify the owner, and apply the approved rollback threshold. Do not troubleshoot directly in PROD beyond the explicitly approved incident scope.

## Rollback

1. Deactivate the affected PROD workflow when authorized or required by the incident plan.
2. Restore the last approved backup using [[06 - SOPs/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]].
3. Verify credentials, triggers, and connections.
4. Obtain approval before reactivation.
5. Run the approved smoke test and record the result.

## Troubleshooting

- **Wrong environment reference:** Keep PROD inactive, correct the reference, and repeat review.
- **Smoke test creates unexpected side effects:** Contain the side effect and roll back.
- **Backup cannot be verified:** Stop deployment until a recovery-ready backup exists.
- **Approval is ambiguous:** Treat approval as absent.

## Related Notes

- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[03 - Areas/Automation Operations/Backup Policy|Backup Policy]]
- [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
- [[Templates/Client Automation/Backup and Restore|Backup and Restore]]
