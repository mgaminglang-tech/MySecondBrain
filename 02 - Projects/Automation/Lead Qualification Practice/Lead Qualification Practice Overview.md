---
type: project
project_type: automation
status: demo-complete
phase: demo-closure
priority: medium
client: Demo Sales Company
owner: Mervin
production_ready: false
version: v0.1.0
created: 2026-07-23
updated: 2026-07-24
tags:
  - project
  - client-automation
  - n8n
  - lead-qualification
---

# Lead Qualification Practice

## Objective

Maintain an inactive DEV-only n8n practice automation that accepts one dummy lead, normalizes and validates it, calculates an approved qualification score, assigns a status and sales queue, prepares storage and notification payloads without side effects, and returns an audit-friendly final output.

## Phase Status

- Demo phase: complete.
- Demo acceptance gate: 25 of 25 Core Release Suite tests passed; 0 failed; 0 blocked.
- Extended Regression Suite: 88 tests not run; required before production deployment or after a major workflow change.
- v0.2 integration tests: 10 deferred.
- Production readiness: not approved.
- Full project closure: not applicable while operational review, recovery evidence, owner approval, integrations, and production validation remain outstanding.

## Business Problem

The sales team manually reviews incoming leads, checks whether information is complete, decides whether each lead is qualified, and forwards qualified leads to an appropriate salesperson.

## Desired Result

An evidence-backed, client-style practice automation that is safe to demonstrate in inactive DEV with dummy data only. The controlled demo is accepted; no production deployment, activation, live-data use, or operational approval is claimed.

## Scope

### Included

- Manual Trigger and one dummy lead per execution.
- Exact input normalization and validation rules from [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]].
- Deterministic scoring, qualification status, routing, and human-review flags.
- `idempotency_key` generation from normalized email without a historical lookup.
- Destination-neutral storage and notification payload preparation.
- Final output conforming to the approved schema in [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]].
- Inactive DEV workflow planning, testing, backup, and operational review.

### Not Included

- Live lead-capture forms or webhooks.
- Writing records to Airtable or Google Sheets.
- Sending Email or Telegram notifications.
- Historical duplicate lookup or persistent state.
- External API retries, concurrency control, and side effects.
- STAGING or PROD configuration for v0.1.
- Real credentials, client data, or production access.
- AI-based qualification or enrichment.

## Proposed Workflow

Canonical inactive DEV workflow name: `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`

```text
Manual Trigger
→ Set Sample Lead
→ Normalize Input
→ Validate Required Fields
→ Generate Identity Hash — Crypto v2
→ Calculate Lead Score
→ Assign Qualification Status and Routing
→ Prepare Storage Record
→ Prepare Internal Notification
→ Final Output
```

This is a linear ten-node workflow. IF, Switch, and Merge are not used in v0.1. See [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] for node responsibilities and data flow.

## Success Criteria

- Every required field is validated against its approved type, enum, format, length, range, consent, or UTC timestamp rule.
- Every valid lead receives the exact score and reason codes defined in [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]].
- Invalid leads receive `score: null`, machine-readable errors, and `needs_human_review: true`.
- Routing follows the approved regional queue table; fallback uses General Sales Queue and human review.
- The final output contains every field defined in [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]].
- Each prepared payload explicitly states that no write or send was requested.
- The 25-test Core Release Suite in [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]] produces its exact expected results.
- The inactive DEV workflow uses dummy data, no credentials, and no external side effects.
- Known limitations and v0.2 deferrals are disclosed.

The demo criteria above are satisfied. The 88-test Extended Regression Suite, performance confirmation, operational review, recovery evidence, client/owner approval, integration testing, and production smoke testing remain outside the completed demo gate.

## Project Workflow

1. Confirm scope and rules in [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]].
2. Approve the proposed design in [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]].
3. Confirm access planning in [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]].
4. Build only after authorization using [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]].
5. Execute the cases in [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]] and record evidence in [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]].
6. Track defects in [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]] and constraints in [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]].
7. Prepare recovery and release controls in [[02 - Projects/Automation/Lead Qualification Practice/Backup and Restore|Backup and Restore]] and [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]].
8. Define ongoing ownership in [[02 - Projects/Automation/Lead Qualification Practice/Maintenance Guide|Maintenance Guide]].
9. Complete [[02 - Projects/Automation/Lead Qualification Practice/Lessons Learned|Lessons Learned]], [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]], and [[02 - Projects/Automation/Lead Qualification Practice/Case Study|Case Study]] only after evidence and approval exist.

## Assumptions

- v0.1 is DEV-only, inactive, manual, and limited to dummy data.
- Valid identity inputs use the approved SHA-256 of normalized email and normalized `submitted_at`.
- Missing or invalid identity inputs use the approved canonical raw-input fallback hash.
- These deterministic identifiers do not detect stored duplicates or protect concurrent processing.
- Expected DEV volume is no more than 100 test leads per day.
- Target processing time is under two seconds per lead.
- DEV execution logs are retained for seven days.
- Simulated recovery targets are RTO four hours and RPO 24 hours.
- Project Owner and Automation Engineer approve and review v0.1.

## Key Risks

- Keyword scoring can miss valid needs expressed with unapproved synonyms.
- The five-entry free-email list is intentionally limited and may require later maintenance.
- The email-derived idempotency key is not persistent duplicate detection.
- Unsupported regions fall back safely but require human review.
- Destination escaping must be implemented in v0.2 before storage or notification side effects.
- DEV logs contain dummy lead payloads and must still follow the seven-day retention rule.

## Approved v0.1 Decisions

- Required inputs, normalization, validation codes, score rules, statuses, and queues are defined in [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]].
- v0.1 performs no external lookup, write, send, retry, or concurrency control.
- Airtable, Google Sheets, Email, Telegram, persistent duplicate detection, external retries, and side effects are v0.2 work.
- There is no STAGING or PROD workflow for v0.1.
- Project Owner and Automation Engineer are the approval and operational-review roles.

## Next Action

Decide whether to archive the demo project or continue with v0.2.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]]
- [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]]
