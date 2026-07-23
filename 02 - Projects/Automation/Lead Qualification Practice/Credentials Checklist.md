---
type: checklist
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
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

The initial nine-node practice workflow requires no external integration credentials. Future persistence and delivery require one storage choice and one notification choice.

| Environment | Proposed credential name | Service | Purpose | Status |
|---|---|---|---|---|
| DEV | `DEV - Airtable - Lead Storage` | Airtable, optional choice | Test-base record storage | planned |
| DEV | `DEV - Google Sheets - Lead Storage` | Google Sheets, optional choice | Test-sheet record storage | planned |
| DEV | `DEV - Email - Sales Notification` | Email provider, optional choice | Test inbox notification | planned |
| DEV | `DEV - Telegram - Sales Notification` | Telegram, optional choice | Test chat notification | planned |
| STAGING | `STAGING - Service - Purpose` | Chosen services | Optional integration acceptance | optional |
| PROD | `PROD - Service - Purpose` | Chosen services | Approved live storage or notification | planned |

Only the selected storage and notification credentials should be created.

## Required Resource References

- n8n DEV project or instance access.
- Optional STAGING and PROD n8n access with separated roles.
- Airtable base/table/view IDs or Google spreadsheet/sheet IDs.
- Email sender identity and approved recipient role, or Telegram bot and chat reference.
- Approved routing table and fallback owner.

Record identifiers only where policy permits. Never record secret values.

## DEV Checklist

- [ ] Credential owner identified.
- [ ] Least-privilege test credential stored in n8n credentials.
- [ ] Non-production resource and test destination confirmed.
- [ ] Dummy/sanitized data confirmed.
- [ ] Credential value absent from notes, workflow fields, exports, logs, and screenshots.

## Optional STAGING Checklist

- [ ] STAGING is justified and approved.
- [ ] Credentials are separate from DEV and PROD.
- [ ] Resources and recipients are non-production or explicitly controlled.
- [ ] Expiry and cleanup owner is assigned.

## PROD Checklist

- [ ] Credential owner approves use.
- [ ] Separate PROD credentials use least privilege.
- [ ] Backup, rollback, smoke test, monitoring, and affected workflows are documented.
- [ ] Explicit approval to assign each PROD credential is recorded.
- [ ] Rotation and revocation procedures are assigned.

## Permissions Guidance

- Storage: Limit to the selected base/table or spreadsheet where supported.
- Email: Send-only from an approved sender to approved internal recipients.
- Telegram: Send-message access to the approved internal chat only.
- n8n: Separate build, review, and activation responsibilities where practical.

## Open Questions

- Which storage and notification options will be selected?
- Who owns each account and credential?
- What permissions, rotation schedule, and access-review cadence are required?
- What sender identity or Telegram chat is approved?

## Related Notes

- [[Requirements]]
- [[Architecture]]
- [[Deployment Checklist]]
- [[Maintenance Guide]]

