---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - credentials
  - security
---

# Rotate an API Credential

## Purpose

Replace an API credential safely while preserving service continuity and preventing secret exposure.

## When to Use

Use for scheduled rotation, expiry, permission reduction, personnel changes, or suspected exposure.

## Requirements

- Credential owner and affected workflow inventory
- Approved credential store
- New credential provisioned by an authorized owner
- DEV test plan
- PROD backup, rollback plan, change window, and explicit approval when applicable

## Safety Considerations

- Never place the old or new secret in this vault, chat, source control, screenshots, or workflow notes.
- Use placeholders such as `YOUR_API_KEY` and `YOUR_WEBHOOK_SECRET` in documentation.
- Keep DEV and PROD credentials separate.
- Do not revoke the previous credential until the new one is verified unless immediate revocation is required for an incident.
- Codex and MCP must not modify PROD credential references without explicit approval.

## Ownership and Approval Gates

- Credential owner provisions, approves, and revokes credentials.
- Developer verifies the change in DEV.
- Reviewer confirms affected workflows and rollback readiness.
- PROD approver authorizes the production reference change and smoke test.

## Procedure

1. Identify the credential by approved name, never by value.
2. Inventory every workflow and integration that references it.
3. Record the rotation reason, owner, expiry, permissions, and change window without recording the secret.
4. Create or provision the replacement in the approved credential store.
5. Name it `DEV - Service - Purpose` or `PROD - Service - Purpose` as appropriate.
6. Verify permissions follow least privilege.
7. Update and test the DEV credential reference first.
8. Record successful DEV test evidence and failure behavior.
9. Back up affected PROD workflows.
10. Obtain explicit PROD approval.
11. Update only the approved PROD references.
12. Run a minimal smoke test and monitor authentication errors.
13. Confirm all affected workflows use the intended credential.
14. Revoke the previous credential after success and approval, or immediately under the incident plan.
15. Record completion, owner, affected workflows, and next rotation date.

## Verification

- [ ] Secret values were never documented.
- [ ] Affected workflows were inventoried.
- [ ] DEV verification passed.
- [ ] PROD backup and approval exist when applicable.
- [ ] PROD smoke test passed.
- [ ] Old credential was revoked at the approved time.
- [ ] Authentication errors and dependent services were monitored.

## Failure Handling

If the new credential fails, restore the previous approved reference when it remains safe, keep affected workflows inactive if necessary, and notify the credential owner. For suspected exposure, prioritize revocation and containment over continuity according to the incident plan.

## Rollback

Reassign the last working credential reference if it is still valid and approved. Restore workflow backups if unrelated configuration changed. Revoke any failed replacement that should not remain active.

## Troubleshooting

- **Unauthorized response:** Check permissions, environment, and service account ownership.
- **Some workflows still fail:** Repeat the dependency inventory and confirm each credential reference.
- **Old credential already revoked:** Keep workflows contained while the owner corrects the replacement.

## Related Notes

- [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]]
- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[Templates/Client Automation/Credentials Checklist|Credentials Checklist]]
- [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
