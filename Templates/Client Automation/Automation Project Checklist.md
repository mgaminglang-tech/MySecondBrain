---
type: automation-project-checklist
status: template
client: CLIENT_NAME
project: PROJECT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - project-management
  - checklist
---

# Automation Project Checklist

## How to Use This Template

1. Treat [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]] as the permanent process reference.
2. Duplicate this template into every automation project folder before work begins.
3. Rename the project copy clearly, for example: `Acme Lead Routing Project Checklist.md`.
4. Use the project copy—not this template—to track actual status, evidence, approvals, blockers, and deferred work.
5. Link the project copy to its completed [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] copy.
6. Mark a checkbox complete only when evidence exists.

> [!danger] Real-client approval boundary
> Real-client projects require explicit approval before credentials are assigned, external side effects are enabled, a workflow is activated, or production deployment begins. Approval for discovery, documentation, DEV, testing, or a demo does not authorize production.

## Project Record

- Client: `CLIENT_NAME`
- Project: `PROJECT_NAME`
- Project folder:
- Project owner:
- Automation engineer:
- Client approver:
- Current phase:
- Project status: planned
- DEV workflow name:
- STAGING workflow name or `not used`:
- PROD workflow name or `not approved`:
- Checklist updated:

## 1. Project Intake and Discovery

- [ ] A project folder exists in the approved vault location.
- [ ] This checklist was duplicated into the project folder.
- [ ] A project copy of [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] is complete and linked.
- [ ] Business problem and desired outcome are specific.
- [ ] Current process, users, systems, volumes, timing, and exceptions are documented.
- [ ] Project owner, technical owner, stakeholders, and approvers are named.
- [ ] Dummy or sanitized sample data is available.
- [ ] Assumptions, open questions, dependencies, risks, and blockers are recorded.
- [ ] Discovery decision is recorded as GO, CONDITIONAL GO, or NO-GO.

**Discovery decision:**  
**Owner/date/evidence:**  

## 2. Scope

- [ ] Included workflows, integrations, data, environments, and deliverables are defined.
- [ ] Exclusions, deferred phases, and remaining manual steps are defined.
- [ ] Demo, MVP, or release boundary is measurable.
- [ ] Change-control process is documented.
- [ ] Timeline, budget, client dependencies, and approval deadlines are recorded when applicable.
- [ ] Scope approval is recorded.

**Scope approval:**  
**Owner/date/evidence:**  

## 3. Requirements

- [ ] Inputs, types, required fields, formats, ranges, and normalization rules are defined.
- [ ] Outputs and exact schemas are defined.
- [ ] Business rules, calculations, thresholds, routing, and fallbacks are testable.
- [ ] Invalid, empty, duplicate, partial, and edge-case behavior is defined.
- [ ] Error handling, retry, timeout, human-review, alerting, and recovery requirements are defined or deferred.
- [ ] Volume, performance, retention, RTO, RPO, monitoring, and support requirements are defined.
- [ ] Success criteria and phase-specific acceptance gates are measurable.
- [ ] Requirements approval is recorded.

**Requirements approval:**  
**Owner/date/evidence:**  

## 4. Architecture and Documentation

- [ ] DEV, optional STAGING, and PROD responsibilities are separated.
- [ ] Workflow name, trigger, nodes, connections, and versions are documented.
- [ ] Data flow, storage, notifications, identity, duplicate handling, and side effects are documented.
- [ ] Credential requirements are listed by name, owner, purpose, environment, and minimum permission—never by secret value.
- [ ] Failure paths, retries, idempotency, concurrency, monitoring, backup, and rollback are designed or explicitly deferred.
- [ ] Test Plan, Test Results, Issues and Fixes, Known Limitations, Deployment Checklist, Backup and Restore, Maintenance Guide, Client Handover, Lessons Learned, and Case Study notes exist as applicable.
- [ ] Architecture approval is recorded.

**Architecture approval:**  
**Owner/date/evidence:**  

## 5. Security and Privacy

- [ ] Data classification and sensitive fields are documented.
- [ ] Dummy or sanitized DEV-data rules are documented.
- [ ] Logging, masking, retention, geographic, privacy, and compliance requirements are recorded.
- [ ] No secrets or unredacted sensitive data are stored in Obsidian or Git.
- [ ] Least-privilege access and credential ownership are defined.
- [ ] DEV and PROD credentials are separated when production is in scope.
- [ ] Security and privacy approvers are identified.
- [ ] Real-client credential assignment has explicit approval before use.

**Credential-assignment approval or status:**  
**Owner/date/evidence:**  

## 6. Pre-development Review

- [ ] Business problem, outcome, scope, inputs, outputs, rules, and acceptance criteria were reviewed.
- [ ] Security, privacy, credentials, duplicate handling, retries, human review, and operations were reviewed.
- [ ] Test coverage includes happy paths, invalid inputs, boundaries, edge cases, and failures.
- [ ] Document conflicts and missing decisions were recorded.
- [ ] Review recommendation is GO, CONDITIONAL GO, or NO-GO.
- [ ] Blocking findings are resolved or explicitly accepted.
- [ ] DEV development authorization is recorded.

**Review decision:**  
**Development authorization:**  
**Owner/date/evidence:**  

## 7. Git Checkpoint

