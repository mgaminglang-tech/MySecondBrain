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
| `source_event_id` | string or null | conditional | Source event/update identifier; Telegram `update_id` |
| `source_message_id` | string | yes | Channel message identifier |
| `source_conversation_id` | string or null | conditional | Gmail thread ID or Telegram chat ID |
| `source_parent_message_id` | string or null | no | Telegram reply-to message ID; null when absent |
| `received_at` | UTC datetime | yes | Source receipt timestamp |
| `sender_reference` | string | yes | Sanitized or non-sensitive source reference |
| `sender_name` | string or null | no | Sanitized display name |
| `subject` | string or null | conditional | Gmail subject or normalized Telegram summary |
| `message_text` | string | yes | Sanitized support request text |
| `attachment_metadata` | array | no | Safe metadata only; contents excluded from schema `0.1.0` |
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
| `schema_version` | string | yes | Exact contract version `0.1.0` |

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
| `source_event_id` | null unless an approved Gmail event identifier is available | Telegram `update_id` |
| `source_message_id` | Gmail message ID | Telegram `message_id` |
| `source_conversation_id` | Gmail thread ID | Telegram `chat_id` |
| `source_parent_message_id` | null | Telegram `reply_to_message_id`, otherwise null |
| `received_at` | message receipt date | message date |
| `sender_reference` | sanitized sender email/reference | sanitized user/chat reference |
| `sender_name` | sender display name | Telegram display name |
| `subject` | Gmail subject | derived summary or null |
| `message_text` | approved text body selection | message text or approved caption |

Gmail uses the plain-text body or HTML-to-text fallback. Telegram uses message text or caption. `message_text` is limited to 5,000 characters. Attachment metadata may be retained, but attachment contents and edited Telegram messages are excluded from schema `0.1.0`.

## Approved Enums

- `category`: `billing`, `refund`, `account-access`, `technical-support`, `product-question`, `order-delivery`, `feedback-complaint`, `other`
- `priority`: `p1-critical`, `p2-high`, `p3-normal`, `p4-low`
- `duplicate_status`: `new`, `exact_duplicate`, `possible_duplicate`, `unknown`
- `classification_status`: `succeeded`, `failed`, `not-run`
- `sentiment`: `positive`, `neutral`, `negative`, `unknown`; default `unknown`

## Airtable Tickets Table

The future single `Tickets` table contains the unified ticket fields, processing-audit fields, duplicate counters and references, ClickUp reference, Slack alert state, schema version, and timestamps defined in this note.

- Airtable base name: `DEV - SupportFlow AI`
- Airtable base ID: `appell78p9BIEek9J`
- Airtable table name: `Tickets`
- Airtable table ID: `tblI3JYon6kLqZPbP`
- Primary field: `ticket_id` (`fldFnVtL1BHIjowt4`)
- Date-time display timezone: `Asia/Manila`
- Record count at read-only verification on 2026-07-25: `0`
- n8n credential and connection: not created or connected

### Verified Physical Schema Manifest

