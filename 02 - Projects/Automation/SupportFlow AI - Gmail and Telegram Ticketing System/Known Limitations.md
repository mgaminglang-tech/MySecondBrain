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
| LIM-006 | Gemini is approved but the exact free-tier model, project, and credential are deferred | AI integration remains blocked pending compatibility evidence and separate approval | Phase 1 uses mocked output | Mervin | deferred |
| LIM-007 | DEV resource names are reserved; actual IDs and credentials are Not Yet Assigned | External integration remains blocked | Phase 1 uses no external resources | Mervin | deferred |
| LIM-008 | DEV retries and timeout are approved; production reliability remains deferred | Not production-ready | Keep Phase 1 credential-free and inactive | Mervin | deferred |
| LIM-009 | Capacity, retention, recovery, replay, and ownership are approved but untested | Operational claims cannot be made | Verify after authorized build | Mervin | not-run |
| LIM-010 | Attachment contents and edited Telegram messages are excluded from schema `0.1.0` | Some requests require manual handling | Disclose exclusion and test metadata-only path | Mervin | accepted scope boundary |
| LIM-011 | AI classification is probabilistic | Misclassification remains possible | Schema validation, deterministic overrides, human review | Mervin | open |
| LIM-012 | Automatic replies, closure, deletion, SLA enforcement, and analytics are excluded | Manual operations remain | Retain manual process or approve future phase | Mervin | accepted scope boundary |
| LIM-013 | Six Phase 1 fixtures passed, but integration, performance, retention, and recovery testing have not begun | Only skeleton behavior is evidenced | Define fixtures 007–030 and obtain separate integration-test authorization | Mervin | deferred |
| LIM-014 | Production is not approved | No live service or production-readiness claim | Separate production discovery and approval | Mervin | blocked |
| LIM-015 | UUID v4 suffix is limited to eight hexadecimal characters | Collision remains theoretically possible | Re-check ticket ID before any later create action | Mervin | accepted for DEV |
| LIM-016 | All 30 fixtures are defined, but only six seed scenarios have execution evidence | Integration testing cannot begin without separate execution authorization and credentials | Run only an explicitly approved batch later | Mervin | deferred |
| LIM-017 | Dedicated Gmail mailbox, Telegram bot/chat, and Gemini project are Not Yet Assigned | Credential creation and connection remain blocked | Assign exact DEV resources after compatibility approval | Mervin | deferred |
| LIM-018 | Gemini free-tier availability, exact model, rate limits, and n8n structured-output compatibility may change | Model cannot yet be finalized | Verify the credential-grounded model list and structured-output settings before selection | Mervin | deferred |
| LIM-019 | The former schema `0.1`, legacy source fields, and JSON-array fingerprint mismatch was corrected | No remaining schema-alignment blocker for a repeated Airtable credential gate | Preserve executions `7113`–`7118` as evidence; do not infer integration readiness | Mervin | resolved for gate repeat |
| LIM-020 | Gemini free-tier content may be used to improve provider products | Use remains unsuitable for real or unsanitized customer data | Mervin accepts free-tier processing for sanitized dummy DEV fixtures only; keep Gemini mocked until separately approved | Mervin | accepted limited DEV boundary |
| LIM-021 | Telegram Trigger 1.3 registers a webhook and drops pending updates | Testing or activation mutates Telegram state and may discard queued dummy updates | Require separate webhook-registration authorization and a dedicated bot | Mervin | blocking Telegram connection |
| LIM-022 | Native integration nodes do not expose the approved 15-second timeout or two-stage 2s/5s backoff | Reliability contract cannot be represented by a single native-node retry setting | Approve explicit orchestration or revise the DEV policy before integration build | Mervin | deferred |

## Current Safety Boundaries

- Dummy or irreversibly sanitized data only.
- No real customer data, production credentials, or live destinations.
- No automatic customer replies.
- No activation, deployment, closure, deletion, or unapproved external side effects.
- No portfolio screenshots until sanitized evidence exists.
- Gemini may receive only approved dummy or sanitized structured JSON text and remains unconnected until credential approval.
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
