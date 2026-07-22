---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - recovery
---

# Restore an n8n Workflow from Backup

## Purpose

Restore an n8n workflow from a verified backup without losing the current state or causing uncontrolled production execution.

## When to Use

Use after a failed release, accidental configuration change, corruption, or approved recovery test.

## Requirements

- Verified backup and version metadata
- Current-state export before restoration
- Restore target and environment
- Credential-name and resource dependency map
- Rollback and smoke-test plan
- Explicit approval for any PROD restore

## Safety Considerations

- Keep restored workflows inactive during inspection.
- Do not overwrite or delete the only current or known-good copy.
- Never embed secrets in the import package.
- Confirm trigger URLs, schedules, credentials, and resource IDs before activation.
- Codex and MCP must not restore or activate PROD without explicit approval.

## Ownership and Approval Gates

- Incident or project owner authorizes the recovery objective.
- Operator performs the restore.
- Reviewer verifies the backup, graph, settings, and environment mappings.
- PROD approver authorizes replacement and activation.

## Procedure

1. Identify the affected workflow, environment, and desired restore version.
2. Export the current state, even when it is faulty, if safe and possible.
3. Verify the selected backup metadata, integrity, nodes, connections, and expected version.
4. Import or restore as a separate inactive workflow when possible.
5. Name the restored draft clearly until verification is complete.
6. Assign approved environment-specific credentials by name; never copy secret values into notes.
7. Review triggers, URLs, schedules, time zones, data targets, error handling, and workflow settings.
8. Validate the graph and run controlled tests in DEV or isolated conditions.
9. Compare results with the documented acceptance criteria.
10. For PROD, obtain explicit approval to replace or reactivate.
11. Run the approved smoke test and monitor initial executions.
12. Record the restored version, operator, approver, evidence, and disposition of the faulty workflow.

## Verification

- [ ] Current state preserved before restoration.
- [ ] Backup version and integrity verified.
- [ ] Restored workflow remained inactive during review.
- [ ] Nodes and connections match the intended version.
- [ ] Credentials and resource identifiers target the correct environment.
- [ ] Controlled tests passed.
- [ ] PROD activation approval is recorded when applicable.
- [ ] Smoke test and monitoring completed.

## Failure Handling

If restoration fails validation, keep the restored workflow inactive, preserve error evidence, and select another verified backup or rebuild in DEV. Do not repeatedly activate unverified versions.

## Rollback

Revert to the pre-restore export or the last approved workflow version. Reconfirm environment mappings and obtain approval before activation.

## Troubleshooting

- **Missing credential:** Ask the credential owner to provide access through the approved store.
- **Trigger conflicts:** Keep the restored workflow inactive until duplicate triggers are resolved.
- **Version mismatch:** Stop and compare backup metadata with the approved release record.
- **Unexpected execution:** Deactivate or contain according to the incident plan and preserve evidence.

## Related Notes

- [[03 - Areas/Automation Operations/Backup Policy|Backup Policy]]
- [[06 - SOPs/n8n/Export and Version an n8n Workflow|Export and Version an n8n Workflow]]
- [[06 - SOPs/n8n/Handle a Failed Production Workflow|Handle a Failed Production Workflow]]
- [[Templates/Client Automation/Backup and Restore|Backup and Restore]]
