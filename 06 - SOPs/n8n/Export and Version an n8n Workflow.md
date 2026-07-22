---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - versioning
  - backup
---

# Export and Version an n8n Workflow

## Purpose

Create a traceable workflow export that supports review, backup, deployment, and restoration without storing secrets.

## When to Use

Use before PROD changes, after approved releases, before handover, and at meaningful DEV milestones.

## Requirements

- Workflow name, ID, environment, and intended version
- Approved backup location
- Change summary and owner
- Permission to read and export the workflow

## Safety Considerations

- Confirm the export does not contain secret values or prohibited client data.
- Do not publish exports to public or unapproved locations.
- Exporting does not authorize modifying or activating the workflow.
- Back up PROD before changing it; Codex and MCP require explicit approval for any PROD modification.

## Versioning Standard

- `v0.1.0` — initial development version
- `v0.2.0` — development feature update
- `v0.2.1` — development bug fix
- `v1.0.0` — first approved production release

Recommended record label: `ENVIRONMENT - CLIENT_NAME - WORKFLOW_NAME - VERSION`.

## Ownership and Approval Gates

- Developer proposes the version and change summary.
- Reviewer verifies the export and version meaning.
- Project owner approves the storage location.
- PROD approver confirms a PROD export is the intended release or rollback baseline.

## Procedure

1. Confirm the exact workflow name, ID, and environment.
2. Review the change type and assign the next version.
3. Export the workflow using an approved read/export method.
4. Save it in the approved client project location.
5. Record version, timestamp, operator, workflow ID, source environment, and change summary.
6. Inspect the export for unexpected credentials, secrets, personal data, binary data, or environment-specific values.
7. Record required credential names separately without values.
8. Verify the file opens and contains the expected nodes, connections, and settings.
9. Record a checksum or integrity indicator when the storage process supports one.
10. Link the export record from [[Templates/Client Automation/Backup and Restore|Backup and Restore]].

## Verification

- [ ] Correct workflow and environment exported.
- [ ] Version follows the standard.
- [ ] Change summary and owner recorded.
- [ ] Export is readable and structurally complete.
- [ ] No secrets or prohibited client data found.
- [ ] Required credential names and restore dependencies documented.
- [ ] Storage location and integrity evidence recorded.

## Failure Handling

If the export is incomplete, unreadable, or contains prohibited data, do not use it as a backup. Restrict access, create a clean export, and notify the project owner if exposure may have occurred.

## Rollback

This procedure is read-only. If a record was labeled incorrectly, preserve traceability, correct the label or metadata with approval, and do not overwrite the only valid export.

## Troubleshooting

- **Version unclear:** Compare the approved release history and ask the project owner.
- **Credential values appear:** Restrict the file and follow the secrets incident process.
- **Export differs from the canvas:** Repeat the export and confirm the correct workflow ID.

## Related Notes

- [[03 - Areas/Automation Operations/Backup Policy|Backup Policy]]
- [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]]
- [[06 - SOPs/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]]
- [[Templates/Client Automation/Backup and Restore|Backup and Restore]]
