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

Plan an n8n practice automation that accepts a lead, checks completeness, calculates a transparent qualification score, assigns a status, prepares a storage-ready record, prepares an internal sales notification, and returns a final audit-friendly output.

## Business Problem

The sales team manually reviews incoming leads, checks whether information is complete, decides whether each lead is qualified, and forwards qualified leads to an appropriate salesperson.

## Desired Result

A documented, client-style automation design that can later be built and tested in DEV using dummy or sanitized data. Nothing is currently represented as built, tested, deployed, activated, or approved.

## Scope

### Included

- Manual test input for the initial workflow.
- Input normalization and required-field validation.
- Rule-based lead scoring and qualification status.
- Proposed salesperson assignment fields.
- Storage-ready and notification-ready payloads.
- DEV, optional STAGING, and PROD planning.
- Testing, credentials, deployment, backup, maintenance, limitations, and handover documentation.

### Not Included

- Creating or modifying an n8n workflow.
- Using n8n MCP.
- Live lead-capture forms or webhooks.
- Writing records to Airtable or Google Sheets.
- Sending Email or Telegram notifications.
- Real credentials, client data, or production access.
- AI-based qualification or enrichment.

## Proposed Workflow

```text
Manual Trigger
→ Set Sample Lead
→ Normalize Input
→ Validate Required Fields
→ Calculate Lead Score
→ Assign Qualification Status
→ Prepare Storage Record
→ Prepare Internal Notification
→ Final Output
```

See [[Architecture]] for node responsibilities and data flow.

## Success Criteria

- Required fields are validated consistently.
- The score is deterministic, explainable, and limited to 0–100.
- Invalid submissions cannot be marked qualified.
- Status rules match the approved thresholds.
- Output contains a normalized lead, validation result, score breakdown, status, assignment recommendation, storage payload, notification payload, and processing metadata.
- Dummy DEV fixtures produce the expected results once testing is authorized and performed.
- No live storage write or notification occurs in the initial workflow.

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

- The first development version will use Manual Trigger and dummy leads.
- Email is the primary unique identifier unless the owner selects another ID.
- Score inputs will be supplied directly; no enrichment service is planned.
- “Appropriate salesperson” requires an approved routing table that is not yet defined.
- Optional STAGING will be used only if approval, integration risk, or client process justifies it.

## Key Risks

- Unapproved scoring rules could classify leads unfairly or inaccurately.
- Free-text fields can be inconsistent or misleading.
- Duplicate leads may generate duplicate records or notifications.
- Incorrect routing data could assign a qualified lead to the wrong salesperson.
- Future storage or notification outages could cause partial processing.
- Execution logs could retain more lead data than necessary if not configured carefully.

## Decisions Needed Before Development

- Which fields are mandatory?
- Are the proposed score weights and thresholds approved?
- What statuses and reason codes should sales use?
- How should salesperson assignment work by region, product, industry, or round robin?
- Which storage system will be used: Airtable or Google Sheets?
- Which notification channel will be used: Email or Telegram?
- What duplicate key and duplicate window should apply?
- What volumes, response-time target, retention period, and support window are expected?
- Is STAGING required?
- Who approves DEV testing and any future PROD deployment?

## Next Action

- [ ] Demo Sales Company reviews and approves [[Requirements]] and [[Architecture]] before development begins.

## Related Notes

- [[Development Plan]]
- [[Test Plan]]
- [[Known Limitations]]
- [[Credentials Checklist]]

