---
type: project-note
status: draft
client: CLIENT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - maintenance
---

# Maintenance Guide

## Purpose

Define ongoing ownership, monitoring, maintenance, incident, backup, and change-control responsibilities.

## Service Ownership

| Responsibility | Primary owner | Backup owner | Escalation path |
|---|---|---|---|
| Workflow operations |  |  |  |
| Credentials |  |  |  |
| Client data |  |  |  |
| Incident response |  |  |  |
| Vendor dependencies |  |  |  |

## Monitoring

- Success indicator:
- Failure indicator:
- Alert destination by role:
- Review frequency:
- Execution-data retention:
- Reconciliation method:

## Routine Maintenance

| Activity | Frequency | Owner | Evidence |
|---|---|---|---|
| Review failed executions |  |  |  |
| Verify error alerts |  |  |  |
| Review credential expiry |  |  |  |
| Verify backup freshness |  |  |  |
| Review dependency changes |  |  |  |
| Review data retention |  |  |  |

## Change Control

1. Record the requested change and owner.
2. Reproduce or build in DEV with sanitized data and test credentials.
3. Update tests, issues, limitations, backup, and rollback plans.
4. Obtain explicit approval before modifying PROD.
5. Back up PROD, deploy in a controlled window, smoke test, and monitor.

Codex and MCP must not modify PROD without explicit approval.

## Credential Maintenance

- Naming: `DEV - Service - Purpose` and `PROD - Service - Purpose`
- Rotation owner:
- Review schedule:
- Revocation process:
- Related SOP: [[06 - SOPs/n8n/Rotate an API Credential|Rotate an API Credential]]

## Backup and Recovery

- Backup location reference:
- Backup frequency or event trigger:
- Restore owner:
- Last verified backup:
- Restore test status: not-tested

## Incident Response

- Severity definitions:
- Containment authority:
- Communication owner:
- Recovery target:
- Related SOP: [[06 - SOPs/n8n/Handle a Failed Production Workflow|Handle a Failed Production Workflow]]

## Known Limitations

- [[Templates/Client Automation/Known Limitations|Known Limitations]]

## Change History

| Date | Version | Environment | Change | Approver | Result |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

## Related Notes

- [[Templates/Client Automation/Client Handover|Client Handover]]
- [[Templates/Client Automation/Backup and Restore|Backup and Restore]]
- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
