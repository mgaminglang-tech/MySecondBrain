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
  - business-rules
  - customer-support
---

# Business Rules

## Status

Rule framework only. Values marked **Not Yet Defined** must not be implemented by guesswork.

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
| BR-001 | Required input is missing or malformed | Mark invalid; no AI, storage, task, or alert | proposed |
| BR-002 | Duplicate status is `duplicate` | Do not create a new ticket or task; return matched reference safely | proposed |
| BR-003 | Duplicate status is `unknown` | Fail closed; manual review; no creation effects | proposed |
| BR-004 | AI output fails schema or enum validation | Manual review; do not trust AI routing | proposed |
| BR-005 | Deterministic and AI results conflict | Deterministic rule wins and conflict is audited | proposed |
| BR-006 | Valid, non-duplicate ticket passes all gates | Store exactly one DEV ticket | proposed |
| BR-007 | Airtable storage fails | Do not create task or alert unless a compensating design is approved | proposed |
| BR-008 | Ticket is stored successfully | Create at most one controlled ClickUp task | proposed |
| BR-009 | Approved escalation condition matches | Send at most one controlled Slack alert | proposed |
| BR-010 | Draft response exists | Store for human review; never automatically send | confirmed constraint |
| BR-011 | Real data, secret, or production destination is detected | Stop processing and report safely | confirmed constraint |

## Classification Rules

Approved enums and definitions are **Not Yet Defined**.

| Dimension | Proposed responsibility | Required decision |
|---|---|---|
| Category | LLM suggestion constrained to approved enum | Categories, definitions, and fallback |
| Priority | LLM suggestion plus deterministic override | Levels, thresholds, and precedence |
| Sentiment | LLM suggestion constrained to approved enum | Values and whether sentiment affects priority |
| Escalation | Deterministic final decision informed by structured signals | Exact signals, thresholds, and owners |
| Draft response | LLM prepares review-only text | Tone, length, policy boundaries, and prohibited claims |

## Escalation Framework

The brief requires alerts for urgent, refund, or high-risk requests. Exact matching rules are Not Yet Defined. Before implementation, each rule must define:

- machine-readable rule ID
- exact phrase, category, amount, severity, or account condition
- whether matching is case-normalized, exact, semantic, or combined
- priority override
- Slack eligibility
- manual-review requirement
- alert owner and safe payload
- conflict behavior and test examples

Potential topics such as threats, fraud, security, safety, legal claims, chargebacks, data deletion, account takeover, or regulated matters are **recommendations for review**, not approved scope or rules.

## Duplicate Framework

A message must not be labeled duplicate until the approved comparison succeeds. Decisions still required:

- source-message exact match
- cross-channel customer identity matching
- normalized subject/body fingerprint
- time window
- reply and thread behavior
- concurrent request locking
- allowed manual merge, reopen, or false-positive correction

## Side-Effect Eligibility

| Effect | Required conditions |
|---|---|
| Airtable ticket | Valid input, identity generated, duplicate=`new`, AI/rules safe, approved DEV destination |
| ClickUp task | Airtable ticket stored, task not already created, approved DEV destination |
| Slack alert | Ticket stored, approved escalation rule matched, alert not already sent, approved DEV destination |
| Customer reply | Prohibited in current scope |

## Ownership and Change Control

- Rule owner: Mervin until another owner is explicitly named.
- Taxonomy approver: Not Yet Defined.
- Escalation approver: Not Yet Defined.
- Changes require documentation, approval, versioning, test updates, and DEV evidence before use.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model|Data Model]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
