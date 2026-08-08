---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Promote DEV Workflow to PROD

## Purpose

Promote an approved n8n release candidate through a controlled, observable, and reversible production change.

## Preconditions

- The release candidate and version are approved and supported by applicable DEV evidence.
- Known limitations and not-run tests are disclosed.
- A recovery-ready backup, rollback condition, rollback owner, smoke-test plan, deployment window, and monitoring owner are defined.
- The exact production modification and activation or publication are explicitly approved.

## Procedure

1. Freeze the approved release candidate and record its version and change summary.
2. Verify the current production backup under [[Backup and Recovery Standard]].
3. Confirm the production workflow remains separate from DEV and inactive during configuration review.
4. Replace DEV credential and resource references with approved production references under [[Credential and Secrets Management Standard]] without exposing values.
5. Review triggers, schedules, time zones, recipients, URLs, data targets, retries, timeouts, error handling, and downstream side effects.
6. Confirm the approved deployment window, operator, smoke-test steps, monitoring period, rollback threshold, and rollback owner.
7. Apply only the approved release and revalidate node configuration, connections, credential references, and workflow settings.
8. Obtain the recorded activation or publication approval.
9. Activate during the approved window and run the smallest safe smoke test.
10. Verify expected execution state, side effects, alerts, and downstream records.
11. Monitor the defined initial production period and roll back when the documented threshold is reached.
12. Record release version, operator, approver, timestamps, smoke-test result, monitoring result, production handoff state, and remaining risks.

## Verification

- Release identity, environment, backup, credentials, and resource references are correct.
- Configuration review occurred while the workflow was inactive.
- Activation or publication approval is recorded.
- The smoke test produced only expected effects.
- Monitoring and rollback ownership are active.
- The final production and handoff state is documented.

## Stop / Escalate When

- The backup is unreadable or not recovery-ready.
- Approval, release identity, credential mapping, destination, or rollback authority is ambiguous.
- Smoke testing creates unexpected effects or reaches a rollback threshold.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Backup and Recovery Standard]]
- [[Credential and Secrets Management Standard]]
- [[30 Systems/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]]

## Do

- Treat configuration, activation, smoke testing, and handoff as distinct verified steps.

## Don’t

- Rename or convert the only DEV workflow into PROD.
- Troubleshoot beyond the approved production incident scope.
