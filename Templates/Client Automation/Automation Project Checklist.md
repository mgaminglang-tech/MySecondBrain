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

1. Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].
2. Duplicate this checklist into every automation project folder.
3. Use project documents for detailed rules; use this checklist only for lifecycle gates.
4. Complete a gate only when its required evidence and approval exist.

> [!danger] Real-client approval boundary
> Credentials, external side effects, activation, and production deployment require separate explicit approvals. Demo approval does not authorize production.

## Project Record

- Client: `CLIENT_NAME`
- Project: `PROJECT_NAME`
- Project folder:
- Project owner:
- Automation engineer:
- Client approver:
- Current phase:
- Project status: planned
- Production ready: false
- DEV workflow:
- STAGING workflow or `not used`:
- PROD workflow or `not approved`:
- Updated:

## 1. Discovery Completed

- [ ] Gate complete
- **Required evidence:** Completed project copy of [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] and applicable discovery modules; GO, CONDITIONAL GO, or NO-GO decision.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 2. Scope Confirmed

- [ ] Gate complete
- **Required evidence:** Version-one boundary, included and excluded scope, deliverables, environments, dependencies, change control, and scope approval.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 3. Requirements Approved

- [ ] Gate complete
- **Required evidence:** Approved `Requirements.md` with executable inputs, outputs, validation, business rules, errors, non-functional requirements, and acceptance criteria.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 4. Architecture Approved

- [ ] Gate complete
- **Required evidence:** Approved `Architecture.md` with environments, workflow structure, data flow, integrations, credentials by reference, side effects, failure behavior, and deferrals.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 5. Pre-development Review

- [ ] Gate complete
- **Required evidence:** Read-only review result; conflicts, missing decisions, risks, blockers, and DEV authorization recorded.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 6. Git Checkpoint

- [ ] Gate complete
- **Required evidence:** Repository status and scoped diff reviewed; unrelated changes preserved; authorized commit or documented no-commit decision recorded.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 7. Read-only MCP Audit

- [ ] Gate complete
- **Required evidence:** Connectivity, version, nodes, compatibility, naming conflicts, environment, and safety findings; GO, CONDITIONAL GO, or NO-GO conclusion.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 8. Inactive DEV Build

- [ ] Gate complete
- **Required evidence:** Workflow ID and version; approved node and connection inventory; validation evidence; inactive state; credentials and external-node status.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 9. Core Release Suite

- [ ] Gate complete
- **Required evidence:** Approved test IDs, exact expected and actual results, execution evidence, totals, defect records, cleanup status, and final inactive workflow state.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 10. Demo or Client Approval

- [ ] Gate complete
- **Required evidence:** Verified demo scope, accepted test gate, disclosed limitations and deferrals, approver, date, decision, and authorized next phase.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 11. Production Review, When Applicable

- [ ] Gate complete or not applicable
- **Required evidence:** Production requirements, security, privacy, credentials, integrations, tests, backup, rollback, monitoring, recovery, support, ownership, and explicit readiness decision.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 12. Deployment

- [ ] Gate complete or not applicable
- **Required evidence:** Explicit credential, side-effect, deployment, and activation approvals; release and smoke-test evidence; production state and rollback result.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 13. Handover

- [ ] Gate complete
- **Required evidence:** Current workflow and document inventory; access and credential ownership; monitoring, recovery, maintenance, support, training, walkthrough, and acceptance evidence.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## 14. Archive Readiness

- [ ] Gate complete
- **Required evidence:** Final status, phase, owner, production readiness, completed or deferred next action, preserved evidence, known limitations, clean Git state, and owner archive approval.
- **Approval status:**
- **Blocker status:**
- **Owner:**
- **Next action:**

## Related Notes

- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[Templates/Client Automation/Client Discovery - Integrations and Security Module|Client Discovery - Integrations and Security Module]]
- [[Templates/Client Automation/Client Discovery - Operations and Support Module|Client Discovery - Operations and Support Module]]
- [[Templates/Client Automation/Client Automation Project|Client Automation Project]]
