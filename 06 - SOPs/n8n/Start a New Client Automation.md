---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - client-onboarding
---

# Start a New Client Automation

## Purpose

Start a client automation with approved scope, clear ownership, safe data practices, and traceable delivery records.

## When to Use

Use before building a new client workflow or materially expanding an existing automation.

## Requirements

- Named project owner and client approver
- Discovery contact and decision-making process
- Approved project documentation location
- Access to the client automation template suite
- Initial understanding of systems, data, risks, and expected outcomes

## Safety Considerations

- Do not request or record secrets in project notes.
- Use dummy or sanitized data during discovery and DEV.
- Do not promise deployment, testing, or outcomes before evidence exists.
- Codex and MCP must not modify PROD without explicit approval.

## Ownership and Approval Gates

| Gate | Owner | Evidence |
|---|---|---|
| Discovery complete | Project owner | Discovery notes and open questions |
| Scope approved | Client approver | Included and excluded scope |
| Requirements approved | Project owner and client approver | Acceptance criteria and data rules |
| Development authorized | Project owner | DEV plan and access readiness |

## Procedure

1. Create the project from [[Templates/Client Automation/Client Automation Project|Client Automation Project]].
2. Record stakeholders, owners, communication channels, and approval authority.
3. Complete discovery for the current process, pain points, volumes, timing, exceptions, and desired outcome.
4. Define included and excluded scope.
5. Complete [[Templates/Client Automation/Requirements|Requirements]] with acceptance criteria and non-functional requirements.
6. Map systems, data, triggers, outputs, and failure paths using [[Templates/Client Automation/Architecture|Architecture]].
7. Identify required credentials by name and owner using [[Templates/Client Automation/Credentials Checklist|Credentials Checklist]]. Never record values.
8. Define DEV workflow names as `DEV - Client or Project - Workflow Name`.
9. Decide whether optional STAGING adds value; document the decision.
10. Create the development, test, error-handling, backup, deployment, rollback, maintenance, limitations, and handover plans.
11. Obtain scope and requirements approval before building.

## Verification

- [ ] Owners and approvers are named.
- [ ] Discovery and scope are documented.
- [ ] Requirements and acceptance criteria are approved.
- [ ] Data classification and sanitization approach are recorded.
- [ ] DEV credential requirements are identified without secret values.
- [ ] Risks, failure paths, and rollback expectations are documented.
- [ ] Development authorization is recorded.

## Failure Handling

If scope, ownership, data permission, or access is unclear, pause development and record the blocker. Do not compensate by guessing requirements or using production access.

## Rollback

Before development begins, rollback means placing the project on hold, revoking unnecessary temporary access, and preserving approved discovery records. Do not delete client records without approval.

## Troubleshooting

- **Conflicting requirements:** Record the conflict and obtain one authoritative decision.
- **Missing approver:** Keep the project in planned or blocked status.
- **Credential requested in notes:** Replace it with a placeholder such as `YOUR_API_KEY` and direct the owner to the approved credential store.

## Related Notes

- [[03 - Areas/Automation Operations/Automation Operations|Automation Operations]]
- [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]]
- [[Templates/Client Automation/Development Plan|Development Plan]]
- [[06 - SOPs/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
