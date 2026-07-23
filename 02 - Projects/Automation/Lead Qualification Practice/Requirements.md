---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - requirements
  - lead-qualification
---

# Requirements

## Discovery Summary

- Business problem: Manual completeness review, qualification, and forwarding slows lead handling and creates inconsistent decisions.
- Current process: A salesperson reviews each lead and decides what to do.
- Desired outcome: Prepare a consistent qualification result, storage record, and internal notification.
- Stakeholders: Sales operations, sales representatives, project owner, automation maintainer, and data owner.
- Decision owner: To be confirmed by Demo Sales Company.
- Expected volume and frequency: Unknown; must be confirmed.
- Time-sensitive steps: Lead response target is unknown; must be confirmed.

## Scope

### Included

- Dummy manual inputs in DEV.
- Normalization, validation, scoring, status assignment, storage preparation, notification preparation, and final output.
- Proposed lead fields: `lead_id`, `submitted_at`, `full_name`, `email`, `phone`, `company`, `job_title`, `region`, `product_interest`, `budget_band`, `purchase_timeframe`, `need_summary`, `consent_to_contact`, and `source`.
- Explainable score breakdown and reason codes.

### Not Included

- Live capture, enrichment, CRM synchronization, storage writes, notification delivery, dashboards, or production deployment.
- Automated assignment until routing rules are approved.
- Processing real personal or client data during planning or DEV testing.

## Functional Requirements

| ID | Requirement | Priority | Acceptance criterion | Owner |
|---|---|---|---|---|
| FR-001 | Accept one dummy lead through Manual Trigger and Set Sample Lead. | high | A sanitized fixture reaches Normalize Input with the documented fields. | Developer |
| FR-002 | Normalize whitespace, email case, phone formatting, enums, booleans, and missing values. | high | Equivalent inputs produce a consistent normalized schema. | Developer |
| FR-003 | Validate `full_name`, `email`, `company`, `product_interest`, and `consent_to_contact`. | high | Output includes `is_valid`, `missing_fields`, and `validation_errors`. | Project owner |
| FR-004 | Reject malformed email and unsupported enum values. | high | Invalid values receive explicit reason codes and no qualified status. | Developer |
| FR-005 | Calculate a deterministic score from 0–100 and return a score breakdown. | high | Total equals the sum of approved rule points and stays within range. | Project owner |
| FR-006 | Assign `invalid`, `qualified`, `nurture`, or `unqualified`. | high | Status follows validation and approved score thresholds. | Project owner |
| FR-007 | Recommend an assignment target using an approved routing table. | medium | Output records an owner or `UNASSIGNED_REVIEW_REQUIRED`; no silent fallback occurs. | Sales operations |
| FR-008 | Prepare a storage record without writing it. | high | Storage payload contains normalized fields, score, reasons, status, routing, and timestamps. | Developer |
| FR-009 | Prepare an internal notification without sending it. | high | Notification payload contains a subject/title, concise message, severity, recipient role, and lead reference. | Developer |
| FR-010 | Return a final audit-friendly object. | high | Final output preserves validation, scoring, routing, and both prepared payloads. | Developer |
| FR-011 | Identify duplicates before future side effects. | medium | Proposed duplicate key and behavior are documented and testable. | Project owner |

## Data Requirements

| Field | Classification | Required | Validation or normalization |
|---|---|---|---|
| `lead_id` | internal identifier | generated if absent | Stable unique value; generation method to be approved |
| `submitted_at` | operational metadata | yes in final output | ISO 8601 timestamp |
| `full_name` | personal data | yes | Trim; collapse repeated whitespace |
| `email` | personal data | yes | Trim; lowercase; basic format validation |
| `phone` | personal data | no | Trim; preserve country code; do not invent missing digits |
| `company` | business contact data | yes | Trim; collapse repeated whitespace |
| `job_title` | business contact data | no | Trim; map only approved title categories |
| `region` | business contact data | no | Normalize to approved routing values |
| `product_interest` | business intent | yes | Must match approved product list |
| `budget_band` | commercial intent | no | Must match approved bands |
| `purchase_timeframe` | commercial intent | no | Must match approved bands |
| `need_summary` | free text | no | Trim; cap length; do not infer sensitive facts |
| `consent_to_contact` | consent | yes | Explicit boolean; missing is invalid |
| `source` | attribution | no | Normalize to approved source values |

