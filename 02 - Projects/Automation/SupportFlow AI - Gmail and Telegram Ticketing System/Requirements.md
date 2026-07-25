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
  - requirements
---

# Requirements

## Status

Draft requirements derived from the approved project brief. They are not yet approved for implementation.

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

## Unified Input and Output Contracts

The proposed logical ticket fields are defined in [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model|Data Model]]. Exact required fields, maximum lengths, enum values, identifiers, and storage mappings are **Not Yet Defined** and block implementation approval.

## Integration Requirements

| System | Environment | Purpose | Current state |
|---|---|---|---|
| n8n | DEV | Orchestration | No workflow created; inactive design only |
| Gmail | DEV/test | Controlled message intake | Access and trigger method Not Yet Defined |
| Telegram Bot API | DEV/test | Controlled message intake | Bot and trigger method Not Yet Defined |
| Airtable | DEV/test | Duplicate lookup and ticket storage | Base/table/schema Not Yet Defined |
| Approved LLM | DEV/test | Classification and draft generation | Provider/model/policy Not Yet Defined |
| ClickUp | DEV/test | Controlled task creation | Workspace/list/schema Not Yet Defined |
| Slack | DEV/test | Controlled escalation alert | Channel/payload Not Yet Defined |

Credential names may be documented later by reference only. Secret values must never be stored in the vault or Git.

## Error and Exception Requirements

- Invalid input: return validation errors; do not check AI, store, create a task, or alert.
- Duplicate: record or return the matched duplicate reference safely; do not create a second ticket or task.
- AI failure: retry only under an approved bounded policy; otherwise mark manual review and prevent unsafe escalation decisions.
- Airtable lookup uncertainty: fail closed for downstream creation until duplicate status is known.
- Storage failure: do not create a ClickUp task or Slack alert unless an approved compensating design exists.
- ClickUp or Slack failure: preserve ticket context, prevent uncontrolled retries, and expose the failure for manual recovery.
- Empty input: produce a controlled invalid result with no side effects.

## Non-Functional Requirements

- Security: least privilege, credential references only, no secrets in documentation or source control.
- Privacy: dummy or irreversibly sanitized DEV data only.
- Auditability: deterministic rule results and execution evidence must be traceable without sensitive payloads.
- Idempotency: duplicate and replay behavior must be defined before side-effect testing.
- Reliability: retries, timeouts, concurrency, partial-failure handling, and replay controls are Not Yet Defined.
- Performance, volume, availability, retention, recovery, and support targets: Not Yet Defined.

## Acceptance Criteria

- [ ] All open input and output contracts are approved.
- [ ] Both channels pass equivalent-normalization tests.
- [ ] Invalid and incomplete cases fail safely.
- [ ] Ticket identity and duplicate behavior pass deterministic tests.
- [ ] AI results conform to the approved schema and deterministic overrides.
- [ ] Drafts are never sent automatically.
- [ ] Controlled Airtable, ClickUp, and Slack effects match exact expectations.
- [ ] Every required test has evidence and an allowed status.
- [ ] The workflow remains inactive and uses no real customer data or production credentials.

## Approval

- Requirements approver: Mervin
- Approval status: Not Yet Defined
- Approval date: Not Yet Defined
- DEV build authorization: not approved

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model|Data Model]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
