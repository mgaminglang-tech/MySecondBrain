---
type: project
status: planned
priority: medium
client: CLIENT_NAME
owner: PROJECT_OWNER
version: v0.1.0
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - project
  - client-automation
  - n8n
---

# CLIENT_NAME - AUTOMATION_NAME

## Objective

Describe the measurable client outcome.

## Files to Duplicate

### Always

- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- This [[Templates/Client Automation/Client Automation Project|Client Automation Project]] overview
- Core project documents: [[Templates/Client Automation/Requirements|Requirements]], [[Templates/Client Automation/Architecture|Architecture]], [[Templates/Client Automation/Development Plan|Development Plan]], [[Templates/Client Automation/Test Plan|Test Plan]], [[Templates/Client Automation/Test Results|Test Results]], and [[Templates/Client Automation/Issues and Fixes|Issues and Fixes]]
- Delivery and evidence documents applicable to the lifecycle: [[Templates/Client Automation/Credentials Checklist|Credentials Checklist]], [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]], [[Templates/Client Automation/Backup and Restore|Backup and Restore]], [[Templates/Client Automation/Maintenance Guide|Maintenance Guide]], [[Templates/Client Automation/Known Limitations|Known Limitations]], [[Templates/Client Automation/Client Handover|Client Handover]], and [[Templates/Client Automation/Case Study|Case Study]]

### When Relevant

- [[Templates/Client Automation/Client Discovery - Integrations and Security Module|Client Discovery - Integrations and Security Module]] — Add when external tools, credentials, APIs, webhooks, multiple environments, sensitive data, or security requirements apply.
- [[Templates/Client Automation/Client Discovery - Operations and Support Module|Client Discovery - Operations and Support Module]] — Add when production, performance, monitoring, recovery, maintenance, support, training, or post-launch ownership applies.

Duplicate files into the project folder before use. Keep detailed module content in the module copies rather than repeating it here.

## Discovery

- Current process:
- Pain points:
- Stakeholders:
- Volumes and timing:
- Exceptions:
- Open questions:

## Scope

### Included

-

### Not Included

-

## Project Workflow

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]. Use the project copy of [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]] to record gate evidence, approvals, blockers, owners, and next actions.

Detailed behavior belongs in Requirements and Architecture. Executable expectations and evidence belong in Test Plan and Test Results.

## Environment Standards

- DEV workflow: `DEV - Client or Project - Workflow Name`
- Optional STAGING: define only when required.
- PROD workflow: `PROD - Client or Project - Workflow Name`
- DEV credential: `DEV - Service - Purpose`
- PROD credential: `PROD - Service - Purpose`

DEV uses dummy or sanitized data and approved non-production access. Real-client credentials, external side effects, activation, and production deployment require separate explicit approvals.

## Approvals

| Gate | Approver | Date | Evidence |
|---|---|---|---|
| Scope |  |  |  |
| Requirements |  |  |  |
| DEV test completion |  |  |  |
| Production deployment, if applicable |  |  |  |
| Handover |  |  |  |
| Archive |  |  |  |

## Next Action

- [ ]

## Related Operations

- [[03 - Areas/Automation Operations/Automation Operations|Automation Operations]]
- [[06 - SOPs/n8n/Start a New Client Automation|Start a New Client Automation]]
