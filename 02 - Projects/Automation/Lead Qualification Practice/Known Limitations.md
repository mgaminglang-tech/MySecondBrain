---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - limitations
---

# Known Limitations

## Purpose

Record current design constraints and unapproved decisions. None are accepted by the client yet.

## Limitation Register

| ID | Limitation | Potential impact | Proposed mitigation | Status |
|---|---|---|---|---|
| LIM-001 | Initial trigger is manual. | No automatic lead capture. | Add an approved form/webhook trigger later. | planned |
| LIM-002 | Storage is preparation-only. | No persistent lead record. | Select Airtable or Google Sheets and add a controlled integration. | planned |
| LIM-003 | Notification is preparation-only. | Sales receives no message. | Select Email or Telegram and add a controlled integration. | planned |
| LIM-004 | Scoring rules are draft. | Results may not reflect sales priorities. | Obtain business approval and version the rules. | pending approval |
| LIM-005 | Sales routing is undefined. | Qualified leads may remain unassigned. | Approve routing table and fallback owner. | pending |
| LIM-006 | Duplicate policy is undefined. | Duplicate records or alerts may occur later. | Approve unique key, window, and merge/replay behavior. | pending |
| LIM-007 | Free-text need quality is difficult to score reliably. | Inconsistent points. | Use a simple approved rule or structured field. | pending |
| LIM-008 | No enrichment is planned. | Missing firmographic data cannot be inferred. | Require fields or add a separately approved enrichment service. | accepted scope assumption |
| LIM-009 | Volume and performance targets are unknown. | Capacity and timeout settings cannot be validated. | Confirm expected load and service targets. | pending |
| LIM-010 | Retention, privacy, and monitoring owners are unknown. | Operational and compliance gaps. | Assign owners before live use. | pending |

## Excluded Scope

- AI scoring, web research, data enrichment, CRM synchronization, marketing sequences, analytics dashboards, and automatic production activation.

## Review Rules

- Limitations require an owner before production.
- Accepted risks require explicit approver, rationale, and review date.
- Update [[Client Handover]] and [[Maintenance Guide]] when a limitation changes.

## Related Notes

- [[Requirements]]
- [[Issues and Fixes]]
- [[Maintenance Guide]]
- [[Client Handover]]

