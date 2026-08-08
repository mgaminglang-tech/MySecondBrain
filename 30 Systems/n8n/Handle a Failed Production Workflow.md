---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Handle a Failed Production Workflow

## Purpose

Contain, diagnose, recover, and document a failed production n8n workflow without increasing impact or treating findings as repair authority.

## Preconditions

- The incident owner, workflow and release identity, approved evidence access, severity criteria, backup, and rollback instructions are known.
- Containment and production-change authority are explicit.

## Procedure

1. Record detection time, symptoms, affected workflow and version, known impact, and incident owner.
2. Contain continued harm using only the authorized action: pause inputs, disable the harmful path, or deactivate the workflow.
3. Preserve approved execution references, errors, timestamps, configuration state, and affected-record references without copying sensitive payloads.
4. Determine the blast radius across inputs, executions, records, recipients, external writes, and downstream systems.
5. Distinguish a confirmed read failure from an ambiguous or partial write before retrying.
6. Stop blind retries when duplicate writes or further side effects are possible.
7. Inspect execution evidence, workflow configuration, dependency state, recent changes, and environment differences.
8. Reproduce and correct the failure in DEV with dummy or sanitized data when possible.
9. Choose an approved recovery path: restore, deploy a verified fix, replay selected records, reconcile manually, or wait for a dependency.
10. Prepare the backup, rollback, smoke test, monitoring plan, and required production approval.
11. Apply only the approved recovery action and validate configuration before reactivation.
12. Reconcile missed, partial, or duplicate records and verify downstream state.
13. Monitor the recovery window and record the verified outcome, remaining impact, prevention action, and owner.
14. Preserve a reusable lesson only when it generalizes beyond this incident.

## Verification

- Harmful processing and duplicate-write risk are contained.
- Evidence is sufficient and does not expose sensitive data.
- Blast radius and write ambiguity are understood or explicitly unresolved.
- The fix or restore path passed the applicable controlled validation.
- Reactivation or destructive repair approval is recorded when required.
- Smoke testing, reconciliation, monitoring, and incident outcome are documented.

## Stop / Escalate When

- Impact exceeds documented authority or may involve sensitive-data exposure.
- Write state is ambiguous and retry could duplicate effects.
- Recovery validation fails or the cause cannot be reproduced safely.
- A finding would require unapproved remediation, activation, or destructive repair.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Backup and Recovery Standard]]
- [[Client Data Handling Standard]]
- [[Agent Operating Standard]]
- [[30 Systems/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]]

## Do

- Contain first and preserve evidence before changing configuration when safe.

## Don’t

- Convert audit findings or diagnostic access into automatic remediation authority.
- Retry blindly when external write state is uncertain.
