---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Standard Automation Project Workflow

## Purpose

Define the automation-specific lifecycle, evidence gates, and operational controls for practice, demo, internal, and real-client automation projects.

This standard extends [[Project Lifecycle Standard]]. `AGENTS.md` remains controlling for security, Git, credentials, external side effects, production, and approval boundaries.

## Automation Lifecycle

**Discovery → Scope → Requirements and Architecture → Pre-development Review → Capability Audit → Inactive DEV Build → Integration Validation → Consolidated Testing → Release Decision → Deployment → Handover**

Completing one stage does not authorize the next stage or any higher-risk action. Record actual state, evidence, approvals, blockers, deferred work, and next action in the project’s current sources of truth.

## 1 — Discovery and Scope

- Record the business problem, current process, intended result, users, systems, data, volume, exceptions, risks, owners, and approvers.
- Separate confirmed facts, assumptions, open questions, and future ideas.
- Define included workflows, integrations, environments, deliverables, exclusions, manual steps, dependencies, success evidence, and the minimum demo or release boundary.
- Stop when ownership, data permission, security, feasibility, or acceptance criteria remain materially unresolved.

**Gate:** The outcome, scope, exclusions, evidence, and required approvals are clear enough to design.

## 2 — Requirements and Architecture

- Define inputs, outputs, normalization, validation, business rules, routing, identity, duplicate handling, errors, retries, human review, and side effects.
- Define environment, credential, privacy, retention, performance, recovery, monitoring, support, and ownership boundaries.
- Specify expected behavior and phase-specific test and acceptance criteria.
- Keep project-specific details in focused deep documents and link them from the Project Hub.

**Gate:** An independent reviewer can evaluate the design without inventing material behavior.

## 3 — Pre-development Review

Review the proposed build for:

- executable contracts and measurable acceptance criteria
- practical workflow architecture and maintainability
- security, privacy, credentials, duplicate and retry controls, failure handling, and human review
- contradictions, missing decisions, operational risks, and unresolved external dependencies

Return GO, CONDITIONAL GO, or NO-GO for the proposed DEV build. Record unresolved conditions and the exact authorized scope.

## 4 — Read-only Capability Audit

- Confirm connectivity and applicable platform or node versions without changing runtime state.
- Verify required capabilities, node types, expressions, code, authentication types, and compatibility constraints.
- Identify naming conflicts, unavailable capabilities, credential requirements, and side-effect risks.
- Record the recommended inactive DEV design and any blockers.

**Gate:** The environment can support the approved DEV design without unresolved blockers. The audit itself authorizes no build, execution, credential use, or external action.

## 5 — Inactive DEV Build

- Build only the approved workflow and components.
- Use the approved DEV name, architecture, dummy or sanitized data, and non-production boundaries.
- Keep the workflow inactive except for an explicitly approved isolated test mechanism.
- Configure only approved nodes, parameters, credentials, and controlled side-effect paths.
- Validate saved node configuration, connections, workflow structure, credential references, external nodes, and inactive state.
- Record the workflow reference, version, inventory, and validation evidence without recording secret values.

**Gate:** The saved inactive DEV workflow matches the approved requirements and architecture.

## 6 — Integration Validation

- Validate mappings, schemas, identifiers, credential references, permissions, destinations, and failure paths before broader execution.
- Keep credentials environment-specific and disclose any untested or mocked integration.
- Verify external writes, recipients, or trigger side effects only within an explicitly approved non-production scope.
- Do not treat a connection check as end-to-end integration evidence.

**Gate:** Each required integration is verified for the approved environment or clearly marked blocked, mocked, deferred, or not run.

## 7 — Consolidated Testing

- Use the smallest complete approved suite covering critical happy paths, boundaries, duplicates or idempotency, invalid input, retries, failure, and fallback behavior where applicable.
- Record expected and actual results, evidence references, and PASS, FAIL, BLOCKED, or NOT RUN status.
- Stop when a failure makes later results unreliable; fix and retest only within approved scope.
- Remove temporary fixtures or pin data when required and verify the final saved inactive state.
- Keep omitted regression and future integration tests visible.

