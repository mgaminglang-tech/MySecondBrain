---
type: client-discovery-checklist
status: template
client: CLIENT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - discovery
  - checklist
---

# Client Discovery Checklist

## How to Use This Template

1. Duplicate this core checklist into every automation project folder.
2. Complete it during or immediately after discovery.
3. Record facts, decisions, assumptions, and open questions separately.
4. Add the optional discovery modules only when their topics apply.
5. Select a readiness decision only when its evidence is documented.

Do not record passwords, API keys, tokens, credential values, or unredacted sensitive data.

## Discovery Record

- Client: `CLIENT_NAME`
- Project: `PROJECT_NAME`
- Meeting date: `YYYY-MM-DD`
- Interviewer:
- Participants:
- Project owner:
- Discovery version:

## 1. Client and Project Identity

- [ ] What does the client do, and which team owns this process?  
  **Answer:**
- [ ] Who uses, manages, approves, or is affected by the process?  
  **Answer:**
- [ ] Which locations, time zones, languages, departments, brands, or regions affect the project?  
  **Answer:**

## 2. Business Problem

- [ ] What specific problem should the automation solve?  
  **Answer:**
- [ ] What measurable impact does the current problem create in time, cost, errors, delays, or lost opportunities?  
  **Baseline:**
- [ ] Why is the project needed now, and what business date or event matters?  
  **Reason:**
- [ ] What outcome would make the project worthwhile?  
  **Desired result:**

## 3. Current Manual Process

- [ ] Who starts the process, and what are the steps from start to finish?  
  **Steps:**
- [ ] Which steps require manual entry, checking, approval, copying, or communication?  
  **Manual work:**
- [ ] Which forms, inboxes, spreadsheets, tools, documents, or teams are involved?  
  **Current systems:**
- [ ] How long does the process take, and where do delays or errors occur?  
  **Timing and failure points:**
- [ ] Can the client provide a sanitized example of a completed process?  
  **Example reference or owner:**

## 4. Trigger and Workflow Boundary

- [ ] What exact event starts the workflow?  
  **Trigger:**
- [ ] Is it manual, scheduled, webhook-based, email-based, record-based, form-based, or another type?  
  **Trigger type and schedule:**
- [ ] What steps should happen in order after the trigger?  
  **Proposed steps:**
- [ ] Which steps remain human-reviewed or manually approved?  
  **Human steps:**
- [ ] What event or output marks successful completion?  
  **Completion condition:**

## 5. Inputs

- [ ] What data enters the workflow, and from which source?  
  **Input sources:**
- [ ] Which fields are required, optional, or conditionally required?  
  **Field list:**
- [ ] What types, formats, ranges, enums, file limits, and normalization rules apply?  
  **Input contract:**
- [ ] What values are invalid, and what should happen when data is missing or malformed?  
  **Validation behavior:**
- [ ] Are sanitized normal, invalid, boundary, duplicate, and edge-case samples available?  
  **Fixture owner and reference:**

## 6. Outputs

- [ ] What should the workflow create, update, send, prepare, or return?  
  **Outputs:**
- [ ] Who or what receives each output?  
  **Destinations:**
- [ ] What exact fields, formats, filenames, layouts, or schemas are required?  
  **Output contract:**
- [ ] Which outputs require human review or approval before release?  
  **Approval rule:**
- [ ] How will the client verify that each output is correct?  
  **Verification method:**

## 7. Business Rules

- [ ] What calculations, thresholds, priorities, categories, mappings, or routing rules apply?  
  **Rules:**
- [ ] In what order are rules evaluated?  
  **Priority:**
- [ ] What happens when multiple rules match or none matches?  
  **Conflict and fallback behavior:**
- [ ] Who owns and approves rule changes?  
  **Rule owner:**
- [ ] Can each critical rule be written as a testable example?  
  **Examples:**

## 8. Errors and Edge Cases

- [ ] Which empty, invalid, duplicate, late, out-of-order, or partial cases are expected?  
  **Cases:**
- [ ] What should safely stop, continue, fall back, or require human review?  
  **Behavior:**
- [ ] What should happen if a workflow step or external dependency fails?  
  **Failure expectation:**
- [ ] Which failures must be visible to a person?  
  **Notification requirement:**
- [ ] What manual correction or replay path is acceptable?  
  **Recovery expectation:**

Detailed retry, timeout, monitoring, incident, reconciliation, and recovery questions belong in [[Templates/Client Automation/Client Discovery - Operations and Support Module|Client Discovery - Operations and Support Module]].