| Field | Field ID | Airtable type | Physical detail |
|---|---|---|---|
| `ticket_id` | `fldFnVtL1BHIjowt4` | `singleLineText` | Primary field |
| `source_channel` | `fldsyGUjfyZivagKD` | `singleSelect` | `gmail`, `telegram` |
| `source_event_id` | `fldIu0ED7tnkIsHn0` | `singleLineText` | Nullable by contract |
| `source_message_id` | `fldbIRkPNzOJHD1Bh` | `singleLineText` | Exact-duplicate key component |
| `source_conversation_id` | `fldq3M5wW1gSPffy5` | `singleLineText` | Nullable by contract |
| `source_parent_message_id` | `flde46s1rjljMnxjS` | `singleLineText` | Nullable by contract |
| `received_at` | `fldCU5IBS1N2hYqIs` | `dateTime` | ISO date, 24-hour time, `Asia/Manila` |
| `sender_reference` | `fldzWmerJ8B4FILfV` | `singleLineText` | Sanitized only |
| `sender_name` | `fldgv5vVZp4fZ7fGk` | `singleLineText` | Sanitized only |
| `subject` | `fldWfaKYhCJNS6hBv` | `singleLineText` | Nullable by contract |
| `message_text` | `fldPVMsqB1FkvfHrF` | `multilineText` | Sanitized, maximum 5,000 characters |
| `attachment_metadata` | `fldM2ys6sjyNS8tpM` | `multilineText` | Compact UTF-8 JSON array; metadata only, no contents |
| `language` | `fldsEXXXp4zr36BRA` | `singleLineText` | Nullable by contract |
| `category` | `flda5FwIryWnyN4yk` | `singleSelect` | Eight approved values |
| `priority` | `fld11BIrZeyF3CBen` | `singleSelect` | Must use exactly `p1-critical`, `p2-high`, `p3-normal`, `p4-low`; physical rename pending |
| `sentiment` | `fldSR4ocVQmDQ7ja0` | `singleSelect` | Four approved values |
| `escalation_required` | `fld2CPiYhKt3KoQCO` | `checkbox` | Boolean |
| `escalation_reasons` | `fldQlKf4JNc8wKYTd` | `multilineText` | Compact UTF-8 JSON string array |
| `needs_human_review` | `fldt7kVLwY1VaLjgU` | `checkbox` | Boolean |
| `draft_response` | `fldl8GTmVOe9UIDrS` | `multilineText` | Unsent review draft |
| `duplicate_status` | `fldzPQVIBm24DuQHT` | `singleLineText` | Approved enum enforced upstream |
| `duplicate_of_ticket_id` | `flddOlHPK1PJEdrtW` | `singleLineText` | Nullable by contract |
| `possible_duplicate_ticket_id` | `fldtxEjf8dzqV0fVp` | `singleLineText` | Nullable by contract |
| `duplicate_count` | `fldWD6QWiXbraQZUe` | `number` | Precision `0` |
| `content_fingerprint` | `fldLCa3pM9EpakCzk` | `singleLineText` | SHA-256 hexadecimal |
| `status` | `fldhZeI8Ra21tXTg7` | `singleLineText` | Approved value enforced upstream |
| `assigned_owner` | `fldSNKm8G8OXgKAkx` | `singleLineText` | Nullable by contract |
| `airtable_record_id` | `fldvjYYL7uY4DXtZY` | `singleLineText` | Post-create reference |
| `clickup_task_id` | `fldzp2vca6Pwa85g0` | `singleLineText` | Nullable until task creation |
| `slack_alert_reference` | `fldL3UaDmKnBJ1AKy` | `singleLineText` | Nullable until alert |
| `last_alerted_escalation_state` | `fldsomrPDAuhvMPZG` | `singleLineText` | Idempotency state |
| `created_at` | `fldM8blRggq0HVqNw` | `dateTime` | ISO date, 24-hour time, `Asia/Manila` |
| `updated_at` | `fldkEKhRhNtraJLMt` | `dateTime` | ISO date, 24-hour time, `Asia/Manila` |
| `schema_version` | `fldoP2o6cvvzOFUYB` | `singleLineText` | Must equal `0.1.0` |
| `processing_status` | `fldyYrNnw6SJpHLCy` | `singleLineText` | Approved enum enforced upstream |
| `validation_errors` | `fldR691T188Kz8pbl` | `multilineText` | Compact UTF-8 JSON object array |
| `classification_source` | `fldsDzWOaNWHJWePc` | `singleLineText` | Approved enum enforced upstream |
| `classification_status` | `fldAq39dXnfOByMLx` | `singleLineText` | Approved enum enforced upstream |
| `rule_ids_applied` | `fldXF2KaDiqJJh48U` | `multilineText` | Compact UTF-8 JSON string array |
| `ai_schema_valid` | `fldrcPnOy6UO0XQPK` | `checkbox` | Blank when Gemini was not called; true when valid; false when returned output failed validation |
| `error_stage` | `fldwo41ogAApStPUe` | `singleLineText` | Nullable by contract |
| `error_code` | `fldDHpDpwxhMNBezU` | `singleLineText` | Nullable by contract |
| `execution_reference` | `fldR5BQqrJiyd7edw` | `singleLineText` | Sanitized DEV reference |

