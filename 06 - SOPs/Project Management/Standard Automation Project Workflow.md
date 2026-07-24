---
type: sop
status: active
created: 2026-07-24
updated: 2026-07-24
tags:
  - sop
  - project-management
  - client-automation
  - n8n
---

# Standard Automation Project Workflow

## Purpose

Provide the permanent lifecycle and gate reference for practice, demo, internal, and real-client automation projects. Global repository, security, Git, MCP, credential, and production restrictions remain governed by `AGENTS.md`.

Duplicate [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]] into every project folder. The project copy records actual phase status, evidence, approvals, blockers, deferred work, and next action.

## When to Use

Use this SOP when:

- starting an automation project
- materially changing an existing workflow
- preparing a demo or client review
- considering production deployment
- handing over or archiving a project

Begin intake with a project copy of [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]].

## Lifecycle

```text
Discovery
→ Scope
→ Documentation
→ Pre-development Review
→ Git Checkpoint
→ Read-only MCP Audit
→ Inactive DEV Build
→ Core Testing
→ Demo or Client Approval
→ Deployment
→ Handover
→ Archive
```

Each phase needs evidence and authorization before the next phase begins. Completing an earlier phase never grants permission for a later high-risk action.

## Project Records

Maintain the applicable project overview, checklist, discovery record, requirements, architecture, development plan, test plan, test results, issues, credential plan, deployment checklist, backup and restore plan, maintenance guide, known limitations, lessons learned, handover, and case study.

Project records must distinguish:

- planned work from completed evidence
- DEV, optional STAGING, and PROD
- demo acceptance from production readiness
- current scope from deferred work
- expected results from observed results
- project closure from archive readiness

## Demo and Real-Client Boundaries

- **Practice or controlled demo:** May close its approved demo gate while remaining inactive and not production-ready.
- **Real-client demo:** Requires recorded client approval for the accepted demo scope; this does not authorize credentials, external side effects, activation, or production.
- **Production candidate:** Requires a separately approved production scope and all operational, security, recovery, testing, and ownership gates.
- **Production-complete project:** Requires verified deployment, handover, and operational ownership before archive consideration.

## Procedure

### 1. Discovery

1. Copy and complete the [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] in the project folder.
2. Record the business problem, current process, desired result, users, systems, data, volumes, exceptions, risks, owners, and approvers.
3. Separate confirmed facts, assumptions, open questions, and future ideas.
4. Define measurable success evidence.

**Gate:** Record GO, CONDITIONAL GO, or NO-GO. Stop on unresolved ownership, data-permission, security, or feasibility blockers.

### 2. Scope

1. Define included workflows, integrations, data, environments, deliverables, and users.
2. Define exclusions, deferred phases, manual steps, dependencies, constraints, and change control.
3. Identify the minimum demo or release boundary.
4. Record acceptance criteria and required approvals.

**Gate:** The scope owner and required approver accept the boundary.

### 3. Documentation

1. Create the required project documents from the client-automation templates.
2. Define inputs, outputs, normalization, validation, business rules, routing, identity, errors, retries, human review, and side effects.
3. Define environment, credential, privacy, retention, performance, recovery, monitoring, support, and ownership boundaries.
4. Create exact test expectations and phase-specific acceptance gates.

**Gate:** Requirements and architecture are complete enough for an independent pre-development review.

### 4. Pre-development Review

Review the project read-only for:

- clarity and completeness of the business outcome
- executable input, output, validation, scoring, routing, and error contracts
- security, privacy, credential, duplicate, retry, and human-review controls
- practical n8n architecture
- test coverage and measurable acceptance criteria
- contradictions, missing decisions, and operational risks

**Gate:** Return GO, CONDITIONAL GO, or NO-GO. Resolve or explicitly accept blockers and record DEV authorization before building.

### 5. Git Checkpoint

1. Inspect repository status and the project diff.
2. Identify and preserve unrelated changes.
3. Check for secrets, generated files, accidental binaries, and broad changes.
4. Record the authorized checkpoint commit or explicit no-commit decision.

**Gate:** The pre-build state is recoverable and reviewable.

### 6. Read-only MCP Audit

1. Confirm n8n MCP connectivity and available version information.
2. Verify required node types and versions.
3. Review expressions, code, hashing, credentials, compatibility, and naming conflicts.
4. Inspect environmental and safety blockers.
5. Record the recommended inactive DEV architecture and audit conclusion.

**Gate:** The connected environment supports the approved DEV design without unresolved blockers. The audit itself makes no n8n changes.

### 7. Inactive DEV Build