- [ ] Repository status and relevant diff were inspected.
- [ ] Unrelated user changes were identified and preserved.
- [ ] Secret, generated-file, binary, and accidental broad-change checks were completed.
- [ ] Pre-build recovery point is documented.
- [ ] Commit or no-commit decision is recorded.
- [ ] No commit or push occurred without explicit authorization.

**Branch:**  
**Checkpoint commit or decision:**  
**Owner/date/evidence:**  

## 8. n8n MCP Audit

- [ ] MCP connectivity and available n8n version information were checked read-only.
- [ ] Required nodes and node versions are available.
- [ ] Expressions, code, hashing, and compatibility concerns were reviewed.
- [ ] Existing workflow naming conflicts were checked.
- [ ] Credential, external-node, environment, and safety blockers were reviewed.
- [ ] Recommended inactive DEV architecture is recorded.
- [ ] Audit conclusion is GO, CONDITIONAL GO, or NO-GO.
- [ ] No workflow, credential, execution, activation, or setting was changed during the read-only audit.

**Audit conclusion:**  
**Owner/date/evidence:**  

## 9. Inactive DEV Build

- [ ] Canonical DEV workflow name is used.
- [ ] Only the approved workflow and architecture were created or changed.
- [ ] Workflow remains inactive.
- [ ] Dummy or sanitized data is used.
- [ ] Nodes, versions, parameters, expressions, and connections match the approved design.
- [ ] Credentials are absent or explicitly approved for the DEV phase.
- [ ] External side effects are absent, disabled, pinned, mocked, or explicitly approved.
- [ ] Node and workflow validation completed.
- [ ] Workflow ID, version, node count, connection count, credential count, and external-node count are recorded.
- [ ] No activation or production change occurred.

**Workflow ID/version:**  
**Validation evidence:**  

## 10. Controlled Testing

- [ ] Test fixtures use dummy or sanitized data.
- [ ] Exact expected results are documented before execution.
- [ ] Tests run independently against the approved inactive workflow.
- [ ] Execution IDs and actual outputs are recorded.
- [ ] PASS, FAIL, BLOCKED, not-run, and deferred statuses are accurate.
- [ ] Testing stopped when a failure made later results unreliable.
- [ ] Defects, root causes, fixes, and retest evidence are recorded.
- [ ] Temporary pin data and test artifacts were cleared.
- [ ] Workflow remained inactive and saved configuration changes are documented.
- [ ] Accepted demo, client, or release test gate passed.

**Test totals:**  
**Accepted test gate:**  
**Owner/date/evidence:**  

## 11. Demo or Client Approval

- [ ] Only verified features and evidence are presented.
- [ ] Known limitations, not-run tests, blockers, and deferred work are disclosed.
- [ ] Demo acceptance is clearly separated from production readiness.
- [ ] Client feedback is recorded without inventing approval.
- [ ] Approval decision, approver, date, and evidence are recorded.
- [ ] Next-phase authorization is explicit.

**Decision:**  
**Approved phase only:**  
**Approver/date/evidence:**  

## 12. Production Deployment

Complete this section only when live deployment is explicitly in scope.

- [ ] Production scope and architecture are approved.
- [ ] Real-client credential assignment is explicitly approved.
- [ ] External writes, sends, and other side effects are explicitly approved.
- [ ] Required regression, integration, UAT, performance, recovery, and security tests passed.
- [ ] Backup export and restore evidence are verified.
- [ ] Monitoring, alerts, retries, idempotency, concurrency, reconciliation, support, and incident response are ready.
- [ ] Production rollback plan and stop conditions are approved.
- [ ] Production deployment is explicitly approved.
- [ ] Workflow activation is explicitly approved.
- [ ] Controlled production smoke test passed.
- [ ] Production state, version, activation, and results are recorded.

**Deployment approval:**  
**Activation approval:**  
**Owner/date/evidence:**  

## 13. Handover and Closure

- [ ] Workflow inventory, documentation, tests, issues, limitations, release history, and environment status are current.
- [ ] Credential ownership, access, monitoring, incident response, backup, restore, rollback, maintenance, and support were reviewed.
- [ ] Receiving owner completed the walkthrough.
- [ ] Temporary access was removed when authorized.
- [ ] Handover acceptance is recorded.
- [ ] Lessons Learned contains evidence-backed lessons.
- [ ] Case Study uses actual evidence and has publication or anonymization approval when required.
- [ ] Deferred work and future-phase owners are recorded.
- [ ] Project status accurately distinguishes demo complete, production ready, completed, on hold, or archived.
- [ ] Closure approval is recorded only when all applicable obligations are complete.

**Handover decision:**  
**Closure decision:**  
**Owner/date/evidence:**  

## Approval Register

| Gate | Decision | Approver | Date | Evidence |
|---|---|---|---|---|
| Discovery |  |  |  |  |
| Scope |  |  |  |  |
| Requirements |  |  |  |  |
| Architecture |  |  |  |  |
| DEV build |  |  |  |  |
| Test gate |  |  |  |  |
| Demo or client acceptance |  |  |  |  |
| Credentials |  |  |  |  |
| External side effects |  |  |  |  |
| Production deployment |  |  |  |  |
| Activation |  |  |  |  |
| Handover |  |  |  |  |
| Closure |  |  |  |  |

## Current Blockers and Deferred Work

| ID | Blocker or deferred item | Owner | Due date or trigger | Status | Evidence |
|---|---|---|---|---|---|
|  |  |  |  | open |  |

## Related Notes

- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[Templates/Client Automation/Client Automation Project|Client Automation Project]]
