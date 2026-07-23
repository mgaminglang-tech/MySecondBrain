---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - maintenance
---

# Maintenance Guide

## Purpose

Define proposed operational ownership and safe change control. No live service currently exists.

## Ownership to Assign

| Responsibility | Primary owner | Backup owner |
|---|---|---|
| Workflow operations | to be confirmed | to be confirmed |
| Scoring and status policy | Demo Sales Company sales owner | to be confirmed |
| Sales routing table | Sales operations | to be confirmed |
| Credentials | Service account owner | to be confirmed |
| Data privacy and retention | Data owner | to be confirmed |
| Incident response | Automation operations owner | to be confirmed |

## DEV Maintenance

- Use dummy or sanitized data only.
- Make changes in an inactive DEV workflow.
- Version scoring and routing changes.
- Re-run affected and regression cases in [[Test Plan]].
- Preserve a secret-free known-good export.

## Optional STAGING Maintenance

- Use only when adopted and documented.
- Keep resources and credentials separate.
- Rehearse material integration or recovery changes before production.

## PROD Maintenance

- Record the change request, impact, owner, and version.
- Reproduce and verify in DEV first.
- Update tests, issues, limitations, backup, and rollback notes.
- Obtain explicit approval before modifying or activating PROD.
- Deploy in a controlled window, smoke test, reconcile, and monitor.

## Proposed Monitoring

- Failed and partial executions.
- Invalid-rate spikes.
- Qualification distribution changes after rule updates.
- Duplicate detections and duplicate side-effect prevention.
- Unassigned qualified leads.
- Storage and notification delivery divergence.
- Credential expiry and vendor/API changes.

## Suggested Routine

| Activity | Suggested frequency | Evidence |
|---|---|---|
| Review failures and unassigned leads | daily on business days | Sanitized execution references |
| Reconcile accepted leads with storage | daily | Count and exception report |
| Review credential expiry | monthly | Access review record |
| Verify backup freshness | before each release and monthly | Backup inventory |
| Review scoring and routing performance | monthly initially | Approved aggregate report |
| Test restore and alert path | quarterly or per policy | Test evidence |
| Review retention and access | quarterly | Owner approval |

Frequencies are recommendations pending service-volume and policy decisions.

## Incident Response

1. Contain harmful processing if authorized.
2. Preserve sanitized evidence and note affected versions.
3. Identify whether storage, notification, or both were affected.
4. Prevent duplicate replay using the approved idempotency policy.
5. Restore or fix in DEV, verify, then obtain PROD approval.
6. Reconcile records and notifications after recovery.

## Related Notes

- [[Credentials Checklist]]
- [[Backup and Restore]]
- [[Known Limitations]]
- [[Client Handover]]