1. Create or update only the approved workflow.
2. Use the canonical DEV name and approved architecture.
3. Keep the workflow inactive and within its approved test-data boundary.
4. Configure only approved nodes, parameters, credentials, and isolated side-effect behavior.
5. Validate nodes, connections, workflow structure, credential references, external nodes, and inactive state.
6. Record workflow ID, version, inventory, and validation evidence.

**Gate:** The saved inactive DEV workflow matches the approved requirements and architecture.

### 8. Core Testing

1. Select the approved Core Release Suite from the project Test Plan.
2. Run exact tests independently with approved fixtures and expectations.
3. Record execution IDs, expected and actual results, differences, and PASS, FAIL, or BLOCKED status.
4. Stop when a failure or runtime problem makes later results unreliable.
5. Fix and retest only with approval.
6. Clear temporary pin data and record the final saved workflow state.
7. Keep extended and future integration tests visibly not run or deferred.

**Gate:** The defined core demo, client-acceptance, or release suite passes with evidence.

### 9. Demo or Client Approval

1. Demonstrate only verified features.
2. Disclose known limitations, failures, blockers, not-run tests, and deferred work.
3. State whether the result is a practice demo, client acceptance build, or production candidate.
4. Record the accepted gate, approver, evidence, and authorized next phase.

**Gate:** Demo completion is recorded separately from production approval.

### 10. Deployment

This phase applies only when live deployment is explicitly in scope.

1. Complete production-specific architecture, security, privacy, credentials, retention, monitoring, errors, retries, idempotency, concurrency, reconciliation, recovery, support, and ownership.
2. Run required regression, integration, UAT, performance, recovery, security, and smoke tests.
3. Verify the backup and rollback plan.
4. Obtain explicit deployment and activation approvals.
5. Deploy through the approved change procedure and verify controlled production results.
6. Roll back when any release gate fails.

**Gate:** Production state and evidence match the approved release, with no unresolved operational blocker.

### 11. Handover

1. Deliver the workflow inventory, documentation, evidence, limitations, backup, rollback, maintenance, and support records.
2. Review access, credential ownership, monitoring, incidents, recovery, and change control.
3. Complete the receiving-owner walkthrough and remove temporary access when authorized.
4. Record handover acceptance.
5. Prepare an evidence-only case study when applicable; obtain anonymization or publication approval.

**Gate:** The receiving owner accepts the applicable operational responsibilities and remaining work.

### 12. Archive

1. Perform the final project review.
2. Confirm final status, phase, owner, production readiness, next action, evidence, and known limitations.
3. Confirm Git changes are committed and pushed.
4. Obtain project-owner archive approval.
5. Move the complete folder only through the approved archive procedure.
6. Update navigation and verify that links and evidence remain intact.

Demo-complete projects may remain active when future work is possible. Paused work is not automatically archive-ready.

**Gate:** Every condition in [[09 - Archive/Archive|Archive]] is satisfied.

## Prompt and Token Efficiency

Use one phase-specific prompt from [[07 - AI/Automation Project Prompt Library|Automation Project Prompt Library]] instead of repeating the full lifecycle. Each prompt should reference:

- this SOP
- the project-specific `Automation Project Checklist.md`
- the applicable project source-of-truth documents
- exact workflow IDs, file paths, and test IDs when needed

Repeat only restrictions that are unusually high risk for the current phase, especially production, credentials, destructive actions, or real external side effects.

## Verification

- [ ] A project checklist copy exists and reflects the current phase.
- [ ] Discovery, scope, requirements, architecture, risks, and gates are documented.
- [ ] Git and read-only MCP audit decisions have evidence.
- [ ] DEV stayed within its approved inactive and test-data boundary.
- [ ] Test results distinguish passed, failed, blocked, not-run, and deferred cases.
- [ ] Demo approval is separate from production approval.
- [ ] Real-client credentials, side effects, activation, and deployment have explicit approvals.
- [ ] Handover and archive gates are evidence-backed.

## Rollback and Exceptions

- Return to the last completed gate when requirements, approval, or evidence becomes invalid.
- Keep affected workflows inactive while resolving DEV or release failures.
- Follow the project rollback plan for production incidents.
- Preserve evidence; do not delete workflows, credentials, records, or project history as a rollback shortcut.
- When instructions conflict, apply the precedence order in `AGENTS.md`.

## Related Notes

- [[07 - AI/Automation Project Prompt Library|Automation Project Prompt Library]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[06 - SOPs/n8n/Start a New Client Automation|Start a New Client Automation]]
- [[06 - SOPs/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[06 - SOPs/n8n/Client Automation Handover|Client Automation Handover]]
- [[09 - Archive/Archive|Archive]]
