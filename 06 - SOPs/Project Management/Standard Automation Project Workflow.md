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

Provide the permanent reference for managing automation projects from discovery through evidence-based closure. Use this SOP to define the required sequence, safety boundaries, approval gates, and records for practice, demo, internal, and real-client work.

The reusable [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]] is the execution tracker for this SOP. Duplicate that template into every automation project folder. The project copy tracks actual status, evidence, approvals, blockers, and deferred work; the template itself must remain reusable and must not be used as a live project record.

## When to Use

Use this SOP when:

- Starting a new automation project.
- Materially changing an existing workflow.
- Preparing a controlled demo or client review.
- Moving an approved workflow toward production.
- Handing over or closing an automation project.

Begin detailed intake with [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]].

## Standard Workflow

```text
Discovery
→ Scope
→ Documentation
→ Pre-development Review
→ Git Checkpoint
→ n8n MCP Audit
→ Inactive DEV Build
→ Controlled Testing
→ Demo or Client Approval
→ Deployment
→ Handover
→ Case Study
```

Each phase requires evidence before it is marked complete. A later phase must not be treated as authorized merely because an earlier phase succeeded.

## Requirements

- A dedicated project folder in `02 - Projects`.
- A duplicated project copy of [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]].
- Named project owner, technical owner, and approvers.
- Documented data classification and safe test-data plan.
- Explicit environment boundaries for DEV, optional STAGING, and PROD.
- Approved locations for credentials, backups, evidence, and client records.
- Access to the relevant template notes and n8n environment.

## Safety Considerations

- Never store passwords, API keys, access tokens, private keys, webhook secrets, or credential values in the vault or Git.
- Use dummy or sanitized data in DEV unless a separately approved policy permits otherwise.
- Keep new and changed workflows inactive until their activation gate is explicitly approved.
- Inspect the current Git and n8n state before making changes.
- Do not claim that a workflow was built, tested, deployed, approved, or handed over without evidence.
- Real-client projects require explicit approval before assigning credentials, enabling external side effects, activating a workflow, or deploying to production.
- An approval for discovery, documentation, DEV build, testing, or demo does not authorize production.

## Procedure

### 1. Discovery

1. Duplicate and complete [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] in the project folder.
2. Record the current process, business problem, desired result, users, systems, data, volumes, exceptions, risks, owners, and approvers.
3. Separate confirmed facts, assumptions, open questions, and future ideas.
4. Define measurable success and acceptance evidence.
5. Stop if critical ownership, data permission, security, or feasibility questions remain unresolved.

**Gate:** Discovery decision is recorded as GO, CONDITIONAL GO, or NO-GO.

### 2. Scope

1. Define included workflows, integrations, data, environments, deliverables, and user groups.
2. Define exclusions, deferred phases, manual steps, and change-control rules.
3. Identify the minimum demo or release scope.
4. Record dependencies, constraints, risks, and acceptance criteria.

**Gate:** Scope owner and required client approver accept the boundary.

### 3. Documentation

Create or complete the project overview, requirements, architecture, development plan, test plan, credentials checklist, deployment checklist, backup and restore plan, maintenance guide, known limitations, issues log, test results, lessons learned, handover, and case study draft as applicable.

Documentation must distinguish:

- Planned work from completed work.
- DEV, optional STAGING, and PROD.
- Demo acceptance from production readiness.
- Current release scope from deferred features.
- Expected results from observed evidence.

### 4. Pre-development Review

Perform a professional read-only review of:

- Business problem and desired outcome.
- Input, output, validation, business-rule, routing, and error contracts.
- Security, privacy, credentials, duplicate handling, retries, and human review.
- Test coverage, measurable acceptance criteria, operational responsibilities, and document conflicts.

Return GO, CONDITIONAL GO, or NO-GO. Resolve blocking findings and obtain development authorization before building.

### 5. Git Checkpoint

1. Inspect repository status and the relevant diff.
2. Confirm unrelated user changes will remain untouched.
3. Check for secrets, generated files, and accidental binary changes.
4. Create a checkpoint commit only when explicitly authorized.
5. Record the branch, commit, or documented no-commit decision in the project checklist.

**Gate:** The pre-build state is recoverable and reviewable. Never commit or push without authorization.

### 6. n8n MCP Audit

Use n8n MCP in read-only mode first:

1. Confirm connectivity and available version information.
2. Verify required node types and versions.
3. Check expressions, hashing, code, credentials, and compatibility constraints.
4. Search for workflow naming conflicts.
5. Inspect environment and safety blockers.
6. Record the recommended inactive DEV architecture.

