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
  - data-model
---

# Data Model

## Status

Approved logical model for the Phase 1 skeleton and future single Airtable `Tickets` table. Actual external resource IDs and credentials remain deferred.

## Unified Ticket

| Field | Proposed type | Required | Purpose |
|---|---|---|---|
| `ticket_id` | string | yes after validation | `SF-YYYYMMDD-XXXXXXXX` |
| `source_channel` | enum | yes | `gmail` or `telegram` |
| `source_message_id` | string | yes | Channel message identifier |
| `source_thread_id` | string or null | conditional | Gmail thread or Telegram chat/thread context |
| `received_at` | UTC datetime | yes | Source receipt timestamp |
| `sender_reference` | string | yes | Sanitized or non-sensitive source reference |
| `sender_name` | string or null | no | Sanitized display name |
| `subject` | string or null | conditional | Gmail subject or normalized Telegram summary |
| `message_text` | string | yes | Sanitized support request text |
| `attachment_metadata` | array | no | Safe metadata only; contents excluded from v0.1 |
| `language` | string or null | no | Detected or source-provided language |
| `category` | enum | yes after classification | Eight approved taxonomy values |
| `priority` | enum | yes after rules | Four approved priority values |
| `sentiment` | enum | no | Defaults to `unknown` |
| `escalation_required` | boolean | yes after rules | Deterministic final escalation flag |
| `escalation_reasons` | string array | yes | Machine-readable matched reasons |
| `needs_human_review` | boolean | yes | Manual review requirement |
| `draft_response` | string or null | no | Unsent draft for human review |
| `duplicate_status` | enum | yes after lookup | `new`, `exact_duplicate`, `possible_duplicate`, `unknown` |
| `duplicate_of_ticket_id` | string or null | conditional | Matched existing ticket |
| `possible_duplicate_ticket_id` | string or null | conditional | Candidate ticket for human review |
| `duplicate_count` | integer | yes after storage | Count of exact duplicate arrivals |
| `content_fingerprint` | string | yes after validation | Normalized content lookup value |
| `status` | enum | yes | Proposed initial value: `new` |
| `assigned_owner` | string or null | no | Assignment owner reference |
| `airtable_record_id` | string or null | after storage | DEV storage reference |
| `clickup_task_id` | string or null | after task creation | Controlled task reference |
| `slack_alert_reference` | string or null | after alert | Controlled alert evidence |
| `last_alerted_escalation_state` | string or null | after alert | Prevents unchanged duplicate alerts |
| `created_at` | UTC datetime | yes after creation | Internal creation timestamp |
| `updated_at` | UTC datetime | yes | Last controlled update timestamp |
| `schema_version` | string | yes | Contract version, initially proposed `v0.1.0` |

## Processing Audit

| Field | Proposed type | Purpose |
|---|---|---|
| `processing_status` | enum | Proposed: `accepted`, `invalid`, `duplicate`, `manual_review`, `failed` |
| `validation_errors` | object array | Field, code, and sanitized message |
| `classification_source` | enum | `ai`, `rule_override`, `manual`, `not-run` |
| `classification_status` | enum | `succeeded`, `failed`, `not-run` |
| `rule_ids_applied` | string array | Deterministic rule trace |
| `ai_schema_valid` | boolean or null | AI output validation result |
| `error_stage` | string or null | Safe failure location |
| `error_code` | string or null | Machine-readable failure code |
| `execution_reference` | string or null | Sanitized DEV evidence reference |

## Proposed Source Mapping

| Unified field | Gmail source | Telegram source |
|---|---|---|
| `source_channel` | constant `gmail` | constant `telegram` |
| `source_message_id` | Gmail message ID | Telegram update/message ID |
| `source_thread_id` | Gmail thread ID | Telegram chat/thread ID |
| `received_at` | message receipt date | message date |
| `sender_reference` | sanitized sender email/reference | sanitized user/chat reference |
| `sender_name` | sender display name | Telegram display name |
| `subject` | Gmail subject | derived summary or null |
| `message_text` | approved text body selection | message text or approved caption |

Gmail uses the plain-text body or HTML-to-text fallback. Telegram uses message text or caption. `message_text` is limited to 5,000 characters. Attachment metadata may be retained, but attachment contents and edited Telegram messages are excluded from v0.1.

## Approved Enums

- `category`: `billing`, `refund`, `account-access`, `technical-support`, `product-question`, `order-delivery`, `feedback-complaint`, `other`
- `priority`: `p1-critical`, `p2-high`, `p3-normal`, `p4-low`
- `duplicate_status`: `new`, `exact_duplicate`, `possible_duplicate`, `unknown`
- `classification_status`: `succeeded`, `failed`, `not-run`
- `sentiment`: `positive`, `neutral`, `negative`, `unknown`; default `unknown`

## Airtable Tickets Table

The future single `Tickets` table contains the unified ticket fields, processing-audit fields, duplicate counters and references, ClickUp reference, Slack alert state, schema version, and timestamps defined in this note.

- Airtable base name: `DEV - SupportFlow AI`
- Airtable table name: `Tickets`
- Actual base ID, table ID, and credential: Not Yet Assigned

## ClickUp Task Contract

- Name: `[P#] {ticket_id} — {category} — {short subject}`
- Description: sanitized summary, source, Airtable reference, draft response, and escalation reasons
- Custom fields: ticket ID, channel, category, priority, sentiment, escalation, and Airtable record ID
- Initial status: `To Do`
- Initial DEV assignee: Mervin
- SLA-based due date: none in v0.1
- DEV list name: `DEV - SupportFlow AI - Ticket Queue`
- Actual list ID and credential: Not Yet Assigned

## Slack Alert Contract

Include ticket ID, category, priority, sanitized summary limited to 200 characters, escalation reasons, and available Airtable or ClickUp references. Never include credentials, attachment contents, or unredacted client data.

- DEV channel name: `#dev-supportflow-alerts`
- Actual channel ID and credential: Not Yet Assigned

## Identity and Duplicate Data

### Ticket ID

- Format: `SF-YYYYMMDD-XXXXXXXX`
- `XXXXXXXX`: first eight uppercase hexadecimal characters of a UUID v4
- Personal or customer information must never be used

### Content Fingerprint

Normalize sender reference, subject, and message text individually using:

1. Unicode NFKC
2. lowercase
3. remove zero-width characters
4. normalize line endings
5. collapse repeated whitespace
6. trim leading and trailing whitespace

Preserve punctuation, signatures, and quoted text for v0.1. Calculate SHA-256 over the ordered normalized sender reference, subject, and message text.

Approved behavior:

- Exact key: `source_channel + source_message_id`, checked within retained records.
- Content key: normalized `sender_reference + message_text`, checked within 72 hours using a 30-day lookback.
- Exact duplicate updates the existing record and increments `duplicate_count`.
- Content match creates `possible_duplicate`, references the candidate, and requires human review without automatic suppression.

Production-grade concurrent-arrival locking and manual duplicate correction remain deferred.

## Data Classification and Retention

- DEV values must be fabricated or irreversibly sanitized.
- Secrets, credential values, and real customer identifiers are prohibited.
- Attachment content is excluded until separately approved.
- DEV n8n execution data is retained for seven days.
- DEV Airtable records, ClickUp tasks, and Slack test alerts are retained for 30 days.
- OpenAI receives only dummy or sanitized text up to 5,000 characters, without attachment contents or direct identifiers.
- Screenshots must be sanitized and created only after verified evidence exists.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
- [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]]
