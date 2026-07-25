---
type: project-note
status: planned
phase: discovery
client: internal-demo
owner: Mervin
created: 2026-07-25
updated: 2026-07-25
tags:
  - client-automation
  - discovery
  - scope
---

# Discovery and Scope

## Discovery Record

- Project: SupportFlow AI — Gmail and Telegram Ticketing System
- Project type: AI Automation and Customer Support Operations
- Owner and current decision-maker: Mervin
- Future client stakeholders: Not Yet Defined
- Target date: Not Yet Defined
- Discovery source: project brief supplied by Mervin on 2026-07-25
- Data classification: dummy and sanitized test data only

## Confirmed Facts

- Gmail and Telegram inquiries are currently separate and may be missed, delayed, duplicated, or classified inconsistently.
- Version one should centralize both channels into a unified ticket process.
- Automatic customer replies, real customer data, credentials, production activation, and unapproved external side effects are prohibited.
- Draft responses require human review and must never be sent automatically.
- The intended tools are n8n, Gmail, Telegram Bot API, Airtable, ClickUp, Slack, and an approved LLM.
- The workflow must remain unbuilt and inactive during the current discovery phase.

## Current Process

The exact current operating procedure, staffing, handoffs, volumes, response expectations, and existing tool configuration are **Not Yet Defined**. The brief confirms that Gmail and Telegram are handled separately and that visibility after assignment is insufficient.

## Desired Version-One Process

1. Receive a dummy or sanitized Gmail or Telegram message.
2. Normalize channel fields into one ticket contract.
3. Validate required fields and reject unsafe or incomplete input.
4. Generate a unique ticket ID.
5. Check Airtable for a duplicate using approved deterministic rules.
6. Classify the request and prepare a draft response with an approved LLM.
7. Validate AI output and apply deterministic business-rule overrides.
8. Store a valid new ticket in an approved DEV Airtable destination.
9. Create a controlled DEV ClickUp task only for a valid, non-duplicate ticket.
10. Send a controlled DEV Slack alert only when approved escalation rules match.
11. Return an auditable result without replying to the customer.

## Included Scope

- Gmail and Telegram intake and channel normalization
- Unified ticket schema and validation
- Ticket identity and duplicate detection
- AI classification and draft generation
- Deterministic rule enforcement and human-review flags
- Airtable ticket storage
- Conditional ClickUp task creation
- Conditional Slack escalation alerts
- Controlled dummy/sanitized DEV testing
- Documentation and sanitized portfolio evidence after verified testing

## Excluded or Deferred Scope

- Website, voice, and phone intake
- Automatic customer responses
- Real customer data and production credentials
- Production integrations, activation, deployment, and live recipients
- Automatic closure or deletion
- Full SLA enforcement and analytics
- Customer-facing portal
- Test Results, Issues and Fixes, deployment-readiness record, and case study until their lifecycle phases begin and evidence exists

## Human Review and Manual Boundaries

- A person reviews every draft before any customer response.
- Invalid, ambiguous, AI-invalid, conflicting, or high-risk tickets require manual review.
- Duplicate disposition and any merge or reopen action remain manual until explicitly defined.
- Workflow activation, credential assignment, and all production actions require separate approval.

## Dependencies

- Approved field contracts and business rules
- Sanitized Gmail and Telegram fixtures
- Approved DEV-only destinations or mocks for Airtable, ClickUp, and Slack
- Approved LLM provider, model, data-handling terms, output schema, and cost limits
- Defined owners for support operations, taxonomy, escalation, and test evidence

## Major Open Questions

| ID | Question | Owner | Due date | Impact | Status |
|---|---|---|---|---|---|
| OQ-001 | What exact Gmail and Telegram fields are available and required? | Mervin | Not Yet Defined | Blocks input contracts | open |
| OQ-002 | What duplicate keys, similarity rules, and time window are approved? | Mervin | Not Yet Defined | Blocks safe idempotency | open |
| OQ-003 | What category, priority, sentiment, and escalation enums are approved? | Mervin | Not Yet Defined | Blocks AI schema and rules | open |
| OQ-004 | Which phrases, amounts, customer tiers, or risk signals override AI output? | Mervin | Not Yet Defined | Blocks escalation rules | open |
| OQ-005 | What Airtable fields, table IDs, and allowed DEV destination will be used? | Mervin | Not Yet Defined | Blocks storage design | open |
| OQ-006 | What ClickUp space, list, task fields, and controlled DEV destination are approved? | Mervin | Not Yet Defined | Blocks task integration | open |
| OQ-007 | What Slack channel or mock destination and alert payload are approved? | Mervin | Not Yet Defined | Blocks alert testing | open |
| OQ-008 | Which LLM provider/model and privacy, retention, budget, and fallback rules are approved? | Mervin | Not Yet Defined | Blocks AI design | open |
| OQ-009 | What expected volume, concurrency, response-time target, retention, and support hours apply? | Mervin | Not Yet Defined | Blocks non-functional requirements | open |
| OQ-010 | Who will own triage, escalation, assignment, rule changes, and future client approval? | Mervin | Not Yet Defined | Blocks operational ownership | open |
| OQ-011 | What sanitized fixtures and exact expected outputs define acceptance? | Mervin | Not Yet Defined | Blocks executable testing | open |

## Risks and Stop Conditions

- Stop before build if required contracts, destinations, or owners remain undefined.
- Stop immediately if real customer data, secret values, or production access appears.
- Stop downstream side effects when validation, duplicate checking, AI schema validation, or deterministic rules fail.
- Do not treat an LLM result as authoritative for refund, safety, legal, account-security, or other high-risk decisions.

## Discovery Readiness Decision

- Selected decision: **CONDITIONAL GO**
- Decision scope: documentation and discovery refinement only
- Decision owner: Mervin
- Decision date: 2026-07-25
- Evidence: approved project brief and approved ten-file documentation scope
- Conditions: resolve OQ-001 through OQ-011 and obtain separate approvals for scope, requirements, architecture, and inactive DEV build
- Next review date: Not Yet Defined

The project is **not ready for implementation**.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
