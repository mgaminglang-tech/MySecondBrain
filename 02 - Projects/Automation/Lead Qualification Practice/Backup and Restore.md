---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - backup
  - recovery
---

# Backup and Restore

## Current Status

No workflow exists to back up or restore. This is a proposed procedure.

## Recovery Objectives

- DEV: Preserve known-good development versions; targets to be defined.
- STAGING: Optional and only if the environment is adopted.
- PROD: Acceptable data loss and recovery time must be approved before deployment.
- Recovery owner and backup storage location: To be assigned.

## Version Standard

- `v0.1.0` — initial DEV version.
- `v0.2.0` — DEV feature update.
- `v0.2.1` — DEV bug fix.
- `v1.0.0` — first approved production release.

## Backup Contents

- [ ] Secret-free n8n workflow export.
- [ ] Node and connection inventory.
- [ ] Credential names and owners without values.
- [ ] Environment-specific resource references.
- [ ] Approved requirements, scoring rule version, and routing version.
- [ ] Test evidence, issues, limitations, deployment, and rollback notes.

## DEV Backup Procedure

1. Keep the workflow inactive when making risky structural changes.
2. Export the current known-good DEV workflow without credentials or secrets.
3. Record version, export date, operator, and integrity check.
4. Store it in the approved backup location.
5. Validate restore into a separate inactive DEV draft with dummy data.

## Optional STAGING Backup Procedure

Follow the DEV procedure using separate STAGING references. Do not restore STAGING credentials from DEV exports.

## PROD Backup and Restore Procedure

1. Obtain explicit authorization.
2. Export and verify the current PROD version before change.
3. Preserve current scoring/routing configurations and resource mappings.
4. Restore the selected backup as a separate inactive draft when possible.
5. Reassign approved PROD credentials by name; never copy secret values into documentation.
6. Review triggers, settings, retention, nodes, connections, resource IDs, and recipients.
7. Validate with the approved sanitized smoke-test record.
8. Activate only after explicit approval and monitor.

## Data Reconciliation

Workflow restoration does not automatically repair Airtable/Sheets records or resend notifications. A separate approved reconciliation must identify:

- Leads accepted during the incident window.
- Storage records created or missing.
- Notifications sent, missing, or duplicated.
- Safe replay candidates using the approved idempotency key.

## Restore Test Record

- Result: not-tested
- Evidence: none
- Environment: not-applicable

Do not change the result without execution evidence.

## Related Notes

- [[Deployment Checklist]]
- [[Maintenance Guide]]
- [[Issues and Fixes]]

