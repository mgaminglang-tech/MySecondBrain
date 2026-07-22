---
type: policy
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - security
  - credentials
---

# Secrets Management Policy

## Purpose

Prevent credentials and secrets from being exposed, reused across environments, or stored in documentation.

## Covered Secrets

- API keys and access tokens
- Passwords and authentication cookies
- OAuth client secrets and refresh tokens
- Webhook secrets and signing keys
- Private keys, certificates, and database URLs
- Any value that grants access to a client or production system

## Core Rules

- Store secrets only in an approved credential manager or n8n credential store.
- Never place a secret in Obsidian, source control, workflow notes, screenshots, test fixtures, chat messages, or exports intended for documentation.
- Use placeholders such as `YOUR_API_KEY`, `YOUR_ACCESS_TOKEN`, `YOUR_WEBHOOK_SECRET`, and `YOUR_DATABASE_URL`.
- Use separate DEV and PROD credentials.
- Grant the minimum permissions and shortest practical lifetime.
- Do not copy PROD secrets into DEV or STAGING.
- Do not expose credential values to Codex, MCP, or another assistant.

## Naming Standards

- DEV credential: `DEV - Service - Purpose`
- PROD credential: `PROD - Service - Purpose`

The credential name may be documented. The secret value must not be documented.

## Ownership and Approval

| Responsibility | Owner |
|---|---|
| Create or provision credential | Authorized client or system owner |
| Approve access | Client or designated security owner |
| Configure credential reference | Authorized automation operator |
| Review permissions and expiry | Credential owner |
| Rotate or revoke | Credential owner with project coordination |

Production credential creation, replacement, or reassignment requires explicit approval.

## Rotation Requirements

Rotate a credential when:

- It is suspected or confirmed to be exposed.
- A person with access leaves the project.
- The provider requires rotation or expiry.
- The credential has broader permissions than necessary.
- The agreed rotation schedule is reached.

Follow [[06 - SOPs/n8n/Rotate an API Credential|Rotate an API Credential]] and prepare rollback before changing PROD.

## Verification

- Confirm the credential name identifies its environment and purpose.
- Confirm only intended workflows reference it.
- Test in DEV with test credentials first.
- For PROD, perform an approved smoke test without revealing the secret.
- Confirm the previous credential is revoked only after the new credential works and rollback risk is accepted.

## Failure Handling

If exposure is suspected:

1. Stop sharing or copying the value.
2. Notify the credential owner and incident owner.
3. Revoke or rotate according to the approved incident plan.
4. Review workflow and access logs.
5. Remove exposed copies from approved systems without destroying evidence needed for investigation.
6. Document the incident without recording the secret itself.

## Related Notes

- [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]]
- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[Templates/Client Automation/Credentials Checklist|Credentials Checklist]]
- [[06 - SOPs/n8n/Rotate an API Credential|Rotate an API Credential]]
