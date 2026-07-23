---
type: project
project_type: automation
status: planned
priority: medium
client: Demo Sales Company
owner: Demo Sales Company
version: v0.1.0
created: 2026-07-23
updated: 2026-07-23
tags:
  - project
  - client-automation
  - n8n
  - lead-qualification
---

# Lead Qualification Practice

## Objective

Plan an inactive DEV-only n8n practice automation that accepts one dummy lead, normalizes and validates it, calculates an approved qualification score, assigns a status and sales queue, prepares storage and notification payloads without side effects, and returns an audit-friendly final output.

## Business Problem

The sales team manually reviews incoming leads, checks whether information is complete, decides whether each lead is qualified, and forwards qualified leads to an appropriate salesperson.

## Desired Result

A documented, client-style automation design that can later be built and tested in DEV using dummy data only. Nothing is currently represented as built, tested, deployed, activated, or approved.

## Scope

### Included

- Manual Trigger and one dummy lead per execution.
- Exact input normalization and validation rules from [[Requirements]].
- Deterministic scoring, qualification status, routing, and human-review flags.
- `idempotency_key` generation from normalized email without a historical lookup.
- Destination-neutral storage and notification payload preparation.
- Final output conforming to the approved schema in [[Architecture]].
- Inactive DEV workflow planning, testing, backup, and operational review.

### Not Included

- Creating or modifying an n8n workflow.
- Using n8n MCP.
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

This is a linear ten-node workflow. IF, Switch, and Merge are not used in v0.1. See [[Architecture]] for node responsibilities and data flow.

## Success Criteria

- Every required field is validated against its approved type, enum, format, length, range, consent, or UTC timestamp rule.
- Every valid lead receives the exact score and reason codes defined in [[Requirements]].
- Invalid leads receive `score: null`, machine-readable errors, and `needs_human_review: true`.
- Routing follows the approved regional queue table; fallback uses General Sales Queue and human review.
- The final output contains every field defined in [[Architecture]].
- Each prepared payload explicitly states that no write or send was requested.
- Each executable v0.1 case in [[Test Plan]] produces its exact expected result in under two seconds per lead.
- The inactive DEV workflow uses dummy data, no credentials, and no external side effects.

## Project Workflow

1. Confirm scope and rules in [[Requirements]].
2. Approve the proposed design in [[Architecture]].
3. Confirm access planning in [[Credentials Checklist]].
4. Build only after authorization using [[Development Plan]].
5. Execute the cases in [[Test Plan]] and record evidence in [[Test Results]].
6. Track defects in [[Issues and Fixes]] and constraints in [[Known Limitations]].
7. Prepare recovery and release controls in [[Backup and Restore]] and [[Deployment Checklist]].
8. Define ongoing ownership in [[Maintenance Guide]].
9. Complete [[Lessons Learned]], [[Client Handover]], and [[Case Study]] only after evidence and approval exist.

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

- Required inputs, normalization, validation codes, score rules, statuses, and queues are defined in [[Requirements]].
- v0.1 performs no external lookup, write, send, retry, or concurrency control.
- Airtable, Google Sheets, Email, Telegram, persistent duplicate detection, external retries, and side effects are v0.2 work.
- There is no STAGING or PROD workflow for v0.1.
- Project Owner and Automation Engineer are the approval and operational-review roles.

## Next Action

- [ ] Project Owner and Automation Engineer review the resolved v0.1 specification before authorizing development.

## Related Notes

- [[Development Plan]]
- [[Test Plan]]
- [[Known Limitations]]
- [[Credentials Checklist]]
