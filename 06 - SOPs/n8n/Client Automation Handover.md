---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - handover
---

# Client Automation Handover

## Purpose

Transfer an automation with clear ownership, operational knowledge, recovery capability, and accepted limitations.

## When to Use

Use before project closure, support transfer, client self-management, or a change of delivery owner.

## Requirements

- Approved release and test evidence
- Current architecture and workflow inventory
- Credential ownership map without secret values
- Backup and restore information
- Maintenance, monitoring, failure, and escalation guidance
- Known limitations and open actions
- Named receiving owner and acceptance authority

## Safety Considerations

- Transfer access through approved systems, never through documentation.
- Do not include secrets, tokens, passwords, or unredacted client data in the handover package.
- Confirm obsolete temporary access and test credentials are removed according to approval.
- Do not describe untested procedures as verified.

## Ownership and Approval Gates

- Delivery owner prepares the handover package.
- Technical reviewer checks accuracy and recovery readiness.
- Credential and data owners confirm access responsibilities.
- Receiving owner confirms understanding and operational ownership.
- Client approver accepts the handover and remaining limitations.

## Procedure

1. Complete [[Templates/Client Automation/Client Handover|Client Handover]].
2. Record workflow names, IDs, environments, versions, owners, and current activation states.
3. Link architecture, requirements, deployment records, tests, issues, and decisions.
4. Document triggers, schedules, inputs, outputs, downstream systems, and expected volumes.
5. Record credential names, owners, expiry or rotation responsibility, and access-request process without values.
6. Provide monitoring, alert, failure-handling, retry, and escalation instructions.
7. Verify the current backup and document restore prerequisites.
8. Document maintenance cadence, dependency changes, and support boundaries.
9. Review [[Templates/Client Automation/Known Limitations|Known Limitations]] and open actions.
10. Conduct a walkthrough using sanitized examples.
11. Confirm access transfer and removal of temporary access.
12. Obtain receiving-owner and client acceptance.
13. Record the handover date, accepted risks, support start date, and contact path.

## Verification

- [ ] Workflow inventory and activation states are current.
- [ ] Architecture and data flow are understandable.
- [ ] Credential ownership is documented without secrets.
- [ ] Backup and restore requirements are current.
- [ ] Monitoring, maintenance, failure, and escalation paths are assigned.
- [ ] Limitations and open actions are accepted.
- [ ] Walkthrough completed with sanitized data.
- [ ] Access transfer and removal confirmed.
- [ ] Receiving owner and client approver accepted the handover.

## Failure Handling

If ownership, access, backup, or support responsibilities remain unclear, do not close the handover. Record the blocker, owner, and resolution date.

## Rollback

If the receiving team cannot assume operations, retain the prior support arrangement temporarily under explicit agreement. Restore access only through approved systems and record the revised ownership plan.

## Troubleshooting

- **Missing documentation:** Keep handover open and assign an owner.
- **Recipient lacks access:** Use the approved access-request process; never send credentials in notes.
- **Backup cannot be restored:** Treat recovery readiness as blocked and resolve before acceptance.

## Related Notes

- [[03 - Areas/Automation Operations/Automation Operations|Automation Operations]]
- [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]]
- [[Templates/Client Automation/Maintenance Guide|Maintenance Guide]]
- [[Templates/Client Automation/Case Study|Case Study]]
