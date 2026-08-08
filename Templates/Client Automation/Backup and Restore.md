---
type: project-note
status: draft
client: CLIENT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - backup
  - recovery
---

# Backup and Restore

## Recovery Objective

- Workflows covered:
- Environment:
- Recovery owner:
- Acceptable data loss:
- Acceptable recovery time:
- Client retention requirement:

## Backup Inventory

| Workflow | ID | Environment | Version | Export date | Operator | Storage reference | Integrity evidence |
|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |

## Version Standard

- `v0.1.0` — initial development version
- `v0.2.0` — development feature update
- `v0.2.1` — development bug fix
- `v1.0.0` — first approved production release

## Backup Contents

- [ ] Workflow export without secrets
- [ ] Node and connection inventory
- [ ] Credential names and owners without values
- [ ] Environment-specific dependency references
- [ ] Deployment and rollback notes
- [ ] Test evidence and known limitations

## Restore Prerequisites

- [ ] Backup integrity verified.
- [ ] Current state exported before restore.
- [ ] Restore target and version approved.
- [ ] Credentials and resource IDs mapped.
- [ ] Restored workflow will remain inactive during review.
- [ ] Smoke test and rollback plan are ready.
- [ ] Explicit PROD approval exists when applicable.

## Restore Procedure

1. Preserve the current workflow state.
2. Verify the intended backup and version.
3. Restore as a separate inactive draft when possible.
4. Reassign approved credential references by name.
5. Review triggers, schedules, settings, nodes, and connections.
6. Validate with dummy or sanitized data.
7. Obtain approval before PROD activation.
8. Run the approved smoke test and monitor.

## Restore Test Record

- Date:
- Environment:
- Backup version:
- Operator:
- Result: not-tested
- Evidence:
- Issues:

Do not change `Result` to passed without evidence.

## Failure and Rollback

- Restore failure threshold:
- Pre-restore export reference:
- Rollback steps:
- Rollback owner:
- Approval required:

## Related Notes

- [[Backup and Recovery Standard]]
- [[30 Systems/n8n/Export and Version an n8n Workflow|Export and Version an n8n Workflow]]
- [[30 Systems/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]]
