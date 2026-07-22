---
type: checklist
status: draft
client: CLIENT_NAME
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - credentials
  - security
---

# Credentials Checklist

## Safety Rule

Record credential names, owners, purpose, permissions, and status only. Never record secret values.

Use placeholders in examples:

```text
YOUR_API_KEY
YOUR_ACCESS_TOKEN
YOUR_WEBHOOK_SECRET
YOUR_DATABASE_URL
```

## Naming

- DEV: `DEV - Service - Purpose`
- PROD: `PROD - Service - Purpose`

## Credential Inventory

| Environment | Credential name | Service | Purpose | Owner | Permissions | Expiry or rotation | Status |
|---|---|---|---|---|---|---|---|
| DEV | `DEV - Service - Purpose` |  |  |  |  |  | planned |
| PROD | `PROD - Service - Purpose` |  |  |  |  |  | planned |

## DEV Readiness

- [ ] Test credential is stored in the approved credential manager.
- [ ] Permission scope is minimal.
- [ ] Credential targets a non-production account or resource.
- [ ] Dummy or sanitized data is used.
- [ ] Credential value is absent from documentation and source control.

## PROD Approval Gate

- [ ] Credential owner approved use.
- [ ] PROD credential is separate from DEV.
- [ ] Affected workflows are inventoried.
- [ ] Backup and rollback plan exist.
- [ ] Explicit approval to assign the PROD credential is recorded.
- [ ] Smoke-test and monitoring plan are ready.

## Rotation

- Rotation owner:
- Rotation trigger or schedule:
- Previous credential revocation plan:
- Rollback reference:
- Last rotation date:
- Next review date:

## Access Review

- [ ] Only required people and workflows have access.
- [ ] Former project access is removed.
- [ ] Expired or unused credentials are revoked with approval.
- [ ] No credential values appear in notes, logs, exports, or screenshots.

## Related Notes

- [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]]
- [[06 - SOPs/n8n/Rotate an API Credential|Rotate an API Credential]]
- [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
