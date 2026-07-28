---
type: project-note
status: in-progress
phase: phase-2-architecture-alignment
client: internal-demo
owner: Mervin
production_ready: false
version: 0.1.0
created: 2026-07-25
updated: 2026-07-28
tags:
  - client-automation
  - implementation
  - n8n
---

# Implementation Plan

## Objective

Build the complete inactive SupportFlow DEV architecture as one readable main workflow plus one focused Error Handler, validate the full configuration and connections, and only then request authorization for consolidated testing.

## Development Boundaries

- Working workflow: `SupportFlow AI - Gmail and Telegram Ticketing System`
- Current state: existing workflow `cyiCqsjLQdB7apjP` is inactive; compact architecture alignment is pending
- Data: dummy or sanitized only
- Intake: real Gmail Trigger and Telegram Trigger only; no Manual DEV Trigger
- Credentials: preserve approved DEV credentials; do not change or expose them
- External side effects: not approved
- Customer replies: prohibited
- Production work: outside current scope
- Testing: historical evidence retained; consolidated testing for the new architecture is not-run

## Approved Full-Build Sequence

1. **Intake** — add real Gmail and Telegram triggers, keep both inactive, and remove the Manual DEV Trigger from the approved design.
2. **Normalize and Validate** — normalize each channel, map the shared schema, validate required fields, reject unsupported attachments/media, and sanitize content.
3. **Duplicate Prevention and Airtable Persistence** — perform exact source-message lookup, reuse one exact record, create only on no match, preserve references, and stop on ambiguity.
4. **AI Classification and Draft Guidance** — use `AI TASK` with `models/gemini-3.1-flash-lite`, structured JSON, one retry, deterministic fallback, and approved Airtable classification updates.
5. **Operational Actions** — create or reuse the ClickUp task and prepare Gmail, Telegram, and Slack outputs without sending them.
6. **Final Result** — return one compact audit object containing successful references or safe failure details.

The main canvas should contain approximately 15–25 meaningful nodes. Robust retry, validation, API-attempt, and fallback details should be consolidated rather than expanded into long visible chains.

## Separate Error Handler Build

Retain or create `SupportFlow - Error Handler` as an inactive, unpublished, DEV-only workflow of approximately five to eight nodes:

1. receive stopped execution context
2. normalize and sanitize error details
3. classify `warning`, `error`, or `critical`
4. record a safe operational error when storage is available
5. prepare an unsent internal-alert payload
6. return `handled`, `final_status`, `safe_next_action`, `retry_allowed`, and `alert_prepared`

Authentication, billing, schema mismatch, and security issues never retry. Transient reads permit at most two retries; Gemini permits one retry; create/write actions never retry blindly.

## Phase 1 — Complete Discovery

- [x] Approve Gmail and Telegram allowlists, HTML conversion, size limit, and schema `0.1.0` exclusions.
- [x] Approve validation, categories, priorities, duplicate outcomes, deterministic overrides, and LLM failure behavior.
- [x] Approve the single Airtable table, ClickUp task contract, Slack conditions, Gemini controls, and operating defaults.
- [x] Approve 30 sanitized fixtures as the planned dataset size.

**Gate:** Mervin records discovery and scope approval.

**Current status:** complete on 2026-07-25.

## Phase 2 — Approve Design

- [x] Review Requirements, Architecture, Data Model, and Business Rules.
- [x] Resolve ticket-ID, sentiment, fingerprint, DEV reliability, resource-name, fixture-ID, and escalation decisions for Phase 1.
- [x] Define exact n8n node responsibilities through an approved read-only audit.
- [x] Reserve `SF-FX-001` through `SF-FX-030` and approve six Phase 1 seed scenarios.
- [x] Complete the pre-implementation readiness review.

**Gate:** requirements and architecture approved; explicit DEV build authorization recorded.

**Current status:** complete for Phase 1.

## Pre-Implementation Readiness Review

- Review date: 2026-07-25
- Reviewer and decision owner: Mervin
- Result: **GO for Phase 1 — Credential-Free n8n Skeleton only**
- Confirmed boundary: inactive DEV only, dummy or sanitized fixtures, no customer responses, no credentials, and no production access
- Deferred without blocking Phase 1: actual resource IDs and credentials, exact Gemini model, fixtures `SF-FX-007` through `SF-FX-030`, integration behavior, and production-grade locking

## Phase 3 — Read-Only Environment Audit

- [x] Obtain an explicit request to use n8n MCP.
- [x] Verify connectivity, required nodes, compatible node versions, and naming conflicts.
- [x] Confirm the proposed design can remain inactive and isolated.
- [x] Record GO without changing n8n during the audit.

**Gate:** read-only audit supports the approved design.

**Current status:** complete on 2026-07-25.

## Historical Phase 4 — Credential-Free DEV Build

The first implementation phase, once separately approved after the read-only audit gate, is an inactive credential-free skeleton.

