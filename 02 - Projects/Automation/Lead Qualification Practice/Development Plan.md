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

- Proposed name: `DEV - Demo Sales Company - Lead Qualification Practice`
- Data: dummy or sanitized only.
- Trigger: Manual Trigger.
- Integrations: omitted, mocked, or connected only to controlled test destinations.
- Credentials: `DEV - Service - Purpose`.
- Initial version: `v0.1.0`.

### Planned Build Sequence

- [ ] Obtain approval for [[Requirements]] and [[Architecture]].
- [ ] Create an inactive DEV workflow.
- [ ] Add the nine nodes in the approved order.
- [ ] Create sanitized fixtures for high, medium, low, invalid, duplicate, and malformed inputs.
- [ ] Implement normalization without inventing missing data.
- [ ] Implement validation and explicit reason codes.
- [ ] Implement approved score rules with `rule_version`.
- [ ] Implement validation-first statuses and routing fallback.
- [ ] Prepare destination-neutral storage and notification payloads.
- [ ] Add idempotency, bounded error behavior, and audit metadata.
- [ ] Review node settings and connections.
- [ ] Execute [[Test Plan]] and record evidence in [[Test Results]].
- [ ] Record defects in [[Issues and Fixes]].
- [ ] Export the validated inactive DEV workflow without secrets.

## Optional STAGING Procedure

STAGING is not assumed. Add it only if the project owner requires integration-level acceptance or risk warrants a production-like rehearsal.

- [ ] Document why STAGING is required.
- [ ] Create a separate inactive STAGING copy with separate credentials and destinations.
- [ ] Use dummy/sanitized data unless the data owner approves otherwise.
- [ ] Re-run approved integration, retry, idempotency, and recovery cases.
- [ ] Obtain reviewer acceptance before production planning.

## PROD Procedure

PROD work is not authorized by this plan.

- [ ] Confirm approved requirements, tests, limitations, data handling, owners, and support model.
- [ ] Create and verify a secret-free backup.
- [ ] Map separate PROD credentials by name.
- [ ] Review resource IDs, routing, recipients, retention, retries, timeouts, and error alerts.
- [ ] Obtain explicit approval to create or modify PROD.
- [ ] Obtain separate explicit approval to activate PROD.
- [ ] Use a controlled release window, sanitized smoke-test record, and monitoring.
- [ ] Roll back if the documented threshold is met.

## Planned Components

| Component | Dependency | Done criterion |
|---|---|---|
| Input fixture | Approved data schema | Sanitized fixture covers all fields |
| Normalization | Approved enum values | Canonical schema is deterministic |
| Validation | Required-field approval | Errors and missing fields are explicit |
| Scoring | Approved weights | Total and breakdown match expected cases |
| Status | Approved thresholds | Validation overrides scoring |
| Routing | Approved sales routing table | Owner or safe fallback is always present |
| Storage payload | Chosen destination schema | Payload validates without a live write |
| Notification payload | Chosen channel format | Payload validates without a live send |
| Final output | All prior components | One auditable result is returned |

## Definition of Done for DEV

- [ ] Approved requirements are implemented or explicitly deferred.
- [ ] All critical DEV tests have evidence.
- [ ] No real credentials or unredacted client data were used.
- [ ] Failure and recovery behaviors are documented.
- [ ] An inactive, secret-free export and version record exist.
- [ ] Reviewer decision and unresolved limitations are recorded.

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[Architecture]]
- [[Test Plan]]
- [[Issues and Fixes]]
- [[Deployment Checklist]]

