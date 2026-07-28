---
type: automation-project-checklist
status: in-progress
phase: phase-2-controlled-dev-integration
client: internal-demo
project: SupportFlow AI - Gmail and Telegram Ticketing System
owner: Mervin
production_ready: false
created: 2026-07-25
updated: 2026-07-28
tags:
  - client-automation
  - project-management
  - checklist
---

# Automation Project Checklist

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]. A checked gate requires evidence and approval; creating a planning note does not complete its gate.

> [!danger] Authorization boundary
> Phase 1 build and six manual fixture runs were completed. The Gemini credential stage, isolated ClickUp read-only audit, and `SF-CUP-001` create/idempotency fixture are complete. The fixture created exactly one sanitized DEV task and its replay created none. This record does not authorize the next workflow build, additional fixture execution, workflow activation, production work, or any other external side effect.

## Project Record

- Project folder: `02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/`
- Project owner: Mervin
- Current approver: Mervin
- Future client stakeholders: Not Yet Defined
- Current phase: Phase 2 controlled DEV integration — ClickUp branch build gate
- Project status: in-progress
- Production ready: false
- DEV workflow: `DEV - SupportFlow AI - Gmail and Telegram Ticketing System` — built and inactive; ID `cyiCqsjLQdB7apjP`
- STAGING workflow: not used
- PROD workflow: not approved
- Testing: Phase 1 seed suite and ClickUp `SF-CUP-001` fixture passed; full integration testing not-run
- Updated: 2026-07-28

## Lifecycle Gates

| Gate | Status | Required evidence or blocker | Approval |
|---|---|---|---|
| 1. Discovery | complete | Approved Discovery Decision Pack recorded | Mervin, 2026-07-25 |
| 2. Scope | complete | Version-one boundary and exclusions approved | Mervin, 2026-07-25 |
| 3. Requirements | complete-for-phase-1 | Credential-free skeleton contracts approved | Mervin, 2026-07-25 |
| 4. Architecture | complete-for-phase-1 | Exact Phase 1 boundary and prohibitions approved | Mervin, 2026-07-25 |
| 5. Pre-development review | complete | Phase 1 readiness review completed | Mervin, 2026-07-25 |
| 6. Git checkpoint | pending | Separately authorized status/diff review and checkpoint decision | Not Yet Defined |
| 7. Read-only MCP audit | complete | Required node types and versions confirmed compatible | Mervin authorization, 2026-07-25 |
| 8. Inactive DEV build | complete-for-phase-1 | Workflow `cyiCqsjLQdB7apjP`, 14 approved nodes, inactive, no credentials | Mervin authorization, 2026-07-25 |
| 9. Core release suite | complete-for-phase-1 | Initial executions `7107`–`7112` and schema-alignment rerun `7113`–`7118` both passed 6 of 6; integration suite remains not-run | Mervin authorization, 2026-07-25 |
| 9a. Phase 2 decision resolution | complete | Gemini, fingerprint, schema, mapping, resource, fixture, trigger, and DEV-limit decisions recorded | Mervin, 2026-07-25 |
| 9b. Phase 2 credential-free compatibility audit | complete | All six node families exist; schema migration, Gemini privacy/model validation, and resource assignment block credentials | Mervin authorization, 2026-07-25 |
| 9c. Inactive schema alignment | complete | Workflow emits schema `0.1.0`, approved source mapping, and U+001F-composed SHA-256 input; executions `7113`–`7118` passed | Mervin authorization, 2026-07-25 |
| 9d. Airtable physical-schema gate | blocked-pending-schema-change | Base/table/43 fields verified with zero records; storage/retry decisions resolved; approved priority-choice rename remains unapplied | Mervin authorization, 2026-07-25 |
| 9e. Gemini credential stage | complete | n8n credential `AI TASK`; `Google Gemini(PaLM) API` / `googlePalmApi`; connection test passed; no API call, workflow change, activation, real data, or production use | Mervin, 2026-07-27 |
| 9f. ClickUp credential and read-only audit gate | complete | Isolated audit workflow `6yZO7DfXRD8yjsp9`; execution `7126`; PASS; hierarchy, statuses, seven custom fields, option IDs, and zero existing tasks verified; inactive and unpublished; zero writes and notifications | Mervin authorization, 2026-07-27 |
| 9g. ClickUp fixture-test gate | complete | `SF-CUP-001` creation executions `7127`–`7129` and replay executions `7130`–`7132`; one task created, replay reused it with zero writes, final count `1` | Mervin authorization, 2026-07-28 |
| 10. Demo approval | pending | Verified demo evidence and disclosed limitations | Not Yet Defined |
| 11. Production review | not-applicable-currently | Production is outside current scope | Not approved |
| 12. Deployment and activation | not-applicable-currently | Separate production scope and approvals required | Not approved |
| 13. Handover and closure | pending | Evidence-backed delivery decision | Not Yet Defined |
| 14. Archive | pending | Owner approval and archive criteria | Not Yet Defined |

## Completed Phase 1 Gate Decision

- Decision: **GO — Phase 1 credential-free skeleton validated**
- Completed boundary: Manual Trigger, dummy Gmail and Telegram payloads, normalization, unified ticket, validation, ticket ID, content fingerprint, mocked duplicate result, mocked AI output and draft, deterministic rules, and final structured output
- Evidence: workflow `cyiCqsjLQdB7apjP`; schema-alignment executions `7113`–`7118`; six passed, zero failed; final saved state inactive
- Not authorized after this completed batch: further workflow modification or execution, credentials, connections, external writes or sends, activation, integration, deployment, commit, or push
- Decision owner: Mervin
- Decision date: 2026-07-25
- Next action: build and wire the ClickUp branch into the main inactive SupportFlow workflow

## Deferred Beyond Phase 1

