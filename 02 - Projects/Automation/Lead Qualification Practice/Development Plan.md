---
type: project-note
status: draft
client: Demo Sales Company
version: v0.1.0
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - development
  - n8n
---

# Development Plan

## Objective

Define how the proposed automation could be built in DEV after requirements and architecture approval. No development has started.

## DEV Procedure

- Proposed name: `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`
- State: Inactive.
- Data: Dummy only.
- Trigger: Manual Trigger.
- Integrations: None.
- Credentials: None.
- Historical duplicate lookup: None; generate the email-derived key only.
- Initial version: `v0.1.0`.

### Planned Build Sequence

- [ ] Obtain approval for [[Requirements]] and [[Architecture]].
- [ ] Create an inactive DEV workflow.
- [ ] Add the ten nodes in the approved linear order.
- [ ] Create the exact dummy fixtures defined in [[Test Plan]].
- [ ] Implement normalization without type coercion or invented data.
- [ ] Implement all approved validation and warning codes.
- [ ] Configure Crypto v2 to generate deterministic SHA-256 `idempotency_key` values as lowercase hexadecimal output without credentials or network requests.
- [ ] Derive the deterministic dummy `lead_id` from the generated hash.
- [ ] Implement approved scoring and exact score reason codes.
- [ ] Implement validation-first statuses, queues, fallback, and human-review flag.
- [ ] Prepare storage payload with `write_requested: false`.
- [ ] Prepare notification payload with `send_requested: false`.
- [ ] Add processing metadata and the complete final output contract.
- [ ] Review node settings and connections.
- [ ] Confirm IF, Switch, and Merge are absent.
- [ ] Execute [[Test Plan]] and record evidence in [[Test Results]].
- [ ] Record defects in [[Issues and Fixes]].
- [ ] Export the validated inactive DEV workflow without secrets.

## STAGING and PROD

STAGING and PROD do not exist in v0.1. No procedure may promote v0.1 outside DEV. Environment design for v0.2 requires a separate approval and specification.

## Planned Components

| Component | Dependency | Done criterion |
|---|---|---|
| Input fixture | Approved data schema | Dummy fixture covers every required field |
| Normalization | Approved enum values | Canonical schema is deterministic |
| Validation | Required-field approval | Errors and missing fields are explicit |
| Identity hash | Crypto v2 | SHA-256 output is lowercase hexadecimal; no credential or network request exists |
| Scoring | Approved weights | Total and breakdown match expected cases |
| Status | Approved thresholds | Validation overrides scoring |
| Routing | Approved regional table | Exact queue, reason, and review flag are present |
| Storage payload | Destination-neutral contract | `prepare_only`; no credential or write |
| Notification payload | Plain-text contract | `prepare_only`; no credential or send |
| Final output | All prior components | One auditable result is returned |

## Definition of Done for DEV

- [ ] Approved requirements are implemented or explicitly deferred.
- [ ] All executable v0.1 DEV tests have evidence.
- [ ] No credentials, integrations, external calls, or real client data were used.
- [ ] Processing is under two seconds per lead at the approved DEV volume.
- [ ] Seven-day log retention and simulated recovery procedures are reviewed.
- [ ] An inactive, secret-free export and version record exist.
- [ ] Project Owner and Automation Engineer decisions are recorded.

## Deferred v0.2 Build

- Persistent duplicate lookup and concurrency control.
- Airtable or Google Sheets writes.
- Email or Telegram sends.
- External API retries, timeouts, error workflow, partial-failure recovery, and reconciliation.
- Any STAGING or PROD workflow.

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[Architecture]]
- [[Test Plan]]
- [[Issues and Fixes]]
- [[Deployment Checklist]]
