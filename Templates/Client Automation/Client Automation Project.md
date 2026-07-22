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

1. Discovery and scope → [[Templates/Client Automation/Requirements|Requirements]]
2. System and data design → [[Templates/Client Automation/Architecture|Architecture]]
3. Access planning → [[Templates/Client Automation/Credentials Checklist|Credentials Checklist]]
4. DEV implementation → [[Templates/Client Automation/Development Plan|Development Plan]]
5. Test definition → [[Templates/Client Automation/Test Plan|Test Plan]]
6. Evidence capture → [[Templates/Client Automation/Test Results|Test Results]]
7. Defect tracking → [[Templates/Client Automation/Issues and Fixes|Issues and Fixes]]
8. Backup and recovery → [[Templates/Client Automation/Backup and Restore|Backup and Restore]]
9. PROD approval and release → [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
10. Operations → [[Templates/Client Automation/Maintenance Guide|Maintenance Guide]]
11. Accepted constraints → [[Templates/Client Automation/Known Limitations|Known Limitations]]
12. Ownership transfer → [[Templates/Client Automation/Client Handover|Client Handover]]
13. Evidence-based summary → [[Templates/Client Automation/Case Study|Case Study]]

## Environment Standards

- DEV workflow: `DEV - Client or Project - Workflow Name`
- Optional STAGING: define only when required by project risk or client process.
- PROD workflow: `PROD - Client or Project - Workflow Name`
- DEV credential: `DEV - Service - Purpose`
- PROD credential: `PROD - Service - Purpose`

DEV uses dummy or sanitized data and test credentials. PROD requires explicit approval, backup, rollback planning, smoke testing, and controlled activation. Codex and MCP must not modify PROD without explicit approval.

## Error Handling

- Failure workflow or alert path:
- Retry policy:
- Idempotency or duplicate prevention:
- Manual recovery owner:
- Escalation threshold:

## Approvals

| Gate | Approver | Date | Evidence |
|---|---|---|---|
| Scope |  |  |  |
| Requirements |  |  |  |
| DEV test completion |  |  |  |
| PROD deployment |  |  |  |
| Handover |  |  |  |

## Next Action

- [ ] 

## Related Operations

- [[03 - Areas/Automation Operations/Automation Operations|Automation Operations]]
- [[06 - SOPs/n8n/Start a New Client Automation|Start a New Client Automation]]