- DEV: dummy or sanitized data only.
- Optional STAGING: dummy/sanitized data unless the data owner explicitly approves another controlled dataset.
- PROD: minimum necessary real data only after privacy, retention, and access approval.
- Retention and deletion requirements: To be confirmed.

## Proposed Scoring Rules

Scoring applies only after validation output exists. An invalid lead remains `invalid` regardless of points.

| Rule | Condition | Points |
|---|---|---:|
| Email type | Business-domain email | 15 |
| Company completeness | Non-empty company after validation | 10 |
| Role fit | Approved decision-maker title category | 20 |
| Budget fit | High = 20; medium = 12; low = 5; unknown = 0 | 0–20 |
| Purchase timeframe | 0–30 days = 20; 31–90 days = 12; 91+ days = 5; unknown = 0 | 0–20 |
| Need clarity | Specific need summary meeting approved minimum quality rule | 15 |

Proposed statuses:

- `invalid`: A required field is missing or invalid, or consent is not explicitly true.
- `qualified`: Valid and score is 70–100.
- `nurture`: Valid and score is 40–69.
- `unqualified`: Valid and score is 0–39.

The business-domain list, title categories, budget bands, timeframe bands, and need-quality rule require approval before implementation.

## Non-Functional Requirements

- Determinism: Same normalized input and rule version must produce the same result.
- Auditability: Include `rule_version`, score breakdown, reason codes, and processing timestamp.
- Performance: Target to be confirmed after expected volume is known.
- Security: Least-privilege credentials; no secret values in notes, nodes, logs, or exports.
- Privacy: Minimize personal data and configure execution retention before live use.
- Reliability: Future side effects require idempotency, bounded retries, timeouts, and failure alerts.
- Maintainability: Rules and routing should be centralized and documented.

## Error and Exception Requirements

- Missing or invalid input: Return `invalid` with explicit errors; do not prepare a sendable sales alert.
- Empty input: Return a controlled invalid result rather than crashing.
- Duplicate input: Flag for review or suppress side effects according to the approved duplicate policy.
- Unsupported enum: Preserve the sanitized raw value only if approved; otherwise return an error code.
- Storage failure: Do not report success; retain safe recovery context and alert the operations role.
- Notification failure after storage: Mark partial failure and allow a notification-only retry without duplicating storage.
- Routing failure: Set `UNASSIGNED_REVIEW_REQUIRED`.

## Success and Acceptance Criteria

- [ ] Demo Sales Company approves required fields, scoring rules, thresholds, statuses, and routing logic.
- [ ] All critical DEV cases in [[Test Plan]] pass with evidence.
- [ ] Invalid leads never receive `qualified`.
- [ ] Every score includes a correct breakdown and approved rule version.
- [ ] No duplicate storage or notification side effect occurs during retry testing.
- [ ] DEV uses only dummy or sanitized data and separate non-production credentials.
- [ ] Storage and notification integrations remain disabled or absent until explicitly authorized.
- [ ] Security, backup, rollback, monitoring, and ownership are documented before PROD approval.

## Open Questions

- What are the approved product, region, title, budget, timeframe, and lead-source values?
- Should a free-email domain reduce points, earn zero, or disqualify?
- Should phone be required for qualified leads?
- How should duplicate leads be merged, updated, ignored, or alerted?
- Should invalid leads be stored for audit, and for how long?
- What assignment rule and fallback owner should apply?
- Which system and channel will be selected for future integrations?

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[Architecture]]
- [[Test Plan]]
- [[Credentials Checklist]]
- [[Known Limitations]]