Do not create, modify, execute, activate, or assign credentials during a read-only audit.

**Gate:** The connected environment can support the approved DEV design without an unresolved safety blocker.

### 7. Inactive DEV Build

1. Create or update only the approved workflow.
2. Use the canonical DEV name and approved node architecture.
3. Keep the workflow inactive.
4. Use dummy or sanitized fixtures.
5. Add credentials only when the project explicitly authorizes them; real-client credential assignment requires explicit approval.
6. Keep side-effect nodes disabled, absent, or safely isolated until their approved test phase.
7. Validate node configurations, connections, workflow structure, credentials, and inactive state.
8. Record the workflow ID, version, node inventory, and validation result.

### 8. Controlled Testing

1. Execute only approved tests with exact fixtures and expectations.
2. Run tests independently and preserve the workflow’s approved state.
3. Stop when a failure or runtime issue makes later results unreliable.
4. Record execution IDs, expected and actual results, differences, and PASS, FAIL, or BLOCKED status.
5. Fix only approved defects, validate again, and run only authorized retests.
6. Clear temporary pin data or test artifacts.
7. Keep unexecuted tests visibly not run and future integration tests deferred.

**Gate:** The defined demo, client-acceptance, or release suite passes with evidence.

### 9. Demo or Client Approval

1. Demonstrate only verified features and disclose limitations.
2. State whether the result is a practice demo, client acceptance build, or production candidate.
3. Record the accepted test gate, failures, blockers, and deferred work.
4. Obtain explicit approval for the next phase.

Demo approval does not authorize credentials, external side effects, activation, or production deployment.

### 10. Deployment

Deployment applies only when production work is in scope and explicitly approved.

1. Confirm production requirements, security, privacy, credentials, retention, monitoring, error handling, retries, idempotency, backup, rollback, support, and ownership.
2. Run required regression, integration, user-acceptance, performance, recovery, and smoke tests.
3. Create and verify a secret-free backup.
4. Obtain explicit production-deployment and activation approval.
5. Deploy using controlled change procedures.
6. Verify production state and side effects with approved sanitized or controlled data.
7. Roll back if any release gate fails.

### 11. Handover

1. Deliver the approved workflow inventory, documentation, evidence, known limitations, backup, rollback, maintenance, and support records.
2. Review access, credentials by name and owner, monitoring, incident response, recovery, and change control.
3. Remove temporary access when authorized.
4. Obtain receiving-owner acceptance.

### 12. Case Study

1. Use actual project evidence only.
2. Separate verified technical results from unmeasured business outcomes.
3. Do not invent savings, client feedback, performance, or production outcomes.
4. Anonymize or obtain publication approval for real-client information.
5. Keep the case study draft until its evidence and publication gates are complete.

## Verification

- [ ] A project copy of [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]] exists.
- [ ] Discovery links to a completed project copy of [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]].
- [ ] Scope, requirements, architecture, risks, and acceptance gates are documented.
- [ ] Git and n8n checkpoints have evidence.
- [ ] DEV remained within its approved inactive and test-data boundary.
- [ ] Test results distinguish passed, failed, blocked, not-run, and deferred cases.
- [ ] Demo or client approval is separate from production approval.
- [ ] Real-client approvals precede credentials, side effects, activation, and production deployment.
- [ ] Deployment, handover, closure, and case-study claims are evidence-backed.

## Rollback

- Before build: return the project to planned or blocked status and preserve discovery records.
- During DEV: keep the workflow inactive, restore the last reviewed DEV version, and re-run affected tests.
- During deployment: follow the approved project rollback plan, stop side effects, restore the known-good version, and record the incident.
- Never delete workflows, credentials, records, or client evidence as a rollback shortcut without explicit authorization.

## Troubleshooting

- **Unclear requirements:** Return to discovery and record the blocking question.
- **Conflicting approvals:** Stop at the current safe phase until one authoritative decision is recorded.
- **Dirty Git state:** Isolate the project diff and preserve unrelated changes.
- **MCP incompatibility:** Record the missing node, version, or permission and revise the design only after approval.
- **Failed controlled test:** Stop dependent tests, preserve sanitized evidence, and request approval before fixing.
- **Missing production evidence:** Keep the workflow inactive and do not deploy or activate.
- **Credential value found in documentation:** Remove it from the project record, follow the applicable incident process, and rotate it through the approved credential owner when required.

## Related Notes

- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[06 - SOPs/n8n/Start a New Client Automation|Start a New Client Automation]]
- [[06 - SOPs/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[06 - SOPs/n8n/Client Automation Handover|Client Automation Handover]]
