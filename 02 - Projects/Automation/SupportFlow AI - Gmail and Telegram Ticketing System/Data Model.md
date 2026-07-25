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
  - data-model
---

# Data Model

## Status

Proposed logical model for discovery review. Airtable, ClickUp, Slack, Gmail, Telegram, and LLM field mappings are **Not Yet Defined**.

## Unified Ticket

| Field | Proposed type | Required | Purpose |
|---|---|---|---|
| `ticket_id` | string | yes after validation | Unique internal ticket identifier |
| `source_channel` | enum | yes | `gmail` or `telegram` |
| `source_message_id` | string | yes | Channel message identifier |
| `source_thread_id` | string or null | conditional | Gmail thread or Telegram chat/thread context |
| `received_at` | UTC datetime | yes | Source receipt timestamp |
| `sender_reference` | string | yes | Sanitized or non-sensitive source reference |
| `sender_name` | string or null | no | Sanitized display name |
| `subject` | string or null | conditional | Gmail subject or normalized Telegram summary |
| `message_text` | string | yes | Sanitized support request text |
| `attachment_metadata` | array | no | Safe metadata only; content handling Not Yet Defined |
| `language` | string or null | no | Detected or source-provided language |
| `category` | enum | yes after classification | Approved taxonomy value |
| `priority` | enum | yes after classification | Approved priority value |
| `sentiment` | enum | yes after classification | Approved sentiment value |
| `escalation_required` | boolean | yes after rules | Deterministic final escalation flag |
| `escalation_reasons` | string array | yes | Machine-readable matched reasons |
| `needs_human_review` | boolean | yes | Manual review requirement |
| `draft_response` | string or null | no | Unsent draft for human review |
| `duplicate_status` | enum | yes after lookup | Proposed: `new`, `duplicate`, `unknown` |
| `duplicate_of_ticket_id` | string or null | conditional | Matched existing ticket |
| `status` | enum | yes | Proposed initial value: `new` |
| `assigned_owner` | string or null | no | Assignment owner reference |
| `airtable_record_id` | string or null | after storage | DEV storage reference |
| `clickup_task_id` | string or null | after task creation | Controlled task reference |
| `slack_alert_reference` | string or null | after alert | Controlled alert evidence |
| `created_at` | UTC datetime | yes after creation | Internal creation timestamp |
| `updated_at` | UTC datetime | yes | Last controlled update timestamp |
| `schema_version` | string | yes | Contract version, initially proposed `v0.1.0` |

## Processing Audit

| Field | Proposed type | Purpose |
|---|---|---|
| `processing_status` | enum | Proposed: `accepted`, `invalid`, `duplicate`, `manual_review`, `failed` |
| `validation_errors` | object array | Field, code, and sanitized message |
| `classification_source` | enum | Proposed: `ai`, `rule_override`, `manual`, `not-run` |
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

Exact source paths, HTML handling, quoted-thread removal, bot commands, edits, attachments, and maximum sizes are **Not Yet Defined**.

## Identity and Duplicate Data

The following require approval before implementation:

- Ticket ID format and generator
- Canonical idempotency key
- Exact-match fields
- Normalization applied before matching
- Similarity or fuzzy-match behavior
- Duplicate lookback window
- Treatment of replies, forwarded email, Telegram edits, and reopened issues
- Concurrent-arrival protection
- Manual duplicate override and audit fields

## Data Classification and Retention

- DEV values must be fabricated or irreversibly sanitized.
- Secrets, credential values, and real customer identifiers are prohibited.
- Attachment content is excluded until separately approved.
- Airtable, n8n execution, ClickUp, Slack, and LLM retention periods are Not Yet Defined.
- Screenshots must be sanitized and created only after verified evidence exists.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
- [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]]
