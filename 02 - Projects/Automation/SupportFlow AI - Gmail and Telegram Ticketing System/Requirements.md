---
type: project-note
status: in-progress
phase: phase-2-credential-gates
client: internal-demo
owner: Mervin
created: 2026-07-25
updated: 2026-07-27
tags:
  - client-automation
  - requirements
---

# Requirements

## Status

Requirements are approved and validated for the credential-free Phase 1 skeleton. The completed Phase 1 authorization does not authorize further workflow modification, credentials, additional execution, integration, or external side effects.

## Phase 1 Requirement Boundary

Phase 1 includes only Manual Trigger, dummy Gmail and Telegram payloads, channel normalization, unified ticket formatting, strict validation, ticket-ID and content-fingerprint generation, mocked duplicate results, mocked AI classification and draft response, deterministic business rules, and final structured output.

Phase 1 excludes all live triggers, service connections, credentials, external side effects, real data, activation, and production claims.

## Functional Requirements

| ID | Requirement | Priority | Acceptance criterion |
|---|---|---|---|
| FR-001 | Accept controlled Gmail test messages | must | Approved Gmail fixture enters the Gmail branch without live customer data |
| FR-002 | Accept controlled Telegram test messages | must | Approved Telegram fixture enters the Telegram branch without live customer data |
| FR-003 | Normalize both channels | must | Equivalent inputs produce the same approved unified ticket structure |
| FR-004 | Validate required fields and formats | must | Invalid input returns machine-readable errors and no downstream side effects |
| FR-005 | Generate a unique ticket ID | must | Each valid new request has one ID matching the approved format |
| FR-006 | Detect duplicates in Airtable | must | Approved duplicate cases create no second ticket or task |
| FR-007 | Classify with an approved LLM | must | Output matches approved category, priority, sentiment, and escalation enums |
| FR-008 | Generate a draft response | must | Draft is stored for review and never sent automatically |
| FR-009 | Validate AI output | must | Malformed or disallowed output routes to manual review without unsafe actions |
| FR-010 | Apply deterministic business rules | must | Approved overrides take precedence over AI suggestions |
| FR-011 | Store valid new tickets in Airtable | must | One approved DEV record matches the ticket schema |
| FR-012 | Create ClickUp tasks conditionally | must | One controlled task is created only for a valid, non-duplicate ticket |
| FR-013 | Send Slack escalation alerts conditionally | must | One controlled alert is sent only when an approved escalation rule matches |
| FR-014 | Preserve audit context | must | Result records rule decisions, statuses, timestamps, and safe error context |
| FR-015 | Handle partial dependency failures | must | Failure is visible, recoverable, and does not silently repeat side effects |
| FR-016 | Keep customer communication manual | must | No node or path sends a Gmail or Telegram customer reply |
| FR-017 | Keep DEV inactive | must | Saved workflow remains inactive before and after approved testing |

## Approved Input Contracts

| Source | Allowed input fields |
|---|---|
| Gmail | `message_id`, `thread_id`, `received_at`, sanitized `sender_reference`, sanitized `sender_name`, `subject`, plain-text body, attachment metadata |
| Telegram | `update_id`, `message_id`, `chat_id`, `received_at`, sanitized `sender_reference`, sanitized `sender_name`, text or caption, `reply_to_message_id`, attachment metadata |

- Gmail HTML may be converted to text only when a plain-text body is unavailable.
- `message_text` is trimmed and limited to 5,000 characters.
- Attachment contents and edited Telegram messages are excluded from schema `0.1.0`.
- Required unified fields are `source_channel`, `source_message_id`, `received_at`, `sender_reference`, and non-empty `message_text`.
- `source_channel` must be `gmail` or `telegram`; identifiers must be non-empty; `received_at` must be a valid UTC datetime; `subject` is optional and limited to 250 characters.
- Invalid input fails closed before duplicate lookup, AI, storage, task creation, or alerts.

The complete approved logical model is in [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model|Data Model]].

## Ticket Identity and Fingerprint

- Ticket ID format: `SF-YYYYMMDD-XXXXXXXX`.
- `XXXXXXXX` is the first eight uppercase hexadecimal characters of a UUID v4.
- No ticket-ID component derives from personal or customer information.
- Before any create retry, re-check the ticket ID or applicable dedupe key.
- Content normalization applies Unicode NFKC, lowercase, zero-width-character removal, line-ending normalization, repeated-whitespace collapse, and leading/trailing whitespace trimming.
- Punctuation, signatures, and quoted text are preserved in schema `0.1.0`.
- The fingerprint input is `normalized_sender_reference + "\u001F" + normalized_subject + "\u001F" + normalized_message_text`.
- `\u001F` is the literal Unicode Unit Separator used between components; an absent subject normalizes to an empty string but both separators remain.
- The fingerprint is SHA-256 of that exact combined value.

