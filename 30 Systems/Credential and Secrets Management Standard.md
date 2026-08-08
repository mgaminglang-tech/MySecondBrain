---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Credential and Secrets Management Standard

## Purpose

Define the reusable credential lifecycle controls that supplement the secret-protection and approval boundaries in `AGENTS.md`.

## Storage and Access

- Store secrets only in an approved credential manager or platform credential store.
- Never place secret values in Obsidian, Git, workflow notes, screenshots, fixtures, chat messages, or documentation exports.
- Grant the minimum required permissions and shortest practical lifetime.
- Use separate credentials by environment; never copy production credentials into DEV or STAGING.
- Document only non-secret metadata such as credential name, purpose, environment, owner, minimum permission, and approved secure location.

Useful naming defaults:

- DEV credential: `DEV - Service - Purpose`
- PROD credential: `PROD - Service - Purpose`

## Ownership

| Responsibility | Owner |
| --- | --- |
| Provision credential | Authorized client or system owner |
| Approve access | Client or designated security owner |
| Configure credential reference | Authorized automation operator |
| Review permissions and expiry | Credential owner |
| Rotate or revoke | Credential owner with project coordination |

Production credential creation, replacement, reassignment, or revocation requires the applicable explicit approval.

## Rotation Triggers

Rotate or replace a credential when:

- exposure is suspected or confirmed
- a person with access leaves the project
- the provider requires rotation or the credential expires
- permissions are broader than necessary
- an approved rotation schedule is reached

## Staged Replacement

1. Identify affected workflows, owners, environment, permissions, and rollback needs without exposing the secret.
2. Provision the replacement through an approved secure mechanism.
3. Validate with non-production credentials first when applicable.
4. Update only approved credential references.
5. Run the approved smoke test without revealing the value.
6. Confirm intended workflows use the replacement.
7. Revoke the previous credential only after the replacement works and rollback risk is accepted.
8. Reduce obsolete access and record non-secret evidence of the change.

## Exposure Response

1. Stop sharing or copying the value.
2. Notify the credential owner and incident owner.
3. Revoke or rotate according to the approved incident plan.
4. Review affected workflow and access logs.
5. Remove exposed copies from approved systems without destroying required incident evidence.
6. Document the incident without recording the secret itself.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Backup and Recovery Standard]]
- [[Client Data Handling Standard]]