- [x] Create only the approved inactive DEV workflow.
- [x] Add Manual Trigger and dummy Gmail/Telegram fixture payloads.
- [x] Normalize channels and produce the unified ticket.
- [x] Validate required fields and generate the approved ticket ID and fingerprint.
- [x] Add mocked duplicate results.
- [x] Add mocked structured AI classification and unsent draft output.
- [x] Apply deterministic rules and human-review routing.
- [x] Produce the final structured output.
- [x] Validate each node configuration and the full workflow.
- [x] Validate `SF-FX-001` through `SF-FX-006`.
- [x] Confirm no credentials, external nodes, side effects, or activation exist.

**Gate:** saved inactive workflow matches approved documentation.

**Current status:** complete on 2026-07-25. Workflow `cyiCqsjLQdB7apjP` remains inactive.

### Phase 1 Implementation Evidence

- Node count: 14
- Node versions: Manual Trigger 1, Edit Fields 3.4, Code 2, Crypto 2
- Initial manual executions: `7107`, `7108`, `7109`, `7110`, `7111`, `7112`
- Schema-alignment rerun: `7113`, `7114`, `7115`, `7116`, `7117`, `7118`
- Rerun result: six passed, zero failed
- Alignment verified: schema `0.1.0`, approved unified source mapping, and U+001F-composed SHA-256 fingerprint input
- Compatibility correction: Edit Fields raw JSON was changed from object form to runtime-compatible JSON-string form after execution `7106` failed with `jsonOutput?.startsWith is not a function`. This did not change scope or add a side effect; the complete suite was restarted afterward.
- Final verification: inactive, no active version, no credentials, no external-service nodes

## Phase 5 — Consolidated Testing

- [ ] Finish the complete inactive workflow and separate Error Handler.
- [ ] Pass a consolidated connection/configuration audit with no broken active path.
- [ ] Obtain explicit authorization for one consolidated batch.
- [ ] Run Gmail happy path.
- [ ] Run Telegram happy path.
- [ ] Run duplicate replay.
- [ ] Run one failure and deterministic-fallback case.
- [ ] Record execution IDs, expected and observed results, permitted side effects, and final inactive state.

**Gate:** critical tests pass with evidence and limitations are current.

**Current status:** historical Phase 1 evidence is retained. The new consolidated suite is not-run and cannot begin until the complete compact build and connection audit pass.

## Phase 2 — Controlled DEV Integration Readiness

- [x] Replace OpenAI with Google Gemini as the approved DEV LLM provider.
- [x] Resolve fingerprint separator, schema version, and Telegram source mapping.
- [x] Approve DEV resource names, ownership, trigger boundaries, and review-cycle limits.
- [x] Define `SF-FX-007` through `SF-FX-030`; do not execute them yet.
- [x] Complete the credential-free compatibility audit for Airtable, Gemini, ClickUp, Slack, Gmail, and Telegram.
- [x] Complete the Gemini credential stage with saved credential `AI TASK` (`Google Gemini(PaLM) API` / `googlePalmApi`) and a passed connection test.
- [x] Approve `models/gemini-3.1-flash-lite` as the future DEV classification model; defer model configuration until the Gemini workflow node is separately authorized and built.
- [x] Complete the ClickUp credential gate and isolated read-only audit: workflow `6yZO7DfXRD8yjsp9`, execution `7126`, PASS, inactive and unpublished, zero writes and notifications.
- [x] Complete the ClickUp `SF-CUP-001` create and idempotency fixture: creation executions `7127`–`7129`; replay executions `7130`–`7132`; one retained task; zero replay writes.
- [ ] Refactor and complete the full compact inactive architecture, including the approved ClickUp behavior.
- [ ] Obtain separate approval before creating or connecting any remaining service credential.

**Current status:** verified Airtable, Gemini credential, and ClickUp evidence is preserved. The next milestone is the separately authorized compact full-workflow build and consolidated connection audit. Production-grade concurrency locking remains deferred.

## Milestone Documentation and Git Policy

Update project notes and consider a Git checkpoint only after:

- architecture approval
- complete inactive build
- consolidated connection/configuration audit
- authorized consolidated test batch
- demo or production review decision

Do not document every small node edit, tool action, retry, credential check, or intermediate configuration attempt.

## Phase 6 — Demo Evidence

- [ ] Demonstrate only verified behavior.
- [ ] Create sanitized screenshots only after successful evidence exists.
- [ ] Record demo acceptance separately from production approval.
- [ ] Create Test Results, Issues and Fixes, and Case Study only when their lifecycle evidence exists.

**Gate:** Mervin accepts or rejects the controlled demo.

**Current status:** not started.

## Rollback and Stop Conditions

- Keep the workflow inactive throughout DEV.
- Stop if real data, secrets, production access, or an unapproved destination appears.
- Stop if ticket-ID, fingerprint, mocked duplicate, mocked AI, deterministic priority, or final-output behavior differs from the approved contract.
- Stop if a trigger is registered or activated, a workflow is executed before the consolidated test gate, an unapproved credential is changed, or any unapproved external write/send occurs.
- Preserve the last validated DEV version before approved risky changes.
- Never delete tickets, tasks, alerts, workflows, or evidence as a cleanup shortcut.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Automation Project Checklist|Automation Project Checklist]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