## Approved Duplicate Requirements

- Exact duplicate key: `source_channel + source_message_id`, checked within retained Airtable records.
- Content fingerprint: normalized sender reference, subject, and message text joined with `\u001F`, checked within 72 hours using a 30-day Airtable lookback.
- Exact duplicate: update the existing ticket record and increment `duplicate_count`; do not create another ClickUp task; do not send another Slack alert unless the final escalation state changes.
- Content duplicate: create the request as `possible_duplicate`, store the candidate ticket reference, require human review, and do not suppress it automatically.
- Cross-channel similarity may create `possible_duplicate` only; it may not automatically establish an exact duplicate.
- Duplicate lookup uncertainty fails closed for downstream creation.

## Approved Airtable Physical-Storage Requirements

- The `priority` select must use exactly `p1-critical`, `p2-high`, `p3-normal`, and `p4-low`.
- `attachment_metadata`, `escalation_reasons`, `validation_errors`, and `rule_ids_applied` must be stored as compact valid UTF-8 JSON using the array or object structure defined in the data model.
- Invalid JSON, code fences, and human-readable pseudo-JSON are prohibited.
- `ai_schema_valid` is blank when Gemini was not called, true when returned output passed schema validation, and false when returned output failed schema validation.
- Read-only Airtable operations allow at most two retries with 2-second and 5-second backoff and a target timeout of 15 seconds.
- Airtable create operations must never be retried blindly. After an ambiguous create result, re-check the exact dedupe key before any retry.
- Persistent Airtable failure stops downstream processing.

## Approved Classification Requirements

- Categories: `billing`, `refund`, `account-access`, `technical-support`, `product-question`, `order-delivery`, `feedback-complaint`, `other`.
- Priorities: `p1-critical`, `p2-high`, `p3-normal`, `p4-low`.
- Sentiment is optional: `positive`, `neutral`, `negative`, or `unknown`; default `unknown`.
- Sentiment never independently changes priority or triggers Slack alerts.
- Deterministic business rules override AI classifications.
- Google Gemini is the controlled DEV provider for a later phase; OpenAI is no longer approved. Phase 1 uses mocked structured classification output.
- The approved future model is `models/gemini-3.1-flash-lite`. Exact structured-output node settings will be configured only when the Gemini workflow node is separately authorized and built.
- Gemini input is structured JSON only and limited to dummy or sanitized text of at most 5,000 characters without attachment contents or direct personal identifiers.
- Gemini tools, browsing, code execution, external actions, and paid usage are prohibited.
- Draft responses remain review-only and are never sent automatically.

## Integration Requirements

| System | Environment | Purpose | Current state |
|---|---|---|---|
| n8n | DEV | Credential-free Phase 1 orchestration | Workflow `cyiCqsjLQdB7apjP` built and inactive |
| Gmail | DEV/test | Read-only controlled message intake from a dedicated DEV mailbox | Mailbox, label/filter, trigger configuration, IDs, and credential Not Yet Assigned |
| Telegram Bot API | DEV/test | New-message intake from a dedicated DEV bot and one private DEV chat | Bot/chat identities, trigger configuration, IDs, and credential Not Yet Assigned |
| Airtable | DEV/test | Base `DEV - SupportFlow AI` (`appell78p9BIEek9J`), table `Tickets` (`tblI3JYon6kLqZPbP`), primary `ticket_id` | Manifest and storage/retry decisions approved; zero records; physical priority-choice rename and credential approval remain pending |
| Google Gemini | DEV/test | Free-tier structured classification and draft generation after Phase 1 | Credential `AI TASK`; `Google Gemini(PaLM) API` / `googlePalmApi`; connection test passed; future model `models/gemini-3.1-flash-lite`; no API calls made and no workflow node configured |
| ClickUp | DEV/test | Workspace `90161719575`; Space `90167621384`; Folder `901610630678`; List `DEV - SupportFlow AI - Ticket Queue` (`901616152035`); assignee Mervin | Read-only audit `7126` passed; List active, seven-field manifest verified, zero tasks, zero writes/notifications; fixture-test gate next |
| Slack | DEV/test | Channel `#dev-supportflow-alerts` | Actual ID and credential Not Yet Assigned |

