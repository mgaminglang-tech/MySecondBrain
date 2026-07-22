---
type: policy
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - backup
  - recovery
---

# Backup Policy

## Purpose

Ensure approved workflow versions and recovery information are available before risky changes and during incidents.

## Backup Scope

A client automation backup should include, where applicable:

- Exported workflow definition without embedded secrets
- Workflow name, ID, environment, and version
- Export timestamp and operator
- Node and connection inventory
- Required credential names, not credential values
- Environment-specific IDs recorded as non-secret references
- Deployment notes, dependencies, and rollback steps
- Related test evidence and known limitations

## Required Backup Events

Create or verify a backup:

- Before the first PROD activation
- Before every PROD change
- Before credential rotation affecting a workflow
- Before restoring or replacing workflow configuration
- After an approved production release
- Before client handover

## Storage and Access

- Store backups only in the approved project location.
- Restrict access according to client and environment requirements.
- Never store secrets or unredacted sensitive client data in an export package.
- Record the storage location as a reference, not as a public link when access is restricted.
- Define retention and deletion periods per client agreement; no universal retention period is assumed.

## Version Labels

- `v0.1.0` — initial development version
- `v0.2.0` — development feature update
- `v0.2.1` — development bug fix
- `v1.0.0` — first approved production release

Use the environment and version in the backup record, for example: `PROD - CLIENT_NAME - WORKFLOW_NAME - v1.0.0`.

## Ownership and Approval

- The project owner defines the approved storage location and retention requirement.
- The operator creates the export and records its checksum or other integrity evidence when available.
- A reviewer confirms the backup opens, contains the expected workflow, and excludes secrets.
- The PROD approver confirms rollback readiness before deployment.

## Verification

- [ ] Correct workflow and environment identified.
- [ ] Export completed before the change.
- [ ] Version and timestamp recorded.
- [ ] No secrets or prohibited client data included.
- [ ] File is readable and structurally complete.
- [ ] Restore steps and required credential names documented.
- [ ] Approved storage location recorded.

## Restore and Rollback

A backup is not considered recovery-ready until restore requirements are documented. Use [[06 - SOPs/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]] for controlled restoration. Restoring to PROD requires explicit approval and must not overwrite the only recoverable copy.

## Related Notes

- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[06 - SOPs/n8n/Export and Version an n8n Workflow|Export and Version an n8n Workflow]]
- [[Templates/Client Automation/Backup and Restore|Backup and Restore]]
- [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
