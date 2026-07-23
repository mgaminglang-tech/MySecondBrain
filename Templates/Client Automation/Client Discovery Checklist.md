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

1. Duplicate this note into the relevant client project folder.
2. Rename the copy using the client or project name, for example: `Acme Lead Routing Discovery.md`.
3. Replace placeholders and complete the checklist during or immediately after the discovery call.
4. Record facts, decisions, assumptions, and unresolved questions separately.
5. Do not mark the discovery readiness gate until the required answers and approvals are documented.

> [!warning] Credential safety
> Never store passwords, API keys, access tokens, private keys, webhook secrets, database URLs containing credentials, or other secret values in Obsidian. Record only the credential name, owner, purpose, required permissions, environment, and access status. Store secret values in an approved password manager or credential vault.

## Discovery Details

- Client: `CLIENT_NAME`
- Project: `PROJECT_NAME`
- Meeting date: `YYYY-MM-DD`
- Interviewer:
- Participants:
- Discovery version:

## 1. Client and Company Information

- [ ] What is the client's legal or trading name?  
  **Answer:**
- [ ] What does the company do, and who are its customers?  
  **Answer:**
- [ ] Which department or business unit owns this process?  
  **Answer:**
- [ ] Where does the company operate, and which time zones or languages matter?  
  **Answer:**
- [ ] If the answer is vague, such as “we serve everyone,” who are the primary users for this automation?  
  **Primary users:**
- [ ] How many people will use, manage, or be affected by the automation?  
  **Number and roles:**

## 2. Business Problem

- [ ] What specific problem should the automation solve?  
  **Answer:**
- [ ] What happens today because this problem is not solved?  
  **Impact:**
- [ ] How often does the problem occur?  
  **Occurrences per day, week, or month:**
- [ ] What is the estimated cost in time, money, errors, or lost opportunities?  
  **Current measurable impact:**
- [ ] If the client says “the process is too slow,” how long does it take now, and what target time is acceptable?  
  **Current time:**  
  **Target time:**
- [ ] Why is this project important now?  
  **Reason and deadline:**

## 3. Current Manual Process

- [ ] Who starts the current process?  
  **Role or team:**
- [ ] What are the current steps from start to finish?  
  **Steps:**
- [ ] Which steps require copying, retyping, checking, approving, or sending information manually?  
  **Manual steps:**
- [ ] Which spreadsheets, forms, inboxes, tools, or documents are used?  
  **Current systems:**
- [ ] How long does each step normally take?  
  **Timing by step:**
- [ ] If the client says “someone checks it,” who checks it, what do they check, and how do they decide it passes?  
  **Checker, checks, and pass criteria:**
- [ ] Can the client provide a sanitized example of a completed process?  
  **Example reference or follow-up owner:**

## 4. Trigger and Workflow Steps

- [ ] What exact event should start the automation?  
  **Trigger:**
- [ ] Is the trigger a webhook, form submission, new record, email, schedule, manual action, or another event?  
  **Trigger type:**
- [ ] What steps should run after the trigger, in order?  
  **Expected workflow steps:**
- [ ] Which steps can run automatically, and which require human review or approval?  
  **Automatic steps:**  
  **Human steps:**
- [ ] Can the same event arrive more than once, and how should duplicates be handled?  
  **Duplicate rule:**
- [ ] If the client says “run it regularly,” what exact schedule, time zone, start time, and blackout periods apply?  
  **Schedule and time zone:**
- [ ] What event marks the workflow as successfully finished?  
  **Completion event:**

## 5. Inputs and Required Fields

- [ ] What data enters the workflow, and from which source?  
  **Input sources:**
- [ ] Which fields are required, optional, or conditionally required?  
  **Required:**  
  **Optional:**  
  **Conditional:**
- [ ] What format is expected for dates, names, phone numbers, currency, IDs, and files?  
  **Field formats:**
- [ ] What values are valid or invalid for each important field?  
  **Validation rules:**
- [ ] If the client says “basic contact details,” does that mean name, email, phone, company, country, consent, or something else?  
  **Exact fields:**
- [ ] What should happen when a required field is missing, blank, malformed, or inconsistent?  
  **Expected behavior:**
- [ ] Can sanitized sample inputs be provided for normal, invalid, and edge cases?  
  **Sample-data owner and due date:**

## 6. Outputs and Expected Results

