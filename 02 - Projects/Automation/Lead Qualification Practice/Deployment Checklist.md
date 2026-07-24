---
type: checklist
status: draft
client: Demo Sales Company
release: v0.1.0
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - deployment
---

# Deployment Checklist

## Current Status

The controlled inactive DEV demo is accepted. This is not a deployment approval: no STAGING or PROD deployment is permitted, and production readiness remains unapproved.

## v0.1 DEV Readiness

- [x] Demo [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]] and [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] are approved.
- [x] Inactive DEV workflow created with the approved name.
- [x] Manual Trigger and dummy fixtures confirmed.
- [x] Exact ten-node linear order matches [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]].
- [x] Crypto v2 uses SHA-256 lowercase hexadecimal output with no credential or network request.
- [x] IF, Switch, and Merge are absent.
- [x] Credential inventory confirms zero credentials.
- [x] Node inventory confirms zero external lookup, write, send, or API nodes.
- [x] All 25 Core Release Suite tests pass with evidence in [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]].
- **Future production gate:** Processing time is under two seconds per lead.
- **Future production gate:** Seven-day DEV execution-log retention is configured and reviewed.
- [x] Open issues and limitations reviewed for the demo.
- **Deferred:** Secret-free DEV export created and verified.

## Controlled v0.1 Review

- [x] Confirm name `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`.
- [x] Confirm workflow remains inactive before and after each manual test.
- [x] Confirm final output includes all 16 required top-level keys.
- [x] Confirm storage payload uses `destination: deferred-v0.2`, `operation: none`, and the complete prepared record.
- [x] Confirm notification payload uses `channel: internal-preview` and the approved status-based preview rules.
- [x] Confirm invalid and fallback-routing cases require human review.
- [x] Record demo review date, workflow version, and available execution IDs in [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]].

## v0.1 Rollback Gate

Restore the last reviewed inactive DEV export if validation, scoring, routing, schema, performance, or retention differs from the approved specification.

- **Procedural rollback step:** Stop manual testing.
- **Procedural rollback step:** Preserve dummy-data evidence.
- **Procedural rollback step:** Restore following [[02 - Projects/Automation/Lead Qualification Practice/Backup and Restore|Backup and Restore]].
- **Procedural rollback step:** Re-test before review continues.

## Demo Release Record

- Outcome: controlled inactive DEV demo accepted
- Date: 2026-07-24
- Core results: 25 passed; 0 failed; 0 blocked
- Execution IDs: recorded in [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]]
- Workflow state: inactive
- Production approval: not granted
- Remaining risks: see [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]]

## Production Blockers

- **Deferred:** Run the 88-test Extended Regression Suite before production deployment or after a major workflow change.
- **Future production gate:** Complete operational review, recovery evidence, and client/owner approval.
- **Deferred:** Complete integration testing and production smoke testing.
- **Future production gate:** Approve STAGING/PROD architecture, credentials, rollback, and activation separately.

## Deferred v0.2 Deployment

STAGING, PROD, credentials, integrations, side-effect smoke tests, external retries, reconciliation, activation, and production rollback require a new v0.2 deployment plan and explicit approval.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]]
- [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]]
- [[02 - Projects/Automation/Lead Qualification Practice/Backup and Restore|Backup and Restore]]
