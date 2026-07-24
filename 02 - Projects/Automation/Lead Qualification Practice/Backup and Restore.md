---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - backup
  - recovery
---

# Backup and Restore

## Current Status

An inactive DEV demo workflow exists. The demo acceptance gate does not require restore evidence, and no secret-free export or restore test has been recorded. Recovery readiness is therefore not approved for live deployment.

## Recovery Objectives

- Scope: Inactive DEV v0.1 workflow and its secret-free documentation/export only.
- Simulated RTO: Four hours.
- Simulated RPO: 24 hours.
- Recovery reviewers: Project Owner and Automation Engineer.
- STAGING and PROD: Not used in v0.1.
- External data recovery: Not applicable because v0.1 performs no writes or sends.

## Version Standard

- `v0.1.0` — initial DEV version.
- `v0.1.x` — v0.1 DEV documentation or bug-fix revision.
- `v0.2.0` — separately approved integration-development version.

## Backup Contents

- [ ] Secret-free n8n workflow export.
- [ ] Node and connection inventory.
- [ ] Credential names and owners without values.
- [ ] Environment-specific resource references.
- [ ] Approved requirements, scoring rule version, and routing version.
- [ ] Test evidence, issues, limitations, deployment, and rollback notes.
- [ ] Evidence that the workflow is inactive and has no credentials or external nodes.

## DEV Backup Procedure

1. Keep the workflow inactive when making risky structural changes.
2. Export the current known-good DEV workflow without credentials or secrets.
3. Record version, export date, operator, and integrity check.
4. Store it in the approved backup location.
5. Validate restore into a separate inactive DEV draft with dummy data.

## v0.1 Restore Procedure

1. Stop manual testing and keep all copies inactive.
2. Select the reviewed secret-free v0.1 export from no more than 24 hours before the last material change where available.
3. Import as a separate inactive DEV draft.
4. Confirm Manual Trigger is the only trigger.
5. Confirm credential count and external-node count are both zero.
6. Confirm workflow version, nodes, connections, score rules, routing rules, payload flags, and seven-day retention.
7. Run the approved dummy smoke fixture.
8. Record whether restoration completed within the simulated four-hour RTO.

No storage or notification reconciliation is needed in v0.1 because there are no side effects.

## Restore Test Record

- Result: not-tested
- Evidence: none
- Environment: DEV
- Simulated RTO target: four hours
- Simulated RPO target: 24 hours

Do not change the result without execution evidence.

## Demo Boundary

The demo phase can close with restore evidence outstanding because the workflow is inactive, uses dummy data, and has no side effects. Before any live deployment, create and verify a secret-free export, perform the documented restore test, and record evidence against the simulated RTO and RPO.

## Deferred v0.2 Recovery

External records, notifications, credentials, duplicate state, reconciliation, replay, STAGING, and PROD recovery require a separate v0.2 procedure.

## Related Notes

- [[Deployment Checklist]]
- [[Maintenance Guide]]
- [[Issues and Fixes]]
