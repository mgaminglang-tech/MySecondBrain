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
| LIM-006 | Exact OpenAI model and credential are deferred | AI integration remains blocked | Phase 1 uses mocked output | Mervin | deferred |
| LIM-007 | DEV resource names are reserved; actual IDs and credentials are Not Yet Assigned | External integration remains blocked | Phase 1 uses no external resources | Mervin | deferred |
| LIM-008 | DEV retries and timeout are approved; production reliability remains deferred | Not production-ready | Keep Phase 1 credential-free and inactive | Mervin | deferred |
| LIM-009 | Capacity, retention, recovery, replay, and ownership are approved but untested | Operational claims cannot be made | Verify after authorized build | Mervin | not-run |
| LIM-010 | Attachment contents and edited Telegram messages are excluded from v0.1 | Some requests require manual handling | Disclose exclusion and test metadata-only path | Mervin | accepted scope boundary |
| LIM-011 | AI classification is probabilistic | Misclassification remains possible | Schema validation, deterministic overrides, human review | Mervin | open |
| LIM-012 | Automatic replies, closure, deletion, SLA enforcement, and analytics are excluded | Manual operations remain | Retain manual process or approve future phase | Mervin | accepted scope boundary |
| LIM-013 | Six Phase 1 fixtures passed, but integration, performance, retention, and recovery testing have not begun | Only skeleton behavior is evidenced | Define fixtures 007–030 and obtain separate integration-test authorization | Mervin | deferred |
| LIM-014 | Production is not approved | No live service or production-readiness claim | Separate production discovery and approval | Mervin | blocked |
| LIM-015 | UUID v4 suffix is limited to eight hexadecimal characters | Collision remains theoretically possible | Re-check ticket ID before any later create action | Mervin | accepted for DEV |
| LIM-016 | Only six seed scenarios are defined; fixtures 007–030 remain undefined | Integration testing cannot begin | Complete all fixtures before integration testing | Mervin | deferred |

## Current Safety Boundaries

- Dummy or irreversibly sanitized data only.
- No real customer data, production credentials, or live destinations.
- No automatic customer replies.
- No activation, deployment, closure, deletion, or unapproved external side effects.
- No portfolio screenshots until sanitized evidence exists.
- OpenAI receives only approved dummy or sanitized text and remains unconnected until credential approval.
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