**Gate:** The defined demo, acceptance, or release suite passes with evidence, or remaining limitations are explicitly accepted by the authorized decision-maker.

## 8 — Demo and Release Decision

- Demonstrate only verified features and disclose failures, limitations, blocked integrations, and not-run tests.
- Distinguish practice demo, client acceptance, production candidate, and production-ready state.
- Demo or client acceptance does not authorize credentials, external side effects, activation, or production.
- Record the accepted boundary, approver, evidence, and authorized next phase.

## Draft-Derived Environment and Release Conventions

The following operational conventions came from a legacy draft policy. Apply them as defaults until they are separately reviewed or replaced; do not treat them as verified production evidence.

### Naming and Versioning

- DEV workflow: `DEV - Client or Project - Workflow Name`
- PROD workflow: `PROD - Client or Project - Workflow Name`
- DEV credential: `DEV - Service - Purpose`
- PROD credential: `PROD - Service - Purpose`
- Use `v0.1.0` for an initial development version, `v0.2.0` for a development feature update, `v0.2.1` for a development fix, and `v1.0.0` for the first approved production release.
- After `v1.0.0`, use semantic versioning unless the project approves another documented scheme.

STAGING is optional. When used, document its owner, data rules, separate non-production credentials, activation controls, and acceptance criteria.

### Release Ownership

| Role | Responsibility |
| --- | --- |
| Project owner | Scope, risk, stakeholder communication, and final acceptance. |
| Developer | DEV build, change documentation, and test evidence. |
| Reviewer | Architecture, tests, security, failure handling, and rollback readiness. |
| PROD approver | The named release and activation window. |
| Operator | Approved deployment, smoke test, initial monitoring, and result record. |

One person may hold multiple roles, but the approval decision and operator remain explicitly recorded.

## 9 — Production Promotion Gate

Before an approved production change, verify:

- the exact scope and release version
- applicable DEV evidence and disclosed limitations
- security and client-data review
- a current readable backup and documented restore requirements under [[Backup and Recovery Standard]]
- rollback steps, owner, and decision threshold
- credential references and environment identifiers without copying secret values
- the deployment window, operator, monitoring owner, smoke-test steps, and success criteria
- explicit deployment and activation approval

## 10 — Controlled Deployment and Recovery

1. Confirm the approved version, backup, window, operator, monitoring owner, and rollback threshold.
2. Apply only the approved change and revalidate configuration and connections.
3. Activate only when explicitly authorized.
4. Run the minimum safe smoke test and monitor initial executions and error alerts.
5. Roll back when the documented threshold is reached.
6. Record the result, approver, operator, timestamps, evidence, and remaining risks.

Do not overwrite the only recoverable copy. Revalidate triggers, credentials, connections, and downstream side effects before any approved reactivation.

## 11 — Handover

- Deliver the workflow inventory, current documentation, evidence, limitations, backup and recovery information, maintenance expectations, and support contacts.
- Review access, credential ownership, monitoring, incident handling, recovery, and change control.
- Record the receiving owner’s acceptance and remove temporary access when authorized.
- Treat case-study or portfolio publication as a separate approval boundary.

## Verification

- [ ] Discovery, scope, requirements, architecture, risks, and gates are documented.
- [ ] Capability audit conclusions are read-only and evidence-backed.
- [ ] DEV remained within its approved inactive and test-data boundary.
- [ ] Integration state distinguishes verified, blocked, mocked, deferred, and not run.
- [ ] Test evidence distinguishes pass, fail, blocked, and not run.
- [ ] Demo acceptance is separate from production readiness and approval.
- [ ] Production release, recovery, ownership, monitoring, and handover gates are explicit.

## Related Standards

- [[Project Lifecycle Standard]]
- [[AI Context Standard]]
- [[Agent Operating Standard]]
- [[Migration Standard]]
- [[Backup and Recovery Standard]]
- [[Client Data Handling Standard]]
- [[Credential and Secrets Management Standard]]