### Verified Select Choices

| Field | Choice name | Choice ID | Compatibility |
|---|---|---|---|
| `source_channel` | `gmail` | `seleHwpxMKwJr827G` | compatible |
| `source_channel` | `telegram` | `selOcCjAhrd5gyRP4` | compatible |
| `category` | `billing` | `selKogpr1B8xY233Z` | compatible |
| `category` | `refund` | `selGt770a3xF6hciO` | compatible |
| `category` | `account-access` | `selOxkUhcPcnUXEvo` | compatible |
| `category` | `technical-support` | `selmotyScpA88ZjXn` | compatible |
| `category` | `product-question` | `selRyNfoX8C2bvvr0` | compatible |
| `category` | `order-delivery` | `selCgga36V18j7NED` | compatible |
| `category` | `feedback-complaint` | `selikqrSzs7nVCnOk` | compatible |
| `category` | `other` | `selBjtXyCquGSZuaA` | compatible |
| `priority` | `P1 critical` | `selECyozwdBejuU6t` | approved rename required: `p1-critical` |
| `priority` | `P2 high` | `sel3c1zGWeXB3pEc6` | approved rename required: `p2-high` |
| `priority` | `P3 normal` | `selPFIfsNeGjvs5I9` | approved rename required: `p3-normal` |
| `priority` | `P4 low` | `selP7wsoKe2bnplkn` | approved rename required: `p4-low` |
| `sentiment` | `positive` | `selvjDG5hK4e6RYs1` | compatible |
| `sentiment` | `neutral` | `selD496UG1Ml7EqXX` | compatible |
| `sentiment` | `negative` | `selZnRxpXx0cxK68K` | compatible |
| `sentiment` | `unknown` | `selsHwYE0UKZlGEjT` | compatible |

The JSON, nullable-AI-validation, and retry decisions are approved. Credential creation remains blocked until the four physical priority choices are renamed and verified. No field type change is approved or required.

### Approved Airtable Storage Conventions

- `attachment_metadata`: compact valid UTF-8 JSON array containing metadata objects only.
- `escalation_reasons`: compact valid UTF-8 JSON string array.
- `validation_errors`: compact valid UTF-8 JSON array of objects matching the documented validation-error contract.
- `rule_ids_applied`: compact valid UTF-8 JSON string array.
- Reject invalid JSON, code fences, and human-readable pseudo-JSON before any record write.
- `ai_schema_valid` is blank or omitted when Gemini was not called, true when returned output passed schema validation, and false when returned output failed schema validation.
- `classification_status` and `classification_source` remain the authoritative context for distinguishing a not-run Gemini stage from a failed validation stage.

## ClickUp Task Contract

- Name: `[P#] {ticket_id} — {category} — {short subject}`
- Description: sanitized summary, source, Airtable reference, draft response, and escalation reasons
- Custom fields: ticket ID, channel, category, priority, sentiment, escalation, and Airtable record ID
- Initial status: `To Do`
- Initial DEV assignee: Mervin
- SLA-based due date: none in schema `0.1.0`
- Workspace ID: `90161719575`
- Space: `Team Space` (`90167621384`)
- Folder: `Support Operations - Automation` (`901610630678`)
- DEV list name: `DEV - SupportFlow AI - Ticket Queue`
- DEV list ID: `901616152035`
- List archived: false
- Statuses: `to do`, `in progress`, `complete`
- Existing task count at read-only audit execution `7126`: `0`

### Verified ClickUp Physical Manifest

All fields apply to List `901616152035`. The manifest was returned by audit workflow `6yZO7DfXRD8yjsp9`, execution `7126`.