## 9. Measurable Success and Acceptance

- [ ] What measurable business result defines success?  
  **Metric and target:**
- [ ] What must work for version one to be accepted?  
  **Acceptance criteria:**
- [ ] Which exact tests or scenarios must pass?  
  **Required evidence:**
- [ ] Who reviews the evidence and records acceptance?  
  **Tester and approver:**

## 10. Version-One Scope

- [ ] What start and end points define version one?  
  **Boundary:**
- [ ] Which workflows, data, teams, environments, and deliverables are included?  
  **Included scope:**
- [ ] What is the smallest useful first release or demo?  
  **Minimum release:**
- [ ] Which manual steps intentionally remain?  
  **Remaining manual work:**
- [ ] How will new requests be evaluated and approved?  
  **Change-control process:**

## 11. Out of Scope and Future Work

- [ ] Which systems, users, regions, features, or outcomes are excluded?  
  **Out of scope:**
- [ ] Which ideas belong to a future phase?  
  **Future work:**
- [ ] What event, metric, or approval would trigger reconsideration?  
  **Trigger:**
- [ ] Has the scope owner acknowledged these exclusions and deferrals?  
  **Evidence:**

## 12. Stakeholders and Approvers

- [ ] Who is the project owner and primary contact?  
  **Owner:**
- [ ] Who owns the business process and technical implementation?  
  **Owners:**
- [ ] Who approves scope, requirements, architecture, DEV build, testing, and demo acceptance?  
  **Approvers:**
- [ ] If production is possible, who may approve credentials, external side effects, deployment, and activation?  
  **Production approvers:**
- [ ] Who must be informed but does not approve?  
  **Stakeholders:**

## 13. Timeline and Constraints

- [ ] What completion date, milestones, or decision deadlines matter?  
  **Timeline:**
- [ ] Which client actions, samples, access decisions, or dependencies affect the schedule?  
  **Dependencies:**
- [ ] What budget, subscription, hosting, API-usage, or support constraints apply?  
  **Constraints:**
- [ ] Who approves timeline, budget, or scope changes?  
  **Approver:**

## 14. Open Questions and Risks

- [ ] Are uncertain statements converted into explicit questions with owners and due dates?  
  **Open questions:**
- [ ] Which unanswered questions could change scope, cost, timeline, security, architecture, or feasibility?  
  **Impact:**
- [ ] What known risks or blockers could pause or cancel the project?  
  **Risks and stop conditions:**

| ID | Open question, risk, or blocker | Owner | Due date | Impact | Status |
|---|---|---|---|---|---|
| OQ-001 |  |  |  |  | open |

## 15. Meeting Summary and Next Steps

- [ ] Record the agreed problem, outcome, scope, decisions, assumptions, and constraints.  
  **Summary:**
- [ ] Record the next action, owner, due date, and required evidence.  
  **Next action:**
- [ ] Record the next meeting or decision point.  
  **Next review:**

## Optional Discovery Modules

- [[Templates/Client Automation/Client Discovery - Integrations and Security Module|Client Discovery - Integrations and Security Module]] — Use when external tools, APIs, webhooks, credentials, multiple environments, sensitive data, or security requirements are involved.
- [[Templates/Client Automation/Client Discovery - Operations and Support Module|Client Discovery - Operations and Support Module]] — Use when production, performance, monitoring, recovery, maintenance, support, training, or ongoing ownership is in scope.

Duplicate only the relevant modules into the project folder and link their approval gates here.

## Discovery Readiness Gate

- [ ] Client identity, business problem, current process, trigger, inputs, outputs, rules, errors, and version-one scope are sufficiently clear.
- [ ] Measurable acceptance criteria, timeline, owners, approvers, open questions, risks, and next action are documented.
- [ ] Required optional modules are complete, or their absence is justified.
- [ ] No secret values or unredacted sensitive data are stored in this note.

### Decision

- [ ] **GO** — The next approved phase may begin.
- [ ] **CONDITIONAL GO** — Only stated safe work may begin while documented conditions are resolved.
- [ ] **NO-GO** — Critical scope, ownership, approval, safety, data, access, or feasibility issues block progress.

**Selected decision:**  
**Decision owner:**  
**Decision date:**  
**Evidence:**  
**Conditions or blockers:**  
**Next review date:**

## Related Notes

- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- [[Templates/Client Automation/Client Discovery - Integrations and Security Module|Client Discovery - Integrations and Security Module]]
- [[Templates/Client Automation/Client Discovery - Operations and Support Module|Client Discovery - Operations and Support Module]]
