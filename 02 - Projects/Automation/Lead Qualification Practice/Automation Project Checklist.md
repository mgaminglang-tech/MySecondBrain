---
type: project-checklist
status: demo-complete
phase: demo-closure
owner: Mervin
production_ready: false
client: Demo Sales Company
project: Lead Qualification Practice
updated: 2026-07-24
tags:
  - client-automation
  - project-management
  - checklist
---

# Lead Qualification Practice Automation Project Checklist

## How to Use This Project Checklist

1. Treat [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]] as the permanent process reference.
2. Use this project copy to track actual evidence, approvals, blockers, and deferred work.
3. Mark a checkbox complete only when the linked project documentation supports it.
4. Keep demo acceptance separate from production readiness and full project closure.

> [!danger] Approval boundary
> This practice project has no production approval. Credentials, external side effects, activation, integrations, and production deployment require separate explicit approval.

## Project Record

- Client: `Demo Sales Company`
- Project: `Lead Qualification Practice`
- Project folder: `02 - Projects/Automation/Lead Qualification Practice/`
- Project owner: Mervin
- Automation engineer: Automation Engineer role documented; individual assignment not recorded
- Client approver: Project Owner role documented; final client/owner approval not recorded
- Current phase: demo-closure
- Project status: demo-complete
- Production ready: false
- DEV workflow name: `DEV - Demo Sales Company - Lead Qualification Practice - v0.1`
- DEV workflow ID: `Or7VHPFQakcY3l0Q`
- STAGING workflow name or `not used`: not used
- PROD workflow name or `not approved`: not approved
- Checklist updated: 2026-07-24

## 1. Project Intake and Discovery

- [x] A project folder exists in the approved vault location.
- [x] This checklist was duplicated into the project folder.
- [ ] A project copy of [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] is complete and linked.
- [x] Business problem and desired outcome are specific.
- [x] Current process, users, systems, volumes, timing, and exceptions are documented.
- [x] Project owner, technical owner, stakeholders, and approver roles are documented.
- [x] Dummy or sanitized sample data is available.
- [x] Assumptions, open questions, dependencies, risks, and blockers are recorded.
- [ ] Discovery decision is recorded as GO, CONDITIONAL GO, or NO-GO.

**Discovery decision:** Not recorded in a project discovery checklist.  
**Owner/date/evidence:** See [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]] and [[02 - Projects/Automation/Lead Qualification Practice/Lead Qualification Practice Overview|Lead Qualification Practice Overview]].

## 2. Scope

- [x] Included workflows, integrations, data, environments, and deliverables are defined.
- [x] Exclusions, deferred phases, and remaining manual steps are defined.
- [x] Demo, MVP, or release boundary is measurable.
- [x] Change-control process is documented.
- [ ] Timeline, budget, client dependencies, and approval deadlines are recorded when applicable.
- [x] Scope approval is recorded for the controlled v0.1 demo.

**Scope approval:** Controlled inactive DEV demo scope approved; production scope not approved.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]], [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]], and [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]].

## 3. Requirements

- [x] Inputs, types, required fields, formats, ranges, and normalization rules are defined.
- [x] Outputs and exact schemas are defined.
- [x] Business rules, calculations, thresholds, routing, and fallbacks are testable.
- [x] Invalid, empty, duplicate, partial, and edge-case behavior is defined or explicitly deferred.
- [x] Error handling, retry, timeout, human-review, alerting, and recovery requirements are defined or deferred.
- [x] Volume, performance, retention, RTO, RPO, monitoring, and support requirements are defined.
- [x] Success criteria and phase-specific acceptance gates are measurable.
- [x] Requirements approval is recorded for the controlled demo.

**Requirements approval:** Approved for v0.1 controlled demo only.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]] and [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]].

## 4. Architecture and Documentation

- [x] DEV, optional STAGING, and PROD responsibilities are separated.
- [x] Workflow name, trigger, nodes, connections, and versions are documented.
- [x] Data flow, storage, notifications, identity, duplicate handling, and side effects are documented.
- [x] Credential requirements are listed by name, owner, purpose, environment, and minimum permission—never by secret value.
- [x] Failure paths, retries, idempotency, concurrency, monitoring, backup, and rollback are designed or explicitly deferred.
- [x] Test Plan, Test Results, Issues and Fixes, Known Limitations, Deployment Checklist, Backup and Restore, Maintenance Guide, Client Handover, Lessons Learned, and Case Study notes exist as applicable.
- [x] Architecture approval is recorded for the controlled demo.

