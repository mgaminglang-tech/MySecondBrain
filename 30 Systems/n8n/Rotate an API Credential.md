---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Rotate an API Credential

## Purpose

Replace an API credential deliberately while preserving service continuity, least privilege, environment separation, and a safe rollback path.

## Preconditions

- The credential owner, reason, environment, affected references, approved secure store, and rollback approach are known.
- Production backup, change window, smoke test, and approval exist when applicable.

## Procedure

1. Identify the credential by approved non-secret name and inventory every workflow and integration that references it.
2. Record the rotation reason, owner, environment, expiry, required permissions, change window, and status without recording secret values.
3. Provision the replacement through the approved secure mechanism under [[Credential and Secrets Management Standard]].
4. Confirm least privilege and environment-specific naming and access.
5. Update and verify the DEV reference first when applicable.
6. Preserve the last working reference and affected workflow backups as the rollback path.
7. Obtain explicit approval before changing production references.
8. Update only the approved references and validate that unrelated workflows remain unchanged.
9. Run the approved minimal smoke test and monitor authentication errors and dependent services.
10. Confirm every affected workflow uses the intended replacement.
11. Revoke the previous credential only after successful verification and accepted rollback risk, unless immediate incident containment requires earlier revocation.
12. Reduce obsolete access and record rotation completion, owner, affected references, revocation status, and next review date.

## Verification

- No secret value appears in documentation or evidence.
- Affected references were inventoried and deliberately updated.
- Permissions and environment separation are correct.
- The replacement passed the applicable DEV and approved production checks.
- Rollback remained available until verification completed.
- Previous access was revoked or its remaining status is explicit.

## Stop / Escalate When

- Ownership, permissions, affected references, environment, or production approval is unclear.
- The replacement fails or dependent workflows still use the previous credential unexpectedly.
- Exposure is suspected; treat it as an incident and prioritize containment under the approved incident plan.

## Related Standards

- [[Credential and Secrets Management Standard]]
- [[Backup and Recovery Standard]]
- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]

## Do

- Verify the replacement before routine revocation of the previous credential.

## Don’t

- Put keys, tokens, passwords, or client secrets in the vault.
- Change unrelated credential references during rotation.
