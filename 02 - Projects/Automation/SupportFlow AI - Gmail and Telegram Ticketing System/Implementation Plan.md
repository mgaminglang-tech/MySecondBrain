---
type: project-note
status: in-progress
phase: phase-1-validated
client: internal-demo
owner: Mervin
production_ready: false
version: 0.1.0
created: 2026-07-25
updated: 2026-07-25
tags:
  - client-automation
  - implementation
  - n8n
---

# Implementation Plan

## Objective

Record the gated path and verified evidence for the inactive DEV Phase 1 workflow. Further implementation still requires separate authorization.

## Development Boundaries

- Workflow: `DEV - SupportFlow AI - Gmail and Telegram Ticketing System`
- Current state: built and inactive; workflow ID `cyiCqsjLQdB7apjP`
- Data: dummy or sanitized only
- Credentials: not approved
- External side effects: not approved
- Customer replies: prohibited
- Production work: outside current scope
- Testing: Phase 1 seed suite passed; integration testing not-run

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

## Phase 4 — Inactive DEV Build

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

## Phase 5 — Controlled Testing

- [ ] Approve an exact Core Release Suite and fixture batch.
- [ ] Execute only approved DEV tests.
- [ ] Record execution IDs, expected and observed results, and allowed statuses.
- [ ] Stop when failures make later results unreliable.
- [ ] Clear temporary test data as required.
- [ ] Confirm final inactive state.

**Gate:** critical tests pass with evidence and limitations are current.

**Current status:** Phase 1 skeleton suite complete; the 30-fixture integration suite is not-run and not authorized.

## Phase 2 — Controlled DEV Integration Readiness

- [x] Replace OpenAI with Google Gemini as the approved DEV LLM provider.
- [x] Resolve fingerprint separator, schema version, and Telegram source mapping.
- [x] Approve DEV resource names, ownership, trigger boundaries, and review-cycle limits.
- [x] Define `SF-FX-007` through `SF-FX-030`; do not execute them yet.
- [x] Complete the credential-free compatibility audit for Airtable, Gemini, ClickUp, Slack, Gmail, and Telegram.
- [ ] Obtain separate approval before creating credentials or connecting any service.

**Current status:** inactive schema alignment is complete, Gemini free-tier processing is accepted for sanitized dummy DEV fixtures only, and the workflow remains mocked and credential-free. GO to repeat the Airtable credential gate only; credential creation and connection remain unapproved pending exact DEV resource assignment, ownership, least-privilege scope, and a separately authorized validation batch.

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
- Stop if any Gmail/Telegram trigger, Airtable, ClickUp, Slack, Gemini connection, credential, API call, external effect, or activation is introduced.
- Preserve the last validated DEV version before approved risky changes.
- Never delete tickets, tasks, alerts, workflows, or evidence as a cleanup shortcut.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Automation Project Checklist|Automation Project Checklist]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
