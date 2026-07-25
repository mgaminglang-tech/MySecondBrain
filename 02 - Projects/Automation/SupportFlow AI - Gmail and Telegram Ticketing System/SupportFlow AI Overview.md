---
type: project
project_type: ai-automation
status: in-progress
phase: phase-1-validated
priority: medium
client: internal-demo
owner: Mervin
production_ready: false
version: 0.1.0
created: 2026-07-25
updated: 2026-07-25
tags:
  - project
  - client-automation
  - n8n
  - customer-support
  - ai
---

# SupportFlow AI — Gmail and Telegram Ticketing System

## Objective

Design a centralized DEV-only support-ticket process that converts dummy or sanitized Gmail and Telegram messages into one validated ticket structure, detects duplicates, classifies requests, prepares unsent draft responses, stores approved test records, creates controlled test tasks, and produces controlled escalation alerts.

## Initial State

- Status: in-progress
- Current phase: Phase 1 credential-free skeleton validated
- Owner and current approver: Mervin
- Target date: Not Yet Defined
- Production ready: false
- Canonical workflow name: `DEV - SupportFlow AI - Gmail and Telegram Ticketing System`
- Workflow state: built and inactive; workflow ID `cyiCqsjLQdB7apjP`
- Testing state: Phase 1 seed suite passed; integration testing not-run
- Data classification: dummy and sanitized test data only
- External side effects: not approved
- Production credentials, integrations, deployment, and activation: not approved

## Business Problem

Support inquiries arrive through Gmail and Telegram but are managed separately. This creates risk of missed or delayed requests, duplicate tickets, inconsistent classification, missed refund or urgent escalations, limited post-assignment visibility, and unreliable response and resolution-time measurement.

## Desired Outcome

Both channels produce the same auditable ticket structure and follow a controlled path through validation, identity generation, duplicate checking, classification, draft preparation, storage, task preparation or creation, and conditional escalation. No response is automatically sent to a customer.

## Scope

### Included

- Gmail and Telegram intake design
- Channel-specific normalization into a unified ticket
- Required-field validation and unique ticket ID generation
- Airtable duplicate checking and ticket storage
- AI-assisted category, priority, sentiment, escalation, and draft response
- Deterministic business-rule enforcement after AI output
- ClickUp task creation for valid, non-duplicate tickets
- Slack alerts for approved urgent, refund, or high-risk conditions
- Controlled DEV testing with dummy or sanitized data

### Not Included

- Website forms, voice, or phone support
- Automatic customer replies
- Real customer data or production credentials
- Production integrations, activation, or deployment
- Automatic ticket closure or deletion
- Full SLA enforcement, analytics dashboard, or customer portal

## Planned Workflow

```text
Gmail intake ─┐
              ├→ Normalize → Validate → Generate ticket ID
Telegram ─────┘              → Duplicate check
                              → AI classification and draft
                              → Apply deterministic rules
                              → Store ticket
                              → Create controlled ClickUp task
                              → Send controlled Slack alert when eligible
                              → Return audit summary
```

The credential-free portion of this architecture is implemented and validated only within the approved Phase 1 boundary. All integration stages remain proposed.

## Success Criteria

- Both inputs produce the approved unified structure.
- Invalid inputs stop safely without downstream ticket, task, or alert side effects.
- Every valid new request receives a unique ticket ID.
- Documented duplicate rules prevent duplicate downstream actions.
- AI output is schema-validated and constrained to approved values.
- Draft responses are stored for review and never automatically sent.
- Airtable, ClickUp, and Slack actions occur only under approved DEV test controls.
- Evidence distinguishes `passed`, `failed`, `blocked`, `not-run`, and `deferred`.
- The workflow remains inactive and credential-safe throughout development.

## Approved Discovery Decisions