Credential names may be documented later by reference only. Secret values must never be stored in the vault or Git.

The Gemini credential's API key and secrets remain only in the approved n8n credential store and are not recorded in these requirements. The completed connection test does not authorize Gemini calls, real data, workflow activation, or production use.

## Error and Exception Requirements

- Invalid input: return validation errors; do not check AI, store, create a task, or alert.
- Exact duplicate: update the existing ticket and duplicate count; suppress a new task and suppress a repeat Slack alert unless escalation state changed.
- Content duplicate: mark `possible_duplicate`, reference the candidate, require human review, and continue as a separate ticket.
- Gemini failure, timeout, or invalid structured output: allow one retry, then set `category=other`, `sentiment=unknown`, `classification_status=failed`, `needs_human_review=true`, and an empty `draft_response`. Priority comes from deterministic rules; default to `p3-normal` when none matches.
- AI failure alone never creates a customer escalation alert. Repeated system-level AI failures may create a separate operational alert under a later approved operational-alert rule.
- Airtable lookup uncertainty: fail closed for downstream creation until duplicate status is known.
- Storage failure: do not create a ClickUp task or Slack alert unless an approved compensating design exists.
- ClickUp or Slack failure: preserve ticket context, prevent uncontrolled retries, and expose the failure for manual recovery.
- Empty input: produce a controlled invalid result with no side effects.

## Non-Functional Requirements

- Security: least privilege, credential references only, no secrets in documentation or source control.
- Privacy: dummy or irreversibly sanitized DEV data only.
- Auditability: deterministic rule results and execution evidence must be traceable without sensitive payloads.
- Idempotency: duplicate and replay behavior must be defined before side-effect testing.
- Reliability: DEV fixture tests run sequentially. Read-only API calls may retry at most twice with 2-second and 5-second backoff. Default API timeout is 15 seconds.
- Idempotency: never blindly retry non-idempotent create actions; re-check the ticket ID or dedupe key before every create retry.
- Failure behavior: persistent failure stops downstream processing and records an operational error when storage is available.
- Locking: production-grade locking is deferred.
- Capacity: 100 tickets per day and a peak of 10 messages per five minutes.
- Retention: seven days for DEV execution data and 30 days for DEV Airtable records, ClickUp tasks, and Slack test alerts.
- Recovery: RTO four hours, RPO 24 hours, preserved validated workflow exports, and manual replay using source-message identity.
- Usage limits per review cycle: maximum 500 Gemini calls, 100 created Airtable records, 100 created ClickUp tasks, and 30 Slack alerts.
- Gemini budget: free tier only; paid usage and billing-enabled projects require separate approval.
- Stop conditions: free quota exhaustion, repeated rate-limit failure, 500 Gemini calls, unexpected billing, real data, unexpected resource access, broader permissions, out-of-bound external actions, or failed idempotency.
- Ownership: Mervin owns portfolio-phase scope, taxonomy, escalation, testing, recovery, and approval.

## Approved Telegram Mapping

| Telegram field | Unified field |
|---|---|
| `update_id` | `source_event_id` |
| `message_id` | `source_message_id` |
| `chat_id` | `source_conversation_id` |
| `reply_to_message_id` | `source_parent_message_id`; null when absent |
| sanitized sender reference | `sender_reference` |
| received message timestamp | `received_at` |
| message text or caption | `message_text` |

## Acceptance Criteria

- [x] All Phase 1 input and output contracts are approved.
- [x] Both Phase 1 channel fixtures pass the unified normalization contract.
- [x] The authorized invalid fixture fails safely.
- [x] Phase 1 ticket identity and mocked duplicate behavior pass deterministic tests.
- [x] Mocked AI results conform to the approved Phase 1 schema and deterministic overrides.
- [x] Drafts are never sent automatically.
- [ ] Controlled Airtable, ClickUp, and Slack effects match exact expectations.
- [ ] Every required test has evidence and an allowed status.
- [x] The workflow remains inactive and uses no real customer data or production credentials.
- [x] Phase 1 contains no integration node, credential reference, external connection, or side effect.
- [x] Phase 1 validates the six seed fixtures `SF-FX-001` through `SF-FX-006`.

## Approval

- Requirements approver: Mervin
- Approval status: approved for Phase 1 boundary
- Approval date: 2026-07-25
- DEV build authorization: approved and completed for Phase 1 only on 2026-07-25

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model|Data Model]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
