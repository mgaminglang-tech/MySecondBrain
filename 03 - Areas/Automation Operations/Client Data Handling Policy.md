---
type: policy
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - privacy
  - client-data
---

# Client Data Handling Policy

## Purpose

Define how client data may be used, minimized, protected, and removed throughout an automation project.

## Data Principles

- Collect and process only data required by the approved scope.
- Use dummy or sanitized data in DEV.
- Use sanitized data in optional STAGING unless specific production-like data is explicitly approved.
- Use production data only in PROD and only for the approved workflow purpose.
- Do not copy client data into Obsidian, prompts, source control, screenshots, or test fixtures unless it is sanitized and authorized.
- Do not provide unredacted client data to Codex, MCP, or another assistant.
- Respect client requirements for residency, access, retention, deletion, and incident reporting.

## Data Classification

| Class | Examples | Handling |
|---|---|---|
| Public | Published documentation | May be used when relevant. |
| Internal | Non-public operational details | Limit to approved project members. |
| Confidential | Client business records or contact data | Minimize, restrict, and sanitize outside PROD. |
| Restricted | Credentials, authentication data, regulated or highly sensitive records | Never place in this vault; use approved protected systems only. |

When uncertain, apply the more restrictive classification and ask the client owner.

## Environment Rules

### DEV

- Use fabricated values such as `CLIENT_NAME`, `YOUR_EMAIL_ADDRESS`, and `TEST_RECORD_ID`.
- Remove or transform names, email addresses, phone numbers, account identifiers, and document contents.
- Test data must not allow the original person or record to be reconstructed.

### STAGING

- Optional and project-specific.
- Prefer sanitized data and non-production integrations.
- Any exception requires explicit data-owner approval and documented safeguards.

### PROD

- Process only approved fields and destinations.
- Restrict execution and data visibility to authorized roles.
- Configure retention and execution-data settings according to client requirements.
- Do not expose production payloads during troubleshooting unless access is approved and necessary.

## Ownership and Approval

- The client data owner approves permitted data categories and destinations.
- The project owner documents data flow and minimization decisions.
- The developer implements sanitization and avoids logging unnecessary payloads.
- The reviewer checks fields, storage, error paths, and retention before PROD approval.

## Failure and Incident Handling

1. Stop the affected processing when continued execution could increase exposure.
2. Preserve only the evidence required by the incident plan.
3. Notify the project owner and client data owner.
4. Revoke exposed access according to [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]].
5. Correct the workflow in DEV with sanitized reproduction data.
6. Obtain approval before applying a PROD fix.
7. Record decisions without copying sensitive payloads into documentation.

## Handover and Deletion

At handover, document data ownership, retention, deletion responsibilities, and access revocation. Confirm temporary test data and access are removed according to the client agreement.

## Related Notes

- [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]]
- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[Templates/Client Automation/Requirements|Requirements]]
- [[Templates/Client Automation/Architecture|Architecture]]
- [[Templates/Client Automation/Client Handover|Client Handover]]