- [ ] What should the workflow create, update, send, or return?  
  **Outputs:**
- [ ] Which system, table, folder, channel, inbox, or person receives each output?  
  **Destination by output:**
- [ ] What exact fields and format must each output contain?  
  **Output schema or example:**
- [ ] Who should receive notifications, and under which conditions?  
  **Recipients and rules:**
- [ ] If the client says “send a report,” what fields, file type, layout, recipients, and delivery schedule are required?  
  **Report specification:**
- [ ] How will the client confirm that an output is correct?  
  **Verification method:**

## 7. Business Rules and Decision Logic

- [ ] What conditions cause different workflow paths?  
  **Conditions and paths:**
- [ ] Which calculations, thresholds, priorities, categories, or mappings are required?  
  **Rules:**
- [ ] In what order should rules be evaluated?  
  **Rule priority:**
- [ ] Who can approve or change a business rule?  
  **Rule owner:**
- [ ] If the client says “high-value leads go to sales,” what exact value threshold, currency, sales destination, and fallback apply?  
  **Measurable rule:**
- [ ] What should happen when multiple rules match or no rule matches?  
  **Conflict and default behavior:**
- [ ] Can each critical rule be expressed as a testable `given / when / then` example?  
  **Examples:**

## 8. Tools and Integrations

- [ ] Which systems must connect to the automation?  
  **Systems:**
- [ ] What is each system's role: trigger, source, destination, approval, notification, or storage?  
  **Role by system:**
- [ ] Are separate DEV, STAGING, and PROD environments available?  
  **Environment details:**
- [ ] Does each system provide an API, webhook, native n8n node, email interface, file export, or database connection?  
  **Connection method:**
- [ ] Which account, workspace, base, database, table, form, folder, or channel must be used?  
  **Resource names or non-secret IDs:**
- [ ] If the client says “connect our CRM,” which CRM, plan, region, objects, fields, and API limits apply?  
  **Exact integration requirements:**
- [ ] Are vendor documentation, rate limits, sandbox access, or technical contacts available?  
  **References and owners:**

## 9. Access and Credentials

- [ ] Who owns each required account or integration?  
  **Owners:**
- [ ] Who is authorized to grant DEV and PROD access?  
  **Approvers:**
- [ ] What minimum permissions are required for each integration?  
  **Permission scopes:**
- [ ] Where will credentials be stored securely?  
  **Approved credential manager:**
- [ ] Are separate DEV and PROD credentials required?  
  **Credential separation plan:**
- [ ] If the client says “we will share the login,” can a dedicated service account or OAuth connection be used instead?  
  **Approved access method:**
- [ ] What is the access deadline, rotation policy, and revocation owner?  
  **Deadline and policy:**

> [!danger] Do not paste secret values here
> Use non-secret references such as `PROD - HubSpot - Lead Sync` or `Access pending from IT`.

## 10. Security, Privacy, and Sensitive Data

- [ ] What personal, financial, health, client, employee, or confidential data will be processed?  
  **Data categories:**
- [ ] Which data fields are sensitive, and are any prohibited from entering n8n or logs?  
  **Restricted fields:**
- [ ] Which privacy, regulatory, contractual, or internal policies apply?  
  **Requirements:**
- [ ] Where may data be stored or processed geographically?  
  **Approved regions:**
- [ ] How long should data, logs, files, and execution history be retained?  
  **Retention rules:**
- [ ] If the client says “the data is confidential,” what classification, access restrictions, encryption, masking, and deletion rules are required?  
  **Specific controls:**
- [ ] Who approves the security and privacy design before production use?  
  **Approver and evidence:**

## 11. Error Handling and Edge Cases

- [ ] What should happen when an integration is unavailable, slow, or rate-limited?  
  **Expected behavior:**
- [ ] Which failures should retry, how many times, and with what delay?  
  **Retry policy:**
- [ ] Which failures require an alert, manual review, or immediate stop?  
  **Escalation rules:**
- [ ] How should partial success be handled when some steps finish and later steps fail?  
  **Recovery rule:**
- [ ] What empty-data, duplicate, invalid-data, late-data, or out-of-order cases are expected?  
  **Known edge cases:**
- [ ] If the client says “just notify us if it breaks,” who is notified, through which channel, within what time, and with what details?  
  **Measurable alert requirement:**
- [ ] What is the safe manual recovery or replay process?  
  **Recovery owner and steps:**

