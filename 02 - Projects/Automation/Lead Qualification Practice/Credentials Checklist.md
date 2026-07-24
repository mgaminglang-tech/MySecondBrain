---
type: checklist
status: active
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - credentials
  - security
---

# Credentials Checklist

## Safety Rule

Record names, owners, purpose, permissions, and status only. Never record credential values.

```text
YOUR_API_KEY
YOUR_ACCESS_TOKEN
YOUR_EMAIL_ADDRESS
YOUR_TELEGRAM_BOT_TOKEN
YOUR_DATABASE_URL
```

## Required Integrations

v0.1 requires no credentials. It is an inactive DEV workflow with Manual Trigger, dummy data, local transformations, credential-free Crypto v2 SHA-256 hashing, and prepared payloads only. Crypto performs no network requests.

| Version | Environment | Credential requirement | Status |
|---|---|---|---|
| v0.1 | DEV | None | demo verified |
| v0.1 | STAGING | Not used | not-applicable |
| v0.1 | PROD | Not used | not-applicable |
| v0.2 | To be designed | Airtable or Google Sheets, plus Email or Telegram | deferred |

No v0.2 credential may be created or assigned under the v0.1 plan.

## v0.1 Access

- Automation Engineer: May build and manually test the inactive DEV workflow after approval.
- Project Owner: Reviews requirements, architecture, results, and operational readiness.
- No Airtable, Google Sheets, Email, Telegram, STAGING, or PROD access is required.

## v0.1 DEV Checklist

- [x] Workflow credential count is zero.
- [x] Workflow node inventory has no credential-backed or external request node.
- [x] Crypto v2 is configured for SHA-256 lowercase hexadecimal output with no credential.
- [x] Manual Trigger is the only trigger.
- [x] Dummy data is confirmed.
- [x] Workflow remains inactive.
- [x] No secret or credential placeholder is placed in workflow fields.

These checks support the controlled demo only. No production credential design, access approval, or live integration approval exists.

## Deferred v0.2 Credential Decisions

- Select Airtable or Google Sheets and assign a least-privilege credential owner.
- Select Email or Telegram and approve sender/chat and recipient ownership.
- Define DEV, optional STAGING, and PROD separation for v0.2.
- Define permissions, rotation, revocation, expiry, access review, and temporary-access cleanup.
- Record credential names and owners only; never record secret values.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]]
- [[02 - Projects/Automation/Lead Qualification Practice/Architecture|Architecture]]
- [[02 - Projects/Automation/Lead Qualification Practice/Deployment Checklist|Deployment Checklist]]
- [[02 - Projects/Automation/Lead Qualification Practice/Maintenance Guide|Maintenance Guide]]
