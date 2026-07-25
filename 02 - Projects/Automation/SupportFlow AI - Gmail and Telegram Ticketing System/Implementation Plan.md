---
type: project-note
status: planned
phase: discovery
client: internal-demo
owner: Mervin
production_ready: false
version: v0.1.0
created: 2026-07-25
updated: 2026-07-25
tags:
  - client-automation
  - implementation
  - n8n
---

# Implementation Plan

## Objective

Define the gated path to an inactive DEV workflow. This note does not authorize implementation.

## Development Boundaries

- Workflow: `DEV - SupportFlow AI - Gmail and Telegram Ticketing System`
- Current state: unbuilt and inactive
- Data: dummy or sanitized only
- Credentials: not approved
- External side effects: not approved
- Customer replies: prohibited
- Production work: outside current scope
- Testing: not-run

## Phase 1 — Complete Discovery

- [ ] Resolve OQ-001 through OQ-011 in Discovery and Scope.
- [ ] Approve source contracts, unified schema, taxonomy, rules, and duplicate behavior.
- [ ] Define owners, volumes, retention, privacy, retry, timeout, and recovery expectations.
- [ ] Approve exact sanitized fixtures and controlled destinations or mocks.

**Gate:** Mervin records discovery and scope approval.

**Current status:** in-progress.

## Phase 2 — Approve Design

- [ ] Review Requirements, Architecture, Data Model, and Business Rules.
- [ ] Resolve all Not Yet Defined implementation decisions.
- [ ] Define exact n8n node responsibilities without assigning credentials.
- [ ] Approve the core test IDs and expected outputs.
- [ ] Complete the required pre-development review.

**Gate:** requirements and architecture approved; explicit DEV build authorization recorded.

**Current status:** blocked by Phase 1.

## Phase 3 — Read-Only Environment Audit

- [ ] Obtain an explicit request to use n8n MCP.
- [ ] Verify connectivity, n8n version, required nodes, node versions, and naming conflicts.
- [ ] Confirm the proposed design can remain inactive and isolated.
- [ ] Record GO, CONDITIONAL GO, or NO-GO without changing n8n.

**Gate:** read-only audit supports the approved design.

**Current status:** not approved and not run.

## Phase 4 — Inactive DEV Build

- [ ] Create only the approved inactive DEV workflow.
- [ ] Build channel intake or fixture paths.
- [ ] Normalize, validate, and generate identity.
- [ ] Add duplicate lookup and fail-closed routing.
- [ ] Add constrained AI classification and unsent draft generation.
- [ ] Apply deterministic rules and human-review routing.
- [ ] Add only approved DEV storage, task, and alert destinations.
- [ ] Add bounded failure handling, idempotency, and audit output.
- [ ] Validate each changed node and the full workflow.
- [ ] Confirm credentials by reference, saved state, connections, and inactive status.

**Gate:** saved inactive workflow matches approved documentation.

**Current status:** not authorized.

## Phase 5 — Controlled Testing

- [ ] Approve an exact Core Release Suite and fixture batch.
- [ ] Execute only approved DEV tests.
- [ ] Record execution IDs, expected and observed results, and allowed statuses.
- [ ] Stop when failures make later results unreliable.
- [ ] Clear temporary test data as required.
- [ ] Confirm final inactive state.

**Gate:** critical tests pass with evidence and limitations are current.

**Current status:** not-run.

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
- Stop if duplicate safety, idempotency, or partial-failure behavior is unresolved.
- Preserve the last validated DEV version before approved risky changes.
- Never delete tickets, tasks, alerts, workflows, or evidence as a cleanup shortcut.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Automation Project Checklist|Automation Project Checklist]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Test Plan|Test Plan]]
