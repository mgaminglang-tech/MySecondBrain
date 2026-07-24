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

1. Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].
2. Use project documents for detailed rules and this checklist only for lifecycle gates.
3. Complete a gate only when its required evidence and approval exist.
4. Keep demo completion separate from production readiness and archive readiness.

> [!danger] Approval boundary
> This practice project has no production approval. Credentials, external side effects, activation, integrations, and production deployment require separate explicit approval.

## Project Record

- Client: Demo Sales Company
- Project: Lead Qualification Practice
- Project folder: 02 - Projects/Automation/Lead Qualification Practice/
- Project owner: Mervin
- Automation engineer: Automation Engineer role documented; individual assignment not recorded
- Client approver: Project Owner role documented; final client/owner approval not recorded
- Current phase: demo-closure
- Project status: demo-complete
- Production ready: false
- DEV workflow: DEV - Demo Sales Company - Lead Qualification Practice - v0.1
- Workflow ID: Or7VHPFQakcY3l0Q
- STAGING workflow: not used
- PROD workflow: not approved
- Updated: 2026-07-24

## 1. Discovery Completed

- [ ] Gate complete
- **Evidence:** Business problem, desired outcome, assumptions, risks, and dummy-data scope are documented in [[02 - Projects/Automation/Lead Qualification Practice/Lead Qualification Practice Overview|Lead Qualification Practice Overview]] and [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]]. No project discovery-checklist copy or formal discovery decision is recorded.
- **Approval status:** Deferred for any future v0.2 discovery.
- **Blocker status:** Not a blocker for the accepted demo; required before a materially expanded future scope.
- **Owner:** Mervin
- **Next action:** No current demo action.

## 2. Scope Confirmed

- [x] Gate complete
- **Evidence:** The inactive, credential-free, dummy-only v0.1 boundary, exclusions, deliverables, DEV environment, and v0.2 deferrals are documented in [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]].
- **Approval status:** Approved for the controlled v0.1 demo only.
- **Blocker status:** No demo blocker; production scope is not approved.
- **Owner:** Mervin
- **Next action:** No current demo action.

## 3. Requirements Approved

- [x] Gate complete
- **Evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]] defines executable inputs, outputs, validation, scoring, routing, errors, non-functional assumptions, and demo acceptance criteria.
- **Approval status:** Approved for the controlled v0.1 demo only.
- **Blocker status:** No demo blocker; production requirements remain deferred.
- **Owner:** Mervin
- **Next action:** Reopen only for an approved v0.2 or major change.

## 4. Architecture Approved

- [x] Gate complete
- **Evidence:** [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] records the linear ten-node design, environments, data flow, credential-free hashing, inert payloads, side-effect boundaries, and deferrals.
- **Approval status:** Approved for the inactive v0.1 DEV demo only.
- **Blocker status:** No demo blocker; no STAGING or PROD architecture is approved.
- **Owner:** Mervin
- **Next action:** Reopen only for an approved v0.2 or production design.

## 5. Pre-development Review

- [ ] Gate complete
- **Evidence:** Requirements, architecture, risks, test coverage, and blockers were reviewed and resolved or deferred, but no formal GO, CONDITIONAL GO, or NO-GO review record is stored in the project folder.
- **Approval status:** Historical formal decision not recorded.
- **Blocker status:** Not a blocker for the completed demo; a new review is required before future development.
- **Owner:** Mervin
- **Next action:** Deferred until a future development phase is approved.

## 6. Git Checkpoint

- [ ] Gate complete
- **Evidence:** No project-scoped pre-build Git checkpoint, recovery point, or no-commit decision is recorded.
- **Approval status:** Not recorded.
- **Blocker status:** Pending the archive-versus-v0.2 decision; archive readiness still requires the applicable Git gate.
- **Owner:** Mervin
- **Next action:** Perform the appropriate scoped Git review only after the next phase is selected and separately authorized.

## 7. Read-only MCP Audit

