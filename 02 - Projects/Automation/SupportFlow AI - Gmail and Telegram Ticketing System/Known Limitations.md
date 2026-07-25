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
  - limitations
---

# Known Limitations

## Status

These are current planning limitations. None is accepted for production, and no implemented behavior is claimed.

## Limitation Register

| ID | Limitation | Impact | Workaround or next action | Owner | Status |
|---|---|---|---|---|---|
| LIM-001 | Workflow is unbuilt and inactive | No runtime capability exists | Complete gates before build | Mervin | open |
| LIM-002 | Source field contracts are undefined | Normalization cannot be implemented safely | Approve sanitized channel examples and mappings | Mervin | open |
| LIM-003 | Duplicate definition and concurrency controls are undefined | Duplicate or missed-ticket risk remains | Approve exact keys, window, replay, and locking rules | Mervin | open |
| LIM-004 | Classification taxonomy is undefined | AI output cannot be validated | Approve enums, definitions, and fallbacks | Mervin | open |
| LIM-005 | Escalation thresholds and owners are undefined | Urgent/refund/high-risk routing is unsafe | Approve deterministic rules and recipients | Mervin | open |
| LIM-006 | LLM provider, model, policy, and fallback are undefined | Privacy, quality, cost, and availability are unknown | Complete provider review | Mervin | open |
| LIM-007 | DEV Airtable, ClickUp, and Slack destinations are undefined | Controlled integration testing is blocked | Approve isolated destinations or mocks | Mervin | open |
| LIM-008 | Retries, timeouts, concurrency, and recovery are undefined | Partial failures may duplicate or lose actions | Approve reliability design | Mervin | open |
| LIM-009 | Volumes, performance targets, retention, and support ownership are undefined | Operational readiness cannot be assessed | Complete non-functional discovery | Mervin | open |
| LIM-010 | Attachments, rich content, edits, replies, and threads are not specified | Some channel messages may be unsupported | Define version-one handling or exclude explicitly | Mervin | open |
| LIM-011 | AI classification is probabilistic | Misclassification remains possible | Schema validation, deterministic overrides, human review | Mervin | open |
| LIM-012 | Automatic replies, closure, deletion, SLA enforcement, and analytics are excluded | Manual operations remain | Retain manual process or approve future phase | Mervin | accepted scope boundary |
| LIM-013 | Testing has not begun | No pass, performance, or reliability claims are valid | Execute approved tests after build | Mervin | not-run |
| LIM-014 | Production is not approved | No live service or production-readiness claim | Separate production discovery and approval | Mervin | blocked |

## Current Safety Boundaries

- Dummy or irreversibly sanitized data only.
- No real customer data, production credentials, or live destinations.
- No automatic customer replies.
- No activation, deployment, closure, deletion, or unapproved external side effects.
- No portfolio screenshots until sanitized evidence exists.

## Future Review Triggers

Review this note whenever:

- a discovery decision is resolved
- scope, taxonomy, rules, or schemas change
- a DEV build or test phase is approved
- an issue is found or a limitation is accepted
- demo or production readiness is considered

## Approval

- Limitation owner: Mervin
- Accepted risks beyond explicit scope boundaries: none
- Review date: Not Yet Defined
- Production acceptance: not approved

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Implementation Plan|Implementation Plan]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