## 12. Volume, Frequency, and Performance

- [ ] How many items are processed on an average and peak day, week, or month?  
  **Average volume:**  
  **Peak volume:**
- [ ] Are there seasonal spikes, campaigns, deadlines, or batch imports?  
  **Spike details:**
- [ ] How quickly must processing begin and finish?  
  **Maximum start delay:**  
  **Maximum completion time:**
- [ ] How many simultaneous events may occur?  
  **Expected concurrency:**
- [ ] What file sizes, record counts, or payload limits apply?  
  **Limits:**
- [ ] If the client says “near real time,” does that mean within 5 seconds, 1 minute, 5 minutes, or another target?  
  **Target response time:**
- [ ] What performance evidence will be accepted during testing?  
  **Load-test or timing criteria:**

## 13. Success Criteria and Acceptance Criteria

- [ ] What measurable business outcome defines success?  
  **Success metric and target:**
- [ ] What must work for the first release to be accepted?  
  **Acceptance requirements:**
- [ ] What error rate, processing time, accuracy, and uptime are acceptable?  
  **Thresholds:**
- [ ] Which test cases must pass before production approval?  
  **Required tests:**
- [ ] Who performs user acceptance testing and who signs off?  
  **Tester and approver:**
- [ ] If the client says “it should save time,” how many hours per week should be saved, and how will that be measured?  
  **Baseline, target, and measurement method:**
- [ ] What evidence will document acceptance: signed note, email, test record, or meeting approval?  
  **Acceptance evidence:**

## 14. Project Scope

- [ ] Which workflows, integrations, data fields, user roles, and environments are included?  
  **Included scope:**
- [ ] What is the minimum viable first release?  
  **MVP:**
- [ ] Which deliverables are required: n8n workflows, documentation, tests, training, deployment, or support?  
  **Deliverables:**
- [ ] How many workflow variants, forms, departments, brands, or regions are included?  
  **Included quantities:**
- [ ] If the client says “automate the whole process,” which exact start and end points define the boundary?  
  **Scope boundary:**
- [ ] What change-request process applies when new requirements appear?  
  **Change-control process:**

## 15. Out of Scope and Future Phases

- [ ] Which requests, systems, teams, regions, or features are explicitly excluded?  
  **Out of scope:**
- [ ] Which manual steps will remain manual in this phase?  
  **Remaining manual steps:**
- [ ] Which ideas belong to a future phase rather than the current delivery?  
  **Future phases:**
- [ ] What event or metric would justify adding a future feature?  
  **Future trigger:**
- [ ] If the client says “maybe add AI later,” what possible use case is being considered, and is it excluded from the current estimate?  
  **Future AI use case and current status:**
- [ ] Has the client acknowledged the out-of-scope list?  
  **Acknowledgement evidence:**

## 16. Timeline and Budget

- [ ] What is the desired completion date, and is it fixed or flexible?  
  **Date and flexibility:**
- [ ] Are there milestones for discovery, design, build, testing, approval, and launch?  
  **Milestones:**
- [ ] Which client dependencies could affect the schedule?  
  **Dependencies and due dates:**
- [ ] What budget range or approved spending limit applies?  
  **Budget:**
- [ ] Are software subscriptions, n8n hosting, API usage, and support costs included?  
  **Included and excluded costs:**
- [ ] If the client says “as soon as possible,” what business date matters, and what scope can be reduced to meet it?  
  **Required date and trade-off:**
- [ ] Who approves schedule or budget changes?  
  **Approver:**

## 17. Owners, Approvers, and Stakeholders

- [ ] Who is the client project owner and primary contact?  
  **Name and role:**
- [ ] Who owns the business process?  
  **Process owner:**
- [ ] Who owns each integration, dataset, and credential?  
  **Technical owners:**
- [ ] Who reviews security, privacy, legal, and compliance requirements?  
  **Reviewers:**
- [ ] Who approves scope, budget, UAT, production deployment, and workflow activation?  
  **Approver by decision:**
- [ ] If the client says “the team will approve it,” which named person has final authority, and what is the response deadline?  
  **Final approver and deadline:**
- [ ] Who must be informed but does not approve?  
  **Other stakeholders:**

## 18. Monitoring, Maintenance, and Support

- [ ] What workflow health, failures, delays, or business metrics must be monitored?  
  **Monitoring requirements:**
