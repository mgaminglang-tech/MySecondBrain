---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Export and Version an n8n Workflow

## Purpose

Create a traceable, readable n8n export that supports review, release, backup, and recovery without carrying secrets or sensitive test data.

## Preconditions

- The exact workflow, environment, owner, intended checkpoint, and approved storage location are known.
- Read and export access is authorized.

## Procedure

1. Confirm the workflow name or reference, environment, current state, and intended version or checkpoint.
2. Choose a meaningful version based on the approved change or release history; do not invent release approval.
3. Export through the approved read or export method without modifying or activating the workflow.
4. Store the export in the approved project or recovery location.
5. Record the version, timestamp, operator, source environment, workflow reference, and concise change summary.
6. Inspect the export for embedded secret values, sensitive payloads, prohibited client data, binaries, and unintended environment-specific content.
7. Record required credential names and restore dependencies separately without values.
8. Verify that the file opens and contains the expected nodes, connections, and settings.
9. Record a checksum or other integrity indicator when supported.
10. Link the export to the applicable backup, release, or recovery record under [[Backup and Recovery Standard]].
11. Perform Git actions only when separately approved.

## Verification

- The correct workflow and environment were exported.
- The version or checkpoint meaning and owner are recorded.
- The export is readable and structurally complete.
- Credentials remain references and no secret or prohibited data is present.
- Restore dependencies, storage location, and available integrity evidence are recorded.

## Stop / Escalate When

- The workflow identity, version, environment, or approved storage location is unclear.
- The export is incomplete, unreadable, or contains prohibited data.
- The export differs materially from the expected workflow state.

## Related Standards

- [[Backup and Recovery Standard]]
- [[Credential and Secrets Management Standard]]
- [[30 Systems/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]]

## Do

- Preserve traceability when correcting labels or metadata.

## Don’t

- Overwrite the only valid export.
- Treat exporting as permission to modify, publish, or activate a workflow.