**Architecture approval:** Accepted for inactive DEV demo only; no production architecture is approved.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] and [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]].

## 5. Security and Privacy

- [x] Data classification and sensitive-data boundaries are documented.
- [x] Dummy or sanitized DEV-data rules are documented.
- [ ] Logging, masking, retention, geographic, privacy, and compliance requirements are all recorded.
- [x] No secrets or unredacted sensitive data are stored in Obsidian or Git.
- [x] Least-privilege access and credential ownership are defined for the zero-credential v0.1 scope.
- [x] DEV and PROD credentials are separated when production is in scope; PROD is not in scope for v0.1.
- [x] Security and privacy review roles are identified.
- [ ] Real-client credential assignment has explicit approval before use.

**Credential-assignment approval or status:** Not applicable to v0.1; the workflow uses zero credentials. Future credential assignment is not approved.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]].

## 6. Pre-development Review

- [x] Business problem, outcome, scope, inputs, outputs, rules, and acceptance criteria were reviewed.
- [x] Security, privacy, credentials, duplicate handling, retries, human review, and operations were reviewed.
- [x] Test coverage includes happy paths, invalid inputs, boundaries, edge cases, and failures.
- [x] Document conflicts and missing decisions were recorded.
- [ ] Review recommendation is recorded as GO, CONDITIONAL GO, or NO-GO in a project note.
- [x] Blocking findings were resolved or explicitly deferred.
- [x] DEV development authorization is recorded.

**Review decision:** A formal GO, CONDITIONAL GO, or NO-GO record is not stored in the project folder.  
**Development authorization:** Recorded for v0.1 DEV only.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]], [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]], and [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]].

## 7. Git Checkpoint

- [ ] Repository status and relevant diff were inspected and recorded in the project.
- [ ] Unrelated user changes were identified and preserved in project evidence.
- [ ] Secret, generated-file, binary, and accidental broad-change checks were recorded.
- [ ] Pre-build recovery point is documented.
- [ ] Commit or no-commit decision is recorded.
- [ ] No commit or push occurred without explicit authorization is recorded as project evidence.

**Branch:** Not recorded.  
**Checkpoint commit or decision:** Not recorded.  
**Owner/date/evidence:** No project-scoped Git checkpoint evidence is available.

## 8. n8n MCP Audit

- [ ] MCP connectivity and available n8n version information were recorded in the project.
- [x] Required nodes and node versions are documented as available in the implemented workflow.
- [x] Expressions, code, hashing, and compatibility concerns were reviewed.
- [ ] Existing workflow naming-conflict evidence is recorded.
- [x] Credential, external-node, environment, and safety blockers were reviewed.
- [x] Recommended inactive DEV architecture is recorded.
- [ ] Audit conclusion is recorded as GO, CONDITIONAL GO, or NO-GO in a project note.
- [ ] A project note confirms no workflow, credential, execution, activation, or setting changed during the read-only audit.

**Audit conclusion:** The implemented environment supports the documented workflow, but the earlier read-only audit record is not stored in the project folder.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] and [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]].

## 9. Inactive DEV Build

- [x] Canonical DEV workflow name is used.
- [x] Only the approved workflow and architecture were created or changed.
- [x] Workflow remains inactive.
- [x] Dummy or sanitized data is used.
- [x] Nodes, versions, parameters, expressions, and connections match the approved design.
- [x] Credentials are absent.
- [x] External side effects are absent.
- [x] Node and workflow validation completed.
- [x] Workflow ID, version, node count, connection count, credential count, and external-node count are recorded.
- [x] No activation or production change occurred.

**Workflow ID/version:** `Or7VHPFQakcY3l0Q` / `v0.1`.  
**Validation evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]], [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]], and [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]].

## 10. Controlled Testing

- [x] Test fixtures use dummy or sanitized data.
- [x] Exact expected results are documented before execution.
- [x] Tests ran independently against the approved inactive workflow.
- [x] Available execution IDs and actual outputs are recorded; TC-001 has no recorded successful execution ID.
- [x] PASS, FAIL, BLOCKED, not-run, and deferred statuses are accurate.
- [ ] Testing-stop behavior was required and evidenced for an unreliable later-test condition.
- [x] Defects, root causes, fixes, and retest evidence are recorded.
- [x] Temporary pin data and test artifacts were cleared.
- [x] Workflow remained inactive and saved configuration changes are documented.
- [x] Accepted demo test gate passed.

**Test totals:** Core Release Suite: 25 passed, 0 failed, 0 blocked. Extended Regression Suite: 88 not run. v0.2 integration tests: 10 deferred.  
**Accepted test gate:** 25/25 Core Release Suite passed for the controlled inactive DEV demo.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]] and [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]].

