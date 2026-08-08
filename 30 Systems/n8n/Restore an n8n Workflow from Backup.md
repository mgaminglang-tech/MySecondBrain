---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Restore an n8n Workflow from Backup

## Purpose

Restore an n8n workflow from a verified backup without losing useful incident evidence or causing uncontrolled execution.

## Preconditions

- The restore objective, target environment, selected backup, expected version, operator, and reviewer are known.
- Credential and resource dependencies, rollback path, test plan, and smoke-test plan are available.
- Any production restore and later activation are explicitly approved as separate actions.

## Procedure

1. Identify the affected workflow, environment, failure state, and desired restore version.
2. Preserve the current failing state as a separate export when safe and useful for evidence.
3. Inspect the selected backup’s metadata, readability, integrity evidence, nodes, connections, and expected version under [[Backup and Recovery Standard]].
4. Never overwrite or delete the only known-good or only current recovery copy.
5. Restore into a separate inactive workflow when possible and clearly distinguish it during verification.
6. Assign only approved environment-specific credential references; never copy secret values.
7. Review triggers, URLs, schedules, time zones, data targets, error handling, resource identifiers, and workflow settings.
8. Validate node parameters, expressions, code, graph structure, connections, and credential references.
9. Run controlled DEV or isolated tests and compare results with the approved acceptance criteria.
10. For production, obtain explicit replacement and activation approval after validation.
11. Run the approved smoke test, monitor initial executions, and confirm downstream state.
12. Record the restored version, operator, approver, evidence, result, and disposition of the failing workflow.

## Verification

- The current state and only recovery copies were preserved.
- Backup identity, version, readability, and integrity were checked.
- The restored workflow remained inactive during review.
- Nodes, connections, credentials, resources, and environment mappings are correct.
- Controlled tests passed before any approved reactivation.
- Recovery result and production evidence are recorded.

## Stop / Escalate When

- Backup identity, integrity, environment mapping, or restore authority is unclear.
- Trigger conflicts or unexpected execution occur.
- The restored workflow fails validation or controlled testing.

## Related Standards

- [[Backup and Recovery Standard]]
- [[Credential and Secrets Management Standard]]
- [[30 Systems/n8n/Export and Version an n8n Workflow|Export and Version an n8n Workflow]]
- [[30 Systems/n8n/Handle a Failed Production Workflow|Handle a Failed Production Workflow]]

## Do

- Restore in a controlled inactive scope and verify before reactivation.

## Don’t

- Repeatedly activate unverified restored versions.
