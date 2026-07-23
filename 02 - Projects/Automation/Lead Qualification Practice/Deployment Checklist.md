---
type: checklist
status: draft
client: Demo Sales Company
release: v0.1.0
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - deployment
---

# Deployment Checklist

## Current Status

v0.1 is an inactive DEV artifact only. No STAGING or PROD deployment is permitted.

## v0.1 DEV Readiness

- [ ] Project Owner and Automation Engineer approve [[Requirements]] and [[Architecture]].
- [ ] Inactive DEV workflow created with the approved name.
- [ ] Manual Trigger and dummy fixtures confirmed.
- [ ] Exact ten-node linear order matches [[Architecture]].
- [ ] Crypto v2 uses SHA-256 lowercase hexadecimal output with no credential or network request.
- [ ] IF, Switch, and Merge are absent.
- [ ] Credential inventory confirms zero credentials.
- [ ] Node inventory confirms zero external lookup, write, send, or API nodes.
- [ ] All executable v0.1 tests pass with evidence in [[Test Results]].
- [ ] Processing time is under two seconds per lead.
- [ ] Seven-day DEV execution-log retention is configured and reviewed.
- [ ] Open issues and limitations reviewed.
- [ ] Secret-free DEV export created and verified.

## Controlled v0.1 Review

- [ ] Confirm name `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`.
- [ ] Confirm workflow remains inactive before and after each manual test.
- [ ] Confirm final output includes all 16 required top-level keys.
- [ ] Confirm storage payload uses `destination: deferred-v0.2`, `operation: none`, and the complete prepared record.
- [ ] Confirm notification payload uses `channel: internal-preview` and the approved status-based preview rules.
- [ ] Confirm invalid and fallback-routing cases require human review.
- [ ] Record review date, workflow version, execution IDs, and reviewer decisions.

## v0.1 Rollback Gate

Restore the last reviewed inactive DEV export if validation, scoring, routing, schema, performance, or retention differs from the approved specification.

- [ ] Stop manual testing.
- [ ] Preserve dummy-data evidence.
- [ ] Restore following [[Backup and Restore]].
- [ ] Re-test before review continues.

## Release Record

- Outcome: not-reviewed
- Execution IDs: none
- Approval: not-requested
- Remaining risks: see [[Known Limitations]]

## Deferred v0.2 Deployment

STAGING, PROD, credentials, integrations, side-effect smoke tests, external retries, reconciliation, activation, and production rollback require a new v0.2 deployment plan and explicit approval.

## Related Notes

- [[Development Plan]]
- [[Test Results]]
- [[Credentials Checklist]]
- [[Backup and Restore]]
