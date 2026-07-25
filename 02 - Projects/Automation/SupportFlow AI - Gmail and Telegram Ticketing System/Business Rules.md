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
  - business-rules
  - customer-support
---

# Business Rules

## Status

Approved rules for the credential-free Phase 1 skeleton. Integration behavior remains deferred.

## Evaluation Order

1. Normalize source data.
2. Validate required fields and safety limits.
3. Generate approved identity values.
4. Determine duplicate status.
5. Run approved AI classification and draft generation only for eligible inputs.
6. Validate AI output against the approved schema and enums.
7. Apply deterministic overrides.
8. Decide storage, task, alert, and manual-review eligibility.

Earlier safety failures take precedence over later actions.

## Core Rules

| ID | Rule | Result | Status |
|---|---|---|---|
| BR-001 | Required input is missing or malformed | Mark invalid; no AI, storage, task, or alert | approved |
| BR-002 | Exact duplicate matches | Update existing ticket and `duplicate_count`; no new task; alert only if escalation state changed | approved |
| BR-003 | Content duplicate matches | Mark `possible_duplicate`, reference candidate, require review, and do not suppress | approved |
| BR-004 | Duplicate status is `unknown` | Fail closed; manual review; no creation effects | approved |
| BR-005 | AI output fails after one retry | Apply approved safe fallback | approved |
| BR-006 | Deterministic and AI results conflict | Deterministic rule wins and conflict is audited | approved |
| BR-007 | Valid new or possible-duplicate ticket passes all gates | Store exactly one DEV ticket | approved |
| BR-008 | Airtable storage fails | Do not create task or customer-escalation alert | approved |
| BR-009 | Ticket is stored and is not an exact duplicate | Create at most one controlled ClickUp task | approved |
| BR-010 | Approved P1/P2 or escalation condition matches | Send at most one controlled Slack alert per escalation state | approved |
| BR-011 | Draft response exists | Store for human review; never automatically send | confirmed constraint |
| BR-012 | Real data, secret, or production destination is detected | Stop processing and report safely | confirmed constraint |

## Classification Rules

The category, priority, and optional sentiment enums are approved.

| Dimension | Proposed responsibility | Required decision |
|---|---|---|
| Category | Gemini suggestion constrained to eight approved values | `other` fallback |
| Priority | Gemini suggestion plus deterministic override | Four approved levels |
| Sentiment | Mock AI suggestion constrained to approved optional enum | Defaults to `unknown`; never independently affects priority or alerts |
| Escalation | Deterministic final decision informed by structured signals | Approved P1/P2 framework |
| Draft response | Gemini prepares review-only text | Never automatically sent |

### Approved Categories

`billing`, `refund`, `account-access`, `technical-support`, `product-question`, `order-delivery`, `feedback-complaint`, `other`

### Approved Priorities

- `p1-critical`: security or account takeover, safety threat, legal threat, or widespread outage.
- `p2-high`: refund or chargeback, explicit urgent request, repeated serious failure, or another approved high-risk condition.
- `p3-normal`: standard support request and the default after AI failure when no deterministic priority rule matches.
- `p4-low`: feedback or non-urgent information request.

AI must not lower a priority assigned by a deterministic rule.

### Approved Sentiment

`positive`, `neutral`, `negative`, `unknown`; default `unknown`. Sentiment alone never changes priority and never triggers a Slack alert.

## Escalation Framework

P1 and P2 tickets, refunds, explicit urgent requests, and approved high-risk conditions are eligible for a controlled Slack alert after successful ticket storage. Sentiment alone and AI failure alone do not create a customer escalation alert.

- Deterministic rules override AI category, priority, and escalation suggestions.
- Refund and chargeback use a minimum priority of `p2-high`.
- P1/P2 tickets require human review.
- An exact duplicate alerts again only when its final escalation state changed.
- Repeated system-level AI failures may use a separate operational alert after that rule and destination are separately approved.

## Duplicate Framework

A message is an exact duplicate only when `source_channel + source_message_id` matches a retained ticket. A content match uses the approved SHA-256 fingerprint of normalized sender reference, subject, and message text within 72 hours and a 30-day lookup. Cross-channel similarity is never an automatic exact duplicate. Production-grade concurrent locking and manual correction are deferred.

## Ticket Identity Rule

Generate `SF-YYYYMMDD-XXXXXXXX`, using the first eight uppercase hexadecimal characters of a UUID v4. Never derive the identifier from personal or customer information.

## Gemini Failure Rule

After one retry:

- `category=other`
- `sentiment=unknown`
- `classification_status=failed`
- `needs_human_review=true`
- `draft_response` is empty
- priority comes only from deterministic rules
- priority defaults to `p3-normal` when no deterministic priority rule matches
- AI failure alone does not create a customer escalation alert

Phase 1 uses mocked structured AI output and makes no Gemini call. Gemini permits one retry only; repeated system-level failures may create an operational record or alert only after separate approval.

## Gemini Usage and Privacy Rules

- Free tier only, maximum 500 calls per review cycle, and no paid or billing-enabled project without separate approval.
- Structured JSON only; dummy or sanitized text only; maximum 5,000 characters.
- Exclude attachment contents, direct personal identifiers, tools, browsing, code execution, and external actions.
- Stop for exhausted free quota, repeated rate limits, 500 calls, unexpected billing, broader access, or real data.

## DEV Reliability Rules

- Run fixture tests sequentially.
- Re-check the ticket ID or dedupe key before every create retry.
- Never blindly retry non-idempotent create actions.
- Read-only Airtable operations use at most two retries with 2-second and 5-second backoff.
- The target Airtable timeout is 15 seconds.
- After an ambiguous Airtable create result, re-check the exact dedupe key before any retry.
- Persistent failure stops downstream processing and records an operational error when storage is available.
- Production-grade locking is deferred.

## Airtable Serialization Rules

- Store `attachment_metadata`, `escalation_reasons`, `validation_errors`, and `rule_ids_applied` as compact valid UTF-8 JSON strings using their documented array or object contracts.
- Reject invalid JSON, code fences, and human-readable pseudo-JSON before storage.
- Store `ai_schema_valid` as blank when Gemini was not called, true when returned output passed validation, and false when returned output failed validation.
- Store priority using only `p1-critical`, `p2-high`, `p3-normal`, or `p4-low`.

## Side-Effect Eligibility

| Effect | Required conditions |
|---|---|
| Airtable ticket | Valid input, identity generated, not an exact duplicate, approved fallback or AI/rules result, approved DEV destination |
| Airtable exact-duplicate update | Exact source identity match and approved DEV destination |
| ClickUp task | Airtable ticket stored, not an exact duplicate, task not already created, approved DEV destination |
| Slack alert | Ticket stored, approved P1/P2 or escalation rule matched, escalation state not already alerted, approved DEV destination |
| Customer reply | Prohibited in current scope |

## Ownership and Change Control

- Rule owner: Mervin until another owner is explicitly named.
- Taxonomy and escalation approver during the portfolio phase: Mervin.
- Changes require documentation, approval, versioning, test updates, and DEV evidence before use.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model|Data Model]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
