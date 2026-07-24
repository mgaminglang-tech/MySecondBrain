---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - maintenance
---

# Maintenance Guide

## Purpose

Define operational ownership and safe change control for the accepted inactive DEV demo artifact. No live service currently exists, and production operations are not approved.

## Proposed Ownership

| Responsibility | Primary owner | Backup owner |
|---|---|---|
| Scope and business-rule approval | Project Owner | Automation Engineer |
| Workflow build and manual DEV tests | Automation Engineer | Project Owner |
| Scoring, status, and routing review | Project Owner | Automation Engineer |
| Execution-log retention review | Automation Engineer | Project Owner |
| Backup and simulated recovery review | Automation Engineer | Project Owner |
| Issue acceptance | Project Owner | Automation Engineer |

## DEV Maintenance

- Use dummy data only.
- Make changes in an inactive DEV workflow.
- Version scoring and routing changes.
- Re-run affected and regression cases in [[02 - Projects/Automation/Lead Qualification Practice/Test Plan|Test Plan]].
- Preserve a secret-free known-good export.
- Keep credential and external-node counts at zero.
- Retain DEV execution logs for seven days.
- Review results against the under-two-second target.

## STAGING and PROD

Not used in v0.1. Any future environment requires a separately approved v0.2 design.

## Proposed Monitoring

- Unexpected manual execution failures.
- Validation results and fallback-routing cases.
- Score and status distribution across dummy fixtures.
- Normalization injection warnings.
- Executions taking two seconds or more.
- Retention configuration drift.
- Any credential, external node, or activation drift.

## Suggested Routine

| Activity | Suggested frequency | Evidence |
|---|---|---|
| Review manual DEV failures and fallback routes | After each test session | Dummy execution references |
| Verify inactivity and zero credentials/external nodes | Before each test session | Review checklist |
| Verify seven-day retention | Before first test and monthly while in use | Settings evidence |
| Verify backup freshness | Before material change and at least every 24 hours during active development | Backup inventory |
| Review scoring and routing results | After each rule change | Test evidence |
| Simulate restore | Before v0.1 completion review | Restore evidence |

## Incident Response

1. Stop manual testing and keep the workflow inactive.
2. Preserve dummy-data evidence and note the affected version.
3. Confirm no credential, external node, write, or send was introduced.
4. Fix or restore in DEV and run affected regression cases.
5. Project Owner and Automation Engineer review before testing resumes.

## Deferred v0.2 Operations

Credential rotation, vendor monitoring, persistent duplicate review, external retries, delivery/storage reconciliation, live incident response, STAGING, and PROD operations are deferred.

## Demo and Production Boundary

- Demo maintenance scope: keep the workflow inactive, use dummy data only, preserve zero credentials/external nodes, and re-run relevant tests after changes.
- Major-change gate: run the 88-test Extended Regression Suite.
- Live-deployment gate: complete operational review, recovery evidence, client/owner approval, integration testing, production smoke testing, and production-specific monitoring and support ownership.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Credentials Checklist|Credentials Checklist]]
- [[02 - Projects/Automation/Lead Qualification Practice/Backup and Restore|Backup and Restore]]
- [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]]
- [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]]