- Slack resource ID and credential
- Gmail and Telegram triggers and credentials
- Gemini workflow-node construction, exact structured-output configuration, and authorized API-call testing
- Execution of defined fixtures `SF-FX-007` through `SF-FX-030`
- Production-grade locking and all production work

## Approved Phase 2 Control Boundary

- DEV provider: Google Gemini; OpenAI is no longer approved.
- Schema version: `0.1.0`.
- Fingerprint separator: `\u001F`.
- Owner: Mervin.
- Airtable base `appell78p9BIEek9J`, table `tblI3JYon6kLqZPbP`, primary field `fldFnVtL1BHIjowt4`, and the complete 43-field manifest are verified. Gemini credential `AI TASK` is recorded. The ClickUp hierarchy, List, statuses, and complete seven-field manifest are verified by read-only execution `7126`; unresolved service resources remain Not Yet Assigned.
- The complete 30-fixture plan is defined, but only `SF-FX-001` through `SF-FX-006` have execution evidence.
- Mervin accepts Gemini free-tier processing for sanitized dummy DEV fixtures only. Credential `AI TASK` (`googlePalmApi`) passed its connection test; the approved future model is `models/gemini-3.1-flash-lite`. Gemini remains mocked in the workflow and no API call has been made.
- The completed authorization covered only the inactive credential-free schema alignment and executions `7113`–`7118`.

## Phase 2 Compatibility Gate

- Gemini credential stage: **complete**; credential `AI TASK` passed its connection test, with no secret recorded in the vault or Git.
- ClickUp read-only credential audit: **complete and passed**; audit workflow `6yZO7DfXRD8yjsp9`, execution `7126`, inactive and unpublished, zero writes, zero notifications, and no ClickUp credential attachment to SupportFlow workflow `cyiCqsjLQdB7apjP`.
- Recorded Airtable decision: **NO-GO for credential creation**
- Compatible node families found: Airtable 2.2, Google Gemini 1.2 / Gemini Chat Model 1.1, ClickUp 1, Slack 2.5, Gmail Trigger 1.4, and Telegram Trigger 1.3.
- The saved inactive workflow now emits schema `0.1.0`, the approved unified source fields, and SHA-256 of the normalized sender, subject, and message text joined with `\u001F`.
- Mervin accepts the documented Gemini free-tier privacy boundary for sanitized dummy DEV fixtures only; `models/gemini-3.1-flash-lite` is the approved future model and will be configured only when the Gemini workflow node is separately authorized and built.
- Airtable base/table/field IDs are assigned and verified; approved retained DEV fixture evidence exists.
- Resolved decisions: compact UTF-8 JSON serialization, `ai_schema_valid` blank/true/false handling, two read retries with 2-second and 5-second backoff, 15-second target timeout, exact-dedupe recheck after ambiguous create, and fail-closed persistent failure.
- Remaining blocker: the four physical priority choices have not yet been renamed to the approved machine values.
- ClickUp fixture creation and replay: **complete and passed**; task `86d3ut8nt` was created once and reused without another write.
- Next action: build and wire the ClickUp branch into the main inactive SupportFlow workflow.

## Completed ClickUp Read-Only Credential Audit

- Audit workflow: `AUDIT - SupportFlow AI - ClickUp Read-Only Credential Test`
- Workflow ID: `6yZO7DfXRD8yjsp9`
- Execution ID: `7126`
- Result: **PASS**
- Workflow state: inactive and unpublished
- Verified hierarchy: Workspace `90161719575` → Space `Team Space` (`90167621384`) → Folder `Support Operations - Automation` (`901610630678`) → List `DEV - SupportFlow AI - Ticket Queue` (`901616152035`)
- List state: `archived=false`
- Statuses: `to do`, `in progress`, `complete`
- Existing task count: `0`
- Custom fields: seven required fields and all dropdown option IDs verified; canonical manifest is in [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model#Verified ClickUp Physical Manifest|Data Model]]
- Side effects: zero writes and zero notifications
- SupportFlow isolation: no ClickUp credential attachment to workflow `cyiCqsjLQdB7apjP`

## Completed ClickUp Fixture Evidence

- Fixture: `SF-CUP-001`
- Airtable record: `rechUtKgq1V0poegN`
- Ticket ID: `SF-20260727-7A3F1C2D`
- Task ID: `86d3ut8nt`
- Task name: `[P3] SF-20260727-7A3F1C2D — billing — Dummy invoice question`
- Task state: assigned to Mervin; status `to do`
- Isolated workflow: `ths9GF0Z819GrHYe`; inactive and unpublished
- Creation executions: pre-check `7127`, creation `7128`, verification `7129`
- Creation result: exactly one task; Airtable updated only with `clickup_task_id: 86d3ut8nt`
- Idempotency executions: pre-check `7130`, replay `7131`, final verification `7132`
- Replay result: task `86d3ut8nt` reused; zero new tasks; final count `1`; Airtable reference unchanged; zero ClickUp writes, notification-producing writes, or Airtable writes
- Known limitation: production-grade concurrency locking remains deferred

## Phase 1 Stop Conditions

- Any real or unsanitized data, credential, external connection, write, send, or live trigger appears.
- The workflow becomes active or a production claim is implied.
- A node falls outside the approved Phase 1 boundary.
- Required-field validation, ticket-ID format, fingerprint normalization, mocked contracts, deterministic precedence, or final schema cannot be validated.

## Created Planning Records

- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/SupportFlow AI Overview|SupportFlow AI Overview]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Data Model|Data Model]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Implementation Plan|Implementation Plan]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
- [x] [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Known Limitations|Known Limitations]]

These records remain the project documentation set. Phase 1 implementation and test claims are limited to the evidence recorded above; integration and production remain unverified.