| Field name | Field ID | Type | Applicability | Dropdown labels and option IDs |
|---|---|---|---|---|
| `ticket ID` | `01a40e6a-d8b4-459e-a257-545d729fa822` | `short_text` | List `901616152035` | none |
| `Airtable record ID` | `1012c6b8-7f46-4804-99a4-0b9867c04414` | `short_text` | List `901616152035` | none |
| `priority` | `63020409-fde3-4bb1-89ac-f640b90b359e` | `drop_down` | List `901616152035` | `p1-critical` → `7980a022-a8a1-47b3-aa5b-f74e7bd6b63a`; `p2-high` → `f5cc3e9b-a5f9-4ee0-ba3a-9d1ae789a393`; `p3-normal` → `e4b2b998-a8a4-4356-8469-9fe8dda8f5b9`; `p4-low` → `9b95686e-5f10-4f88-80f6-6ffdab3b6206` |
| `escalation` | `67a1f273-f363-46e6-a526-0df2b83c4221` | `drop_down` | List `901616152035` | `none` → `df9b0966-49bc-498b-8401-a0a9986be2f8`; `human_review` → `b2c2faae-2274-4a90-ab5f-c6dc9e73e6dc`; `urgent` → `30609205-6583-41f6-beca-a21d4d04d0d4`; `security` → `7d927b59-79ca-4990-bbea-d74941aa3854`; `billing` → `f8c96292-f558-4f79-a89e-8a368496d0f9` |
| `sentiment` | `6e788e25-f164-468f-b720-d35140fa6dad` | `drop_down` | List `901616152035` | `positive` → `55d9113f-d980-40c7-82c2-1adedf4f00a1`; `neutral` → `8cc8b1e6-f28d-46db-8433-540a32a6bd3a`; `negative` → `a8414f7d-7eec-4489-94de-6e4940ddd71a`; `unknown` → `b4619c72-677a-4a17-a944-a706fe7747f8` |
| `channel` | `962d5211-b361-4109-b7be-fcd2aad31b43` | `drop_down` | List `901616152035` | `gmail` → `d59d6a42-5eb4-4739-a030-75fadb06a844`; `telegram` → `62e75c6d-ea38-4a77-8cee-020875204033`; `other` → `9b89fabf-27d9-47bc-9a1f-4fc35072fa70` |
| `category` | `c9ae68bc-98db-42b6-82d4-17857294a013` | `drop_down` | List `901616152035` | `billing` → `ac7e60f5-9529-478d-b586-5f21691a152e`; `technical` → `aa5e04b7-dbcb-4841-b983-24c97499c74f`; `feature_request` → `dbd65fe5-832f-4008-9dde-abf47f0f2ce1`; `general` → `eae7d080-6a00-4c59-9e3d-04466103feca`; `other` → `ecabfb42-e043-4fd0-b0af-0a0fe72f6e1e` |

The read-only audit workflow remained inactive and unpublished. It made zero writes, sent zero notifications, and did not attach the ClickUp credential to SupportFlow workflow `cyiCqsjLQdB7apjP`. ClickUp task creation and update behavior remain not-run.

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

Preserve punctuation, signatures, and quoted text for schema `0.1.0`. Join the normalized values as:

```text
normalized_sender_reference + "\u001F" + normalized_subject + "\u001F" + normalized_message_text
```

`\u001F` is the literal Unicode Unit Separator. If subject is absent, its normalized value is an empty string and both separators remain. Calculate SHA-256 over this exact combined value.

Approved behavior:

- Exact key: `source_channel + source_message_id`, checked within retained records.
- Content key: the approved three-component fingerprint, checked within 72 hours using a 30-day lookback.
- Exact duplicate updates the existing record and increments `duplicate_count`.
- Content match creates `possible_duplicate`, references the candidate, and requires human review without automatic suppression.

Production-grade concurrent-arrival locking and manual duplicate correction remain deferred.

## Data Classification and Retention

- DEV values must be fabricated or irreversibly sanitized.
- Secrets, credential values, and real customer identifiers are prohibited.
- Attachment content is excluded until separately approved.
- DEV n8n execution data is retained for seven days.
- DEV Airtable records, ClickUp tasks, and Slack test alerts are retained for 30 days.
- Gemini receives only dummy or sanitized structured JSON text up to 5,000 characters, without attachment contents or direct identifiers.
- Gemini tools, browsing, code execution, external actions, paid usage, and unapproved training use are prohibited.
- Screenshots must be sanitized and created only after verified evidence exists.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
- [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]]
