---
type: checklist
status: draft
client: Demo Sales Company
release: v1.0.0
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - deployment
---

# Deployment Checklist

## Current Status

Deployment is not authorized or scheduled. This checklist is preparatory only.

## DEV Readiness

- [ ] Requirements and architecture approved.
- [ ] Inactive DEV workflow created with the approved name.
- [ ] Dummy/sanitized fixtures and test credentials confirmed.
- [ ] Critical tests passed with evidence in [[Test Results]].
- [ ] Open issues and limitations reviewed.
- [ ] Secret-free DEV export created and verified.

## Optional STAGING Readiness

- [ ] STAGING need and acceptance owner documented.
- [ ] Separate non-production credentials and resources assigned.
- [ ] Integration, retry, duplicate, recovery, and alert cases passed.
- [ ] STAGING results reviewed and accepted.

Skip this section only with a documented decision that STAGING is unnecessary.

## PROD Pre-Deployment Gate

- [ ] Release scope and version approved.
- [ ] Security, privacy, retention, and client-data review completed.
- [ ] Current PROD state backed up without secrets.
- [ ] Rollback trigger, owner, and procedure approved.
- [ ] PROD credentials and resource IDs reviewed by name only.
- [ ] Storage schema, routing table, notification recipients, and message format approved.
- [ ] Idempotency, retries, timeouts, error alerts, and partial-failure recovery reviewed.
- [ ] Sanitized smoke-test record and expected side effects approved.
- [ ] Monitoring and reconciliation owners assigned.
- [ ] Explicit approval to create or modify PROD recorded.
- [ ] Explicit approval to activate PROD recorded.

## Controlled PROD Release

- [ ] Keep the workflow inactive during configuration review.
- [ ] Confirm `PROD - Demo Sales Company - Lead Qualification`.
- [ ] Verify triggers, schedules, time zone, credentials, destinations, and retention.
- [ ] Apply only the approved version in the approved window.
- [ ] Activate only through the authorized operator.
- [ ] Record activation timestamp and version.

## Smoke Test

- [ ] Use the approved sanitized test record.
- [ ] Confirm exactly one expected storage side effect.
- [ ] Confirm exactly one expected internal notification.
- [ ] Confirm scoring, status, routing, and final output.
- [ ] Confirm monitoring and alert paths.
- [ ] Obtain owner acceptance.

## Rollback Gate

Rollback if there is data exposure, misrouting, duplicate side effects, sustained failures, incorrect classification beyond the approved tolerance, or inability to reconcile records.

- [ ] Deactivate or contain harmful processing.
- [ ] Preserve sanitized evidence.
- [ ] Restore the last approved version following [[Backup and Restore]].
- [ ] Re-enable only after explicit approval.

## Release Record

- Outcome: not-deployed
- Execution IDs: none
- Approval: not-requested
- Remaining risks: see [[Known Limitations]]

## Related Notes

- [[Development Plan]]
- [[Test Results]]
- [[Credentials Checklist]]
- [[Backup and Restore]]