- Gmail and Telegram use explicit source-field allowlists, HTML-to-text conversion where needed, and a 5,000-character message limit.
- Attachment contents and edited Telegram messages are excluded from schema `0.1.0`.
- Required-field validation fails closed before AI or downstream actions.
- Duplicate handling distinguishes exact duplicates from content-based possible duplicates.
- The approved categories are `billing`, `refund`, `account-access`, `technical-support`, `product-question`, `order-delivery`, `feedback-complaint`, and `other`.
- Priorities are `p1-critical`, `p2-high`, `p3-normal`, and `p4-low`; deterministic rules override AI output.
- Airtable uses one `Tickets` table. Mervin is the initial DEV ClickUp assignee.
- Slack alerts are limited to approved P1/P2 or deterministic escalation rules.
- Google Gemini is the controlled DEV LLM provider with approved privacy, fallback, retry, free-tier, and no-paid-usage boundaries. OpenAI is no longer approved for this project.
- Planning assumes 30 sanitized fixtures, 100 tickets per day, a peak of 10 messages per five minutes, seven-day DEV execution retention, 30-day test-record retention, RTO four hours, RPO 24 hours, manual replay, and Mervin as portfolio-phase owner.
- Ticket IDs use `SF-YYYYMMDD-XXXXXXXX`, where the suffix is the first eight uppercase hexadecimal characters of a UUID v4 and never derives from personal or customer information.
- Sentiment is optional: `positive`, `neutral`, `negative`, or `unknown`, defaulting to `unknown`; it never independently changes priority or triggers alerts.
- Content fingerprints use the approved NFKC normalization and SHA-256 contract with `\u001F` between normalized sender reference, subject, and message text.
- Phase 1 uses six approved seed fixtures and mocked duplicate and AI results; live integrations remain deferred.

## Current Decision

**GO — the Phase 1 credential-free skeleton meets its approved build and test boundary.** This decision is not integration, demo, production, deployment, or activation approval.

## Approved Phase 1 Boundary

Manual Trigger → dummy Gmail and Telegram payloads → channel normalization → unified ticket → required-field validation → ticket ID and content fingerprint → mocked duplicate result → mocked AI classification and draft → deterministic rules → final structured output.

Phase 1 prohibits Gmail or Telegram triggers, Airtable, ClickUp, Slack, or Gemini connections, credentials, external side effects, real data, workflow activation, and production claims.

## Approved Phase 2 Decisions

- Provider: Google Gemini; Mervin accepts free-tier processing for sanitized dummy DEV fixtures only. The exact free-tier, structured-JSON-compatible model remains Not Yet Defined pending credential-grounded model-list validation.
- Gemini boundary: dedicated DEV project and API key, sanitized text only, 5,000-character maximum, no attachment contents, direct identifiers, tools, browsing, code execution, external actions, or paid use.
- Schema version: `0.1.0`.
- Fingerprint input: normalized sender reference + `\u001F` + normalized subject + `\u001F` + normalized message text, then SHA-256.
- Telegram mapping: `update_id` → `source_event_id`; `message_id` → `source_message_id`; `chat_id` → `source_conversation_id`; `reply_to_message_id` → `source_parent_message_id`, defaulting to null.
- DEV limits per review cycle: 500 Gemini calls, 100 Airtable records, 100 ClickUp tasks, and 30 Slack alerts.
- Gmail uses a future dedicated DEV mailbox and read-only trigger boundary. Telegram uses a future dedicated DEV bot and one private DEV chat with new-message updates only.
- Airtable is assigned as base `appell78p9BIEek9J`, table `tblI3JYon6kLqZPbP`, with `ticket_id` as the primary field and `Asia/Manila` date-time display. Other resource IDs, all credentials, and the exact Gemini model remain Not Yet Assigned.

## Phase 1 Evidence

- Workflow ID: `cyiCqsjLQdB7apjP`
- Saved state: inactive; `activeVersionId` is null
- Node count: 14
- Credentials and external-service nodes: none
- Initial manual execution IDs: `7107`, `7108`, `7109`, `7110`, `7111`, `7112`
- Schema-alignment rerun IDs: `7113`, `7114`, `7115`, `7116`, `7117`, `7118`
- Rerun result: `SF-FX-001` through `SF-FX-006` — 6 passed, 0 failed
- Verified alignment: schema `0.1.0`, approved unified source fields, and SHA-256 of the normalized three-component input separated by `\u001F`
- External actions, customer replies, and real-data use: none

## Next Action

**NO-GO for Airtable credential creation until the approved physical priority rename is applied and verified.** JSON serialization, `ai_schema_valid`, retry, timeout, ambiguous-create, and persistent-failure decisions are now approved. No Airtable schema change, credential creation, connection, record action, workflow change, activation, or integration execution is authorized by this documentation update.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Automation Project Checklist|Automation Project Checklist]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
