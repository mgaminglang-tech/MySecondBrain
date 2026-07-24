---
type: project-note
status: active
client: Demo Sales Company
version: v0.1.0
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - development
  - n8n
---

# Development Plan

## Objective

Record how the inactive DEV practice automation was built and what remains outside the completed demo phase.

## DEV Procedure

- Workflow name: `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`
- State: Inactive.
- Data: Dummy only.
- Trigger: Manual Trigger.
- Integrations: None.
- Credentials: None.
- Historical duplicate lookup: None; generate the email-derived key only.
- Initial version: `v0.1.0`.

### Demo Build Record

- [x] Obtain approval for the v0.1 [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]] and [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]].
- [x] Create an inactive DEV workflow.
- [x] Add the ten nodes in the approved linear order.
- [x] Define exact dummy fixtures in [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]].
- [x] Implement normalization without type coercion or invented data.
- [x] Implement the approved validation and warning codes exercised by the Core Release Suite.
- [x] Configure Crypto v2 to generate deterministic SHA-256 `idempotency_key` values as lowercase hexadecimal output without credentials or network requests.
- [x] Derive the deterministic dummy `lead_id` from the generated hash.
- [x] Implement approved scoring and exact score reason codes.
- [x] Implement validation-first statuses, queues, fallback, and human-review flag.
- [x] Prepare the inert storage payload with `destination: deferred-v0.2` and `operation: none`.
- [x] Prepare the inert notification payload with `channel: internal-preview`.
- [x] Add processing metadata and the complete final output contract.
- [x] Review node settings and connections.
- [x] Confirm IF, Switch, and Merge are absent.
- [x] Execute the 25-test Core Release Suite and record evidence in [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]].
- [x] Record and resolve observed DEV defects in [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]].
- **Deferred:** Export the validated inactive DEV workflow without secrets.

## STAGING and PROD

STAGING and PROD do not exist in v0.1. No procedure may promote v0.1 outside DEV. Environment design for v0.2 requires a separate approval and specification.

## Implemented Demo Components

| Component | Dependency | Done criterion |
|---|---|---|
| Input fixture | Approved data schema | Dummy fixture covers every required field |
| Normalization | Approved enum values | Canonical schema is deterministic |
| Validation | Required-field approval | Errors and missing fields are explicit |
| Identity hash | Crypto v2 | SHA-256 output is lowercase hexadecimal; no credential or network request exists |
| Scoring | Approved weights | Total and breakdown match expected cases |
| Status | Approved thresholds | Validation overrides scoring |
| Routing | Approved regional table | Exact queue, reason, and review flag are present |
| Storage payload | Destination-neutral contract | `destination: deferred-v0.2`, `operation: none`; no credential or write |
| Notification payload | Plain-text contract | `channel: internal-preview`; no credential or send |
| Final output | All prior components | One auditable result is returned |

## Demo Definition of Done

- [x] Approved demo requirements are implemented or explicitly deferred.
- [x] All 25 Core Release Suite tests have evidence.
- [x] Core results are 25 passed, 0 failed, and 0 blocked.
- [x] No credentials, integrations, external calls, side effects, or real client data were used.
- [x] The workflow remained inactive.
- [x] The complete v0.1 output contract was demonstrated.
- [x] Known limitations and deferred features are disclosed.

## Remaining Before Live Deployment

- **Deferred:** Run the 88-test Extended Regression Suite before production deployment or after a major workflow change.
- **Future production gate:** Verify processing performance and seven-day execution-log retention.
- **Deferred:** Create and verify a secret-free backup export and recovery evidence.
- **Future production gate:** Complete operational review and obtain client/owner approval.
- **Deferred:** Design and test integrations, production controls, and production smoke tests separately.

## Deferred v0.2 Build

- Persistent duplicate lookup and concurrency control.
- Airtable or Google Sheets writes.
- Email or Telegram sends.
- External API retries, timeouts, error workflow, partial-failure recovery, and reconciliation.
- Any STAGING or PROD workflow.

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]]
- [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]]
