---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Client Data Handling Standard

## Purpose

Define reusable controls for minimizing, separating, protecting, retaining, and removing client or customer data throughout an automation project.

## Data Classification

| Class | Examples | Handling |
| --- | --- | --- |
| Public | Published information | Use when relevant. |
| Internal | Non-public operational information | Restrict to approved project participants. |
| Confidential | Client business records or contact data | Minimize, restrict, and sanitize outside approved production use. |
| Restricted | Credentials, authentication data, regulated or highly sensitive records | Keep out of the vault and use only approved protected systems. |

When classification is uncertain, use the more restrictive handling and ask the data owner.

## Minimization and Environment Rules

- Collect and process only fields required by the approved scope.
- Use fabricated or irreversibly sanitized data in DEV.
- Optional STAGING should use sanitized data and non-production integrations unless the data owner explicitly approves an exception and safeguards.
- PROD may process only approved fields for approved destinations and workflow purposes.
- Avoid copying client data into Obsidian, prompts, source control, screenshots, fixtures, or logs. Any necessary example must be sanitized and authorized.
- Do not expose production payloads during troubleshooting unless access is approved and necessary.

Sanitization should remove or transform names, email addresses, phone numbers, account identifiers, and document contents so the original person or record cannot be reconstructed.

## Ownership and Review

- The client data owner approves permitted data classes and destinations.
- The project owner records the data flow and minimization decisions.
- The developer implements sanitization and avoids unnecessary payload logging.
- The reviewer checks fields, storage, error paths, access, and retention before production approval.

## Incident Response

1. Stop affected processing when continued execution could increase exposure.
2. Preserve only the evidence required by the incident plan.
3. Notify the project owner and client data owner.
4. Revoke or reduce exposed access under [[Credential and Secrets Management Standard]].
5. Reproduce and correct the issue in DEV using sanitized data.
6. Obtain approval before applying a production fix.
7. Record decisions without copying sensitive payloads into documentation.

## Retention, Deletion, and Handover

- Define retention and deletion responsibilities according to the client agreement or applicable policy; do not invent a universal period.
- At handover, document data ownership, approved destinations, retention, deletion, and access-revocation responsibilities.
- Remove temporary test data and temporary access when authorized and required by the agreement.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Backup and Recovery Standard]]
- [[Credential and Secrets Management Standard]]