## 11. Demo or Client Approval

- [x] Only verified features and evidence are presented.
- [x] Known limitations, not-run tests, blockers, and deferred work are disclosed.
- [x] Demo acceptance is clearly separated from production readiness.
- [x] The absence of client feedback and production outcomes is stated without inventing approval.
- [ ] Client or owner approval decision, approver, date, and evidence are recorded.
- [ ] Next-phase authorization is explicit.

**Decision:** Demo phase complete based on the accepted Core Release Suite; production readiness is not approved.  
**Approved phase only:** Controlled inactive DEV demo.  
**Approver/date/evidence:** Final client/owner approval is not recorded.

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

**Deployment approval:** Not approved.  
**Activation approval:** Not approved.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]] and [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]].

## 13. Handover and Closure

- [x] Workflow inventory, documentation, tests, issues, limitations, release history, and environment status are current for the demo.
- [ ] Credential ownership, access, monitoring, incident response, backup, restore, rollback, maintenance, and support were fully reviewed.
- [ ] Receiving owner completed the walkthrough.
- [ ] Temporary access was removed when authorized.
- [ ] Handover acceptance is recorded.
- [x] Lessons Learned contains evidence-backed lessons.
- [ ] Case Study has publication or anonymization approval.
- [x] Deferred work and future-phase owner roles are recorded.
- [x] Project status accurately distinguishes demo complete from production ready and closed.
- [ ] Closure approval is recorded.

**Handover decision:** Incomplete.  
**Closure decision:** Not applicable yet; decide whether to archive the demo or continue with v0.2.  
**Owner/date/evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]], [[02 - Projects/Automation/Lead Qualification Practice/Lessons Learned|Lessons Learned]], and [[02 - Projects/Automation/Lead Qualification Practice/Case Study|Case Study]].

## Approval Register

| Gate | Decision | Approver | Date | Evidence |
|---|---|---|---|---|
| Discovery | Not recorded |  |  | No project discovery checklist |
| Scope | Approved for v0.1 demo | Project Owner and Automation Engineer roles; individuals not recorded |  | [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]] |
| Requirements | Approved for v0.1 demo | Project Owner and Automation Engineer roles; individuals not recorded |  | [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]] |
| Architecture | Approved for v0.1 demo | Project Owner and Automation Engineer roles; individuals not recorded |  | [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] |
| DEV build | Authorized for inactive DEV | Project Owner role; individual not recorded |  | [[02 - Projects/Automation/Lead Qualification Practice/Development Plan|Development Plan]] |
| Test gate | 25/25 Core Release Suite passed | Approver not recorded |  | [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]] |
| Demo or client acceptance | Demo phase complete; client/owner approval outstanding |  |  | [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]] |
| Credentials | Not required for v0.1 |  |  | [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]] |
| External side effects | Not approved; absent from v0.1 |  |  | [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] |
| Production deployment | Not approved |  |  | [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]] |
| Activation | Not approved; workflow inactive |  |  | [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]] |
| Handover | Incomplete |  |  | [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]] |
| Closure | Not approved |  |  | [[02 - Projects/Automation/Lead Qualification Practice/Lead Qualification Practice Overview|Lead Qualification Practice Overview]] |

## Current Blockers and Deferred Work

| ID | Blocker or deferred item | Owner | Due date or trigger | Status | Evidence |
|---|---|---|---|---|---|
| LQP-001 | Run 88-test Extended Regression Suite | Project Owner and Automation Engineer | Before production deployment or after a major workflow change | not run | [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]] |
| LQP-002 | Complete operational review and recovery evidence | Project Owner and Automation Engineer | Before live deployment | open | [[02 - Projects/Automation/Lead Qualification Practice/Backup and Restore|Backup and Restore]] |
| LQP-003 | Obtain client/owner approval | Project Owner | Before live deployment or final handover | open | [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]] |
| LQP-004 | Complete ten deferred v0.2 integration tests | Future v0.2 owner | After v0.2 scope approval | deferred | [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]] |
| LQP-005 | Decide whether to archive or continue with v0.2 | Mervin | Next project decision | open | [[02 - Projects/Automation/Lead Qualification Practice/Lead Qualification Practice Overview|Lead Qualification Practice Overview]] |

## Next Action

Decide whether to archive the demo project or continue with v0.2.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Lead Qualification Practice Overview|Lead Qualification Practice Overview]]
- [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]]
- [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]]
- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
