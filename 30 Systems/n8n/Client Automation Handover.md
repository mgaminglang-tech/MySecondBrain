---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Client Automation Handover

## Purpose

Transfer an n8n automation with a verified operating state, clear ownership, usable recovery information, and accepted limitations.

## Preconditions

- The delivery owner, receiving owner, acceptance authority, support boundary, and applicable release evidence are known.
- Current workflow, dependency, backup, monitoring, and limitation information is available.

## Procedure

1. Record each workflow’s name or reference, environment, version, owner, and current activation state.
2. Link the current architecture, requirements, release evidence, decisions, known issues, and verified test results.
3. Document triggers, schedules, inputs, outputs, dependencies, downstream systems, expected operating volume, and manual steps.
4. Record credential names, owners, environment, access-request process, expiry or rotation responsibility, and minimum permissions without values.
5. Confirm the current export or backup location, readability, restore prerequisites, rollback path, and recovery owner under [[Backup and Recovery Standard]].
6. Assign monitoring, alert response, incident handling, retry or replay decisions, maintenance, support, and escalation responsibilities.
7. Disclose current limitations, blocked integrations, not-run procedures, open actions, accepted risks, and support boundaries.
8. Define handover acceptance criteria and walk through normal operation, failure handling, recovery, and escalation using sanitized examples.
9. Confirm approved access transfer and removal or reduction of temporary access.
10. Record the final verified state, receiving-owner acceptance, accepted limitations, support start, and escalation path.

## Verification

- Workflow inventory and activation states are current.
- Owners understand dependencies, operating boundaries, and current limitations.
- Credential ownership is documented without secret values.
- Backup, rollback, restore prerequisites, and recovery ownership are usable.
- Monitoring, maintenance, support, and escalation responsibilities are assigned.
- Access transfer and the final verified state are confirmed.
- Receiving-owner acceptance and remaining open actions are recorded.

## Stop / Escalate When

- Workflow state, ownership, access, recovery readiness, monitoring, support, or acceptance criteria remain unclear.
- A procedure is described as verified without evidence.
- The handover package would require secrets or unredacted sensitive data.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Backup and Recovery Standard]]
- [[Client Data Handling Standard]]
- [[Credential and Secrets Management Standard]]

## Do

- Keep handover open until responsibility and recovery readiness are accepted.

## Don’t

- Transfer credentials through documentation.
- Hide limitations or unresolved operational ownership.