- [ ] Who receives alerts during business hours and outside business hours?  
  **Alert owners:**
- [ ] What support hours and response times are expected?  
  **Support window and SLA:**
- [ ] Who will investigate failures, replay data, update credentials, and maintain business rules?  
  **Maintenance roles:**
- [ ] How often should workflows, credentials, dependencies, and documentation be reviewed?  
  **Review schedule:**
- [ ] If the client says “we need ongoing support,” how many hours, what channels, which tasks, and what response targets are expected?  
  **Support definition:**
- [ ] What handover, training, runbook, and maintenance documentation is required?  
  **Handover deliverables:**

## 19. Risks and Blockers

- [ ] What technical, business, access, data-quality, security, vendor, or schedule risks are known?  
  **Risks:**
- [ ] Which missing decisions, samples, accounts, approvals, or dependencies block progress?  
  **Current blockers:**
- [ ] What is the likelihood and impact of each major risk?  
  **Risk rating:**
- [ ] Who owns each mitigation, and when is it due?  
  **Mitigation owners and dates:**
- [ ] If the client says “access should be fine,” who will confirm access, to which resources, and by what date?  
  **Access verification commitment:**
- [ ] What condition would require pausing or cancelling the project?  
  **Stop condition:**

## 20. Open Questions

- [ ] Have all uncertain statements and assumptions been converted into explicit questions?  
  **Unresolved items:**
- [ ] Does each open question have an owner and due date?  
  **Owners and dates:**
- [ ] Does any unanswered question affect scope, cost, timeline, security, or architecture?  
  **Impact:**
- [ ] If the answer is “we will decide later,” what is the latest decision date before work is blocked or rework becomes likely?  
  **Decision deadline:**

| ID | Open question | Owner | Due date | Impact if unresolved | Status |
|---|---|---|---|---|---|
| OQ-001 |  |  |  |  | open |

## 21. Meeting Summary

- [ ] What business problem and desired result were confirmed?  
  **Summary:**
- [ ] What key workflow, scope, and architecture decisions were made?  
  **Decisions:**
- [ ] What assumptions still require validation?  
  **Assumptions:**
- [ ] What risks, disagreements, or constraints were raised?  
  **Risks and constraints:**
- [ ] If participants described the goal differently, what wording did everyone agree to use?  
  **Agreed goal statement:**
- [ ] Was the summary reviewed with participants before ending the call?  
  **Review result:**

## 22. Agreed Next Steps

- [ ] What action will happen next?  
  **Next action:**
- [ ] Who owns each action, and when is it due?  
  **Owners and deadlines:**
- [ ] Which documents, samples, access approvals, or technical checks must the client provide?  
  **Client actions:**
- [ ] Which analysis, estimate, design, prototype, or follow-up will the automation team provide?  
  **Automation-team actions:**
- [ ] What is the date and purpose of the next meeting or decision point?  
  **Next meeting:**
- [ ] What measurable condition must be met before planning or building begins?  
  **Start condition:**

| Action | Owner | Due date | Evidence or deliverable | Status |
|---|---|---|---|---|
|  |  |  |  | open |

## Final Discovery Readiness Gate

Complete this gate before planning, estimating, or building the automation.

### Required Readiness Checks

- [ ] The business problem and desired outcome are specific and measurable.
- [ ] The current process and proposed workflow boundaries are documented.
- [ ] Trigger, workflow steps, inputs, outputs, and business rules are testable.
- [ ] Required integrations, environments, owners, and access paths are identified.
- [ ] Security, privacy, sensitive-data, and credential requirements are understood.
- [ ] Expected volume, performance, monitoring, and error handling are defined.
- [ ] Scope, exclusions, deliverables, timeline, and budget are sufficiently clear.
- [ ] Acceptance criteria, approvers, risks, blockers, and open questions are recorded.
- [ ] No passwords, API keys, tokens, secrets, or unredacted sensitive data are stored in this note.

### Decision

- [ ] **GO** — Requirements are sufficiently clear and approved to begin the next agreed phase.
- [ ] **CONDITIONAL GO** — Work may begin only on the stated safe items while listed conditions are resolved.
- [ ] **NO-GO** — Planning or building must not begin because critical information, access, approval, safety, scope, or feasibility is unresolved.

**Selected decision:**  
**Decision owner:**  
**Decision date:**  
**Evidence or approval reference:**  
**Conditions or blockers:**  
**Next review date:**
