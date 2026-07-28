---
type: project-note
status: in-progress
phase: phase-2-controlled-dev-integration
client: internal-demo
owner: Mervin
created: 2026-07-25
updated: 2026-07-28
tags:
  - client-automation
  - limitations
---

# Known Limitations

## Status

These are current limitations after the Phase 1 credential-free skeleton build. None is accepted for production, and no integration behavior is claimed.

## Limitation Register

| ID | Limitation | Impact | Workaround or next action | Owner | Status |
|---|---|---|---|---|---|
| LIM-001 | Workflow is built but intentionally inactive | No live intake or continuous runtime exists | Keep inactive until a separately approved future phase | Mervin | accepted Phase 1 boundary |
| LIM-002 | Six dummy fixture paths are verified; real Gmail and Telegram payloads are not | Live mappings remain unverified | Validate only after separate integration authorization | Mervin | deferred |
| LIM-003 | Fingerprint normalization is approved; production-grade locking is deferred | Concurrent integration arrivals are not protected | Phase 1 runs fixtures sequentially | Mervin | deferred |
| LIM-004 | Optional sentiment enum is approved | Sentiment quality is unverified | Default to `unknown`; never use alone for priority or alerts | Mervin | not-run |
| LIM-005 | Refund and default deterministic paths passed; full P1/P2/P3/P4 rule coverage is incomplete | Untested rules may still be incorrect | Complete the 30-fixture integration suite before integration claims | Mervin | partially tested |
| LIM-006 | Gemini credential `AI TASK` passed its connection test and `models/gemini-3.1-flash-lite` is approved, but the Gemini workflow node is not built | No classification or draft-generation integration is implemented or tested | Keep Gemini mocked until a separate node-build and API-call test authorization | Mervin | credential stage complete; integration not-run |
| LIM-007 | Airtable IDs, the Gemini credential stage, and the ClickUp read-only credential audit are complete; Gmail, Telegram, and Slack resources or credentials remain unresolved | External integration remains incomplete | Resolve each remaining service gate separately; ClickUp task writes remain gated | Mervin | partially resolved |
| LIM-008 | DEV retries and timeout are approved; production reliability remains deferred | Not production-ready | Keep Phase 1 credential-free and inactive | Mervin | deferred |
| LIM-009 | Capacity, retention, recovery, replay, and ownership are approved but untested | Operational claims cannot be made | Verify after authorized build | Mervin | not-run |
| LIM-010 | Attachment contents and edited Telegram messages are excluded from schema `0.1.0` | Some requests require manual handling | Disclose exclusion and test metadata-only path | Mervin | accepted scope boundary |
| LIM-011 | AI classification is probabilistic | Misclassification remains possible | Schema validation, deterministic overrides, human review | Mervin | open |
| LIM-012 | Automatic replies, closure, deletion, SLA enforcement, and analytics are excluded | Manual operations remain | Retain manual process or approve future phase | Mervin | accepted scope boundary |
| LIM-013 | Six Phase 1 fixtures passed, but integration, performance, retention, and recovery testing have not begun | Only skeleton behavior is evidenced | Define fixtures 007–030 and obtain separate integration-test authorization | Mervin | deferred |
| LIM-014 | Production is not approved | No live service or production-readiness claim | Separate production discovery and approval | Mervin | blocked |
| LIM-015 | UUID v4 suffix is limited to eight hexadecimal characters | Collision remains theoretically possible | Re-check ticket ID before any later create action | Mervin | accepted for DEV |
| LIM-016 | All 30 fixtures are defined, but only six seed scenarios have execution evidence | Integration testing cannot begin without separate execution authorization and credentials | Run only an explicitly approved batch later | Mervin | deferred |
| LIM-017 | Dedicated Gmail mailbox and Telegram bot/chat remain Not Yet Assigned; the Gemini credential's underlying project identifier is not recorded in the vault | Remaining service connections are blocked or intentionally undocumented | Assign exact non-secret DEV resource identifiers only when their gates begin; never record secrets | Mervin | partially resolved |
| LIM-018 | Gemini model availability, free-tier limits, and n8n structured-output behavior may change | The approved model still requires node-level configuration and controlled validation | Configure `models/gemini-3.1-flash-lite` only during an authorized Gemini node-build phase and validate within the approved free-tier boundary | Mervin | model approved; integration not-run |
| LIM-019 | The former schema `0.1`, legacy source fields, and JSON-array fingerprint mismatch was corrected | No remaining schema-alignment blocker for a repeated Airtable credential gate | Preserve executions `7113`–`7118` as evidence; do not infer integration readiness | Mervin | resolved for gate repeat |
| LIM-020 | Gemini free-tier content may be used to improve provider products | Use remains unsuitable for real or unsanitized customer data | Mervin accepts free-tier processing for sanitized dummy DEV fixtures only; keep Gemini mocked until separately approved | Mervin | accepted limited DEV boundary |
| LIM-021 | Telegram Trigger 1.3 registers a webhook and drops pending updates | Testing or activation mutates Telegram state and may discard queued dummy updates | Require separate webhook-registration authorization and a dedicated bot | Mervin | blocking Telegram connection |
| LIM-022 | Native integration nodes do not expose the approved 15-second target timeout or exact 2s/5s backoff | Reliability contract requires explicit orchestration | Validate the approved retry design before connection or execution | Mervin | implementation deferred |
| LIM-023 | Airtable priority choices still use `P1 critical` through `P4 low`, not the approved `p1-critical` through `p4-low` values | Direct writes can fail or silently diverge from the approved schema | Separately authorize the four schema-only renames, verify read-only, then repeat the gate | Mervin | blocking Airtable credential |
| LIM-024 | Multiline JSON and nullable `ai_schema_valid` needed physical conventions | The decision blocker is resolved, but storage behavior is untested | Use the approved compact UTF-8 JSON and blank/true/false rules; validate only in an authorized integration batch | Mervin | resolved decision; not-run |
| LIM-025 | One sanitized ClickUp create and replay passed, but the ClickUp branch is not wired into the main inactive workflow and the failure path remains not-run | End-to-end ClickUp integration readiness cannot be claimed | Build and validate the branch separately; keep production-grade concurrency locking deferred | Mervin | fixture passed; integration deferred |

## Current Safety Boundaries

- Dummy or irreversibly sanitized data only.
- No real customer data, production credentials, or live destinations.
- No automatic customer replies.
- No activation, deployment, closure, deletion, or unapproved external side effects.
- No portfolio screenshots until sanitized evidence exists.
- Gemini may receive only approved dummy or sanitized structured JSON text. Credential `AI TASK` exists and passed its connection test, but no workflow node or Gemini API call is authorized or evidenced.
- Phase 1 permits only mocked duplicate and AI results and a final structured output.

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
- Review date: 2026-07-25
- Production acceptance: not approved

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Implementation Plan|Implementation Plan]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