- [ ] Gate complete
- **Evidence:** The implemented node availability, compatibility, inactive state, credential count, and safety boundaries are documented, but a distinct read-only audit record with connectivity, version, naming-conflict evidence, and a formal conclusion is not stored in the project folder.
- **Approval status:** Historical formal audit conclusion not recorded.
- **Blocker status:** Not a blocker for the completed demo; required before a future environment-dependent build.
- **Owner:** Mervin
- **Next action:** Deferred until a future workflow version is approved.

## 8. Inactive DEV Build

- [x] Gate complete
- **Evidence:** Workflow Or7VHPFQakcY3l0Q uses the approved ten-node design, remains inactive, uses dummy data, has no credentials or external integrations, and passed node and workflow validation. See [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]] and [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]].
- **Approval status:** Authorized and completed for inactive DEV v0.1 only.
- **Blocker status:** No demo blocker; activation and production remain unapproved.
- **Owner:** Mervin
- **Next action:** Keep the workflow inactive unless a separate phase is approved.

## 9. Core Release Suite

- [x] Gate complete
- **Evidence:** The 25-test Core Release Suite passed with 25 passed, 0 failed, and 0 blocked; temporary pin data was cleared; the workflow remained inactive and unchanged. Testing-stop behavior was required and evidenced by the two recorded runtime defects before TC-001 passed. See [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]] and [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]].
- **Approval status:** Accepted as the controlled demo gate.
- **Blocker status:** No demo blocker; 88 Extended Regression tests remain not run and ten v0.2 tests remain deferred.
- **Owner:** Mervin
- **Next action:** Extended Regression is deferred until production consideration or a major workflow change.

## 10. Demo or Client Approval

- [ ] Gate complete
- **Evidence:** Verified demo scope, the accepted Core Release Suite, limitations, and deferrals are documented. A named approver, approval date, and next-phase authorization are not recorded.
- **Approval status:** Demo status is recorded as demo-complete; formal client or owner acceptance evidence is unavailable.
- **Blocker status:** Pending decision for archive readiness or continuation.
- **Owner:** Mervin
- **Next action:** Use the authoritative project decision below.

## 11. Production Review, When Applicable

- [ ] Gate complete or not applicable
- **Evidence:** Production requirements, credentials, integrations, recovery, monitoring, support, and production tests are intentionally outside v0.1.
- **Approval status:** Not applicable for this demo; production readiness is not approved.
- **Blocker status:** Deferred unless production is separately proposed.
- **Owner:** Mervin
- **Next action:** No current demo action.

## 12. Deployment

- [ ] Gate complete or not applicable
- **Evidence:** No credential assignment, external side effect, activation, deployment, production smoke test, or production state exists.
- **Approval status:** Not applicable for this demo; deployment and activation are not approved.
- **Blocker status:** Deferred unless a separate production phase is authorized.
- **Owner:** Mervin
- **Next action:** Keep the DEV workflow inactive.

## 13. Handover

- [ ] Gate complete
- **Evidence:** Demo documentation, test evidence, limitations, lessons, and environment status are available. No receiving owner, access transfer, operational walkthrough, support acceptance, or formal handover exists.
- **Approval status:** Not applicable for the controlled practice demo.
- **Blocker status:** Not a demo blocker; full operational handover would require a separately approved live scope.
- **Owner:** Mervin
- **Next action:** No current demo action.

## 14. Archive Readiness

- [ ] Gate complete
- **Evidence:** Status, phase, owner, production readiness, test evidence, and known limitations are documented. Archive-versus-v0.2 selection, applicable Git evidence, and owner archive approval remain outstanding.
- **Approval status:** Pending decision.
- **Blocker status:** The archive-versus-v0.2 decision is unresolved.
- **Owner:** Mervin
- **Next action:** See the authoritative project next action below.

## Next Action

Decide whether to archive the demo project or continue with v0.2.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Lead Qualification Practice Overview|Lead Qualification Practice Overview]]
- [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]]
- [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]]
- [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]]
- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
