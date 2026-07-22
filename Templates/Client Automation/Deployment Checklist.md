---
type: checklist
status: draft
client: CLIENT_NAME
release: RELEASE_VERSION
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - deployment
---

# Deployment Checklist

## Release Details

- DEV workflow: `DEV - Client or Project - Workflow Name`
- PROD workflow: `PROD - Client or Project - Workflow Name`
- Release version:
- Deployment window:
- Operator:
- Reviewer:
- PROD approver:

## Pre-Deployment Approval Gate

- [ ] Scope and release version approved.
- [ ] DEV tests passed with evidence.
- [ ] Open defects and limitations accepted.
- [ ] Security and client-data review completed.
- [ ] Current PROD backup verified.
- [ ] Rollback threshold, owner, and steps documented.
- [ ] PROD credential names and resource IDs reviewed without exposing values.
- [ ] Smoke-test record and expected side effects approved.
- [ ] Monitoring and alert owner assigned.
- [ ] Explicit approval to modify PROD recorded.
- [ ] Explicit approval to activate PROD recorded.

Codex and MCP must not modify PROD unless the specific change is explicitly approved.

## Inactive Configuration Review

- [ ] PROD workflow remains inactive.
- [ ] Workflow name follows the PROD standard.
- [ ] Triggers and schedules are correct.
- [ ] Time zone is correct.
- [ ] Recipients and destinations are production-approved.
- [ ] Credentials follow `PROD - Service - Purpose`.
- [ ] Retry, timeout, idempotency, and error settings reviewed.
- [ ] Error workflow or alert path reviewed.
- [ ] Nodes and connections match the approved release.

## Controlled Activation

- [ ] Deployment window opened.
- [ ] Backup rechecked immediately before change.
- [ ] Approved change applied only.
- [ ] Activation performed by the authorized operator.
- [ ] Activation timestamp recorded.

## Smoke Test

- [ ] Approved test record used.
- [ ] Execution completed successfully.
- [ ] Expected side effects confirmed.
- [ ] No unexpected duplicate or external action occurred.
- [ ] Alerts and monitoring confirmed.
- [ ] Client or project owner accepted the result.

## Failure Handling and Rollback

- [ ] Failure threshold checked.
- [ ] Harmful processing can be contained.
- [ ] Last approved backup is available.
- [ ] Restore steps are understood.
- [ ] Reactivation requires approval.

## Release Record

- Outcome:
- Execution IDs:
- Rollback used:
- Remaining risks:
- Acceptance date:

## Related Notes

- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[Templates/Client Automation/Backup and Restore|Backup and Restore]]
- [[06 - SOPs/n8n/Promote DEV Workflow to PROD|Promote DEV Workflow to PROD]]
