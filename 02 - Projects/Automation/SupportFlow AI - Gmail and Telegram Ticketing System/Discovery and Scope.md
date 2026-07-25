---
type: project-note
status: in-progress
phase: phase-1-validated
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
- The Phase 1 credential-free workflow is built, manually validated, and inactive; integrations remain unbuilt.

## Approved Discovery Decisions

- Gmail allowlist: message ID, thread ID, received timestamp, sanitized sender reference and name, subject, plain-text body, and attachment metadata.
- Telegram allowlist: update ID, message ID, chat ID, received timestamp, sanitized sender reference and name, text or caption, reply-to ID, and attachment metadata.
- Gmail HTML is converted to text when a plain-text body is unavailable. Message text is limited to 5,000 characters.
- Attachment contents and edited Telegram messages are excluded from schema `0.1.0`.
- Required fields fail closed before AI, storage, task creation, or alerts.
- Duplicate handling uses exact identity and content fingerprints with the approved windows and outcomes.
- Eight categories, four priorities, deterministic overrides, one Airtable `Tickets` table, Mervin assignment, controlled Slack alerts, Gemini controls, and operating defaults are approved as documented in the project notes.
- Ticket ID, sentiment, content-fingerprint normalization and `\u001F` separator, DEV concurrency/retry rules, reserved resource names, deferred Gemini-model selection, fixture IDs, and deterministic escalation examples are approved.

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

- Remaining executable field contracts and business rules listed below
- Sanitized Gmail and Telegram fixtures
- Approved DEV-only destinations or mocks for Airtable, ClickUp, and Slack
- Approved LLM provider, model, data-handling terms, output schema, and cost limits
- Defined owners for support operations, taxonomy, escalation, and test evidence

## Decision Resolution

| ID | Question | Owner | Due date | Impact | Status |
|---|---|---|---|---|---|
| OQ-001 | Gmail and Telegram allowlists and required fields | Mervin | 2026-07-25 | Input contract | resolved |
| OQ-002 | Exact and content-based duplicate behavior and windows | Mervin | 2026-07-25 | Idempotency | resolved |
| OQ-003 | Eight categories and four priorities | Mervin | 2026-07-25 | Classification | resolved |
| OQ-004 | Approved deterministic escalation framework | Mervin | 2026-07-25 | Routing | resolved |
| OQ-005 | Resource names approved; actual Airtable resource IDs remain deferred | Mervin | 2026-07-25 | Integration work only | deferred |
| OQ-006 | ClickUp list name and Mervin assignment approved; actual list ID remains deferred | Mervin | 2026-07-25 | Integration work only | deferred |
| OQ-007 | Slack channel name and alert contract approved; actual channel ID remains deferred | Mervin | 2026-07-25 | Integration work only | deferred |
| OQ-008 | Google Gemini approved; OpenAI removed; exact free-tier model and credential deferred until compatibility evidence exists | Mervin | 2026-07-25 | AI integration only | resolved-with-deferred-model |
| OQ-009 | Capacity, retention, recovery, and replay defaults | Mervin | 2026-07-25 | Non-functional design | resolved |
| OQ-010 | Mervin owns portfolio-phase decisions and operations | Mervin | 2026-07-25 | Ownership | resolved |
| OQ-011 | IDs `SF-FX-001` through `SF-FX-030` reserved; six Phase 1 seeds approved | Mervin | 2026-07-25 | Skeleton validation | resolved |
| OQ-012 | Ticket ID `SF-YYYYMMDD-XXXXXXXX` using UUID v4 suffix | Mervin | 2026-07-25 | Identity contract | resolved |
| OQ-013 | Optional sentiment enum with `unknown` default | Mervin | 2026-07-25 | Mock AI schema | resolved |
| OQ-014 | Sequential fixtures, idempotency recheck, bounded read retries, and 15-second timeout | Mervin | 2026-07-25 | DEV reliability | resolved-for-dev |
| OQ-015 | Fingerprint uses normalized sender, subject, and message text separated by `\u001F`; schema version is `0.1.0` | Mervin | 2026-07-25 | Data contract | resolved |
| OQ-016 | Telegram source-event, message, conversation, and parent mapping | Mervin | 2026-07-25 | Channel mapping | resolved |
| OQ-017 | Gmail dedicated DEV mailbox and Telegram dedicated DEV bot/private chat | Mervin | Not Yet Defined | Trigger integration | partially resolved; identities not assigned |
| OQ-018 | Gemini, Airtable, ClickUp, and Slack review-cycle limits | Mervin | 2026-07-25 | DEV cost and side effects | resolved |

## Approved Phase 2 Integration Boundaries

- Gemini: free tier only, maximum 500 calls per review cycle, structured JSON only, sanitized text only, and no paid usage, tools, browsing, code execution, attachment contents, or direct identifiers.
- Airtable: maximum 100 created DEV test records per review cycle.
- ClickUp: maximum 100 created DEV tasks per review cycle.
- Slack: maximum 30 DEV alerts per review cycle.
- Gmail: dedicated DEV mailbox, dummy/sanitized messages, read-only access, and no message or label mutation.
- Telegram: dedicated DEV bot, one private DEV chat, dummy new-message updates only, and no outbound messages, file downloads, or administrator permissions.
- Stop immediately for real data, an unexpected resource, broader permissions, out-of-bound external action, unexpected billing, or failed idempotency.

## Risks and Stop Conditions

- Stop before build if required contracts, destinations, or owners remain undefined.
- Stop immediately if real customer data, secret values, or production access appears.
- Stop downstream side effects when validation, duplicate checking, AI schema validation, or deterministic rules fail.
- Do not treat an LLM result as authoritative for refund, safety, legal, account-security, or other high-risk decisions.

## Discovery Readiness Decision

- Selected decision: **GO for Phase 1 — Credential-Free n8n Skeleton only**
- Decision scope: the exact fixture-driven, credential-free skeleton boundary
- Decision owner: Mervin
- Decision date: 2026-07-25
- Evidence: approved project brief and approved Discovery Decision Pack with duplicate and LLM refinements
- Conditions: external integration decisions remain deferred and prohibited in Phase 1
- Next review date: Not Yet Defined

The Phase 1 skeleton build and six authorized fixture runs are complete. Any Pre-Integration Readiness Review or integration work requires separate approval.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
