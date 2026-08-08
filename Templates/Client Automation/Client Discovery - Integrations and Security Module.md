---
type: client-discovery-module
status: template
module: integrations-security
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - discovery
  - integrations
  - security
---

# Client Discovery - Integrations and Security Module

## When to Use

Duplicate this module into the project folder when external tools, APIs, webhooks, credentials, multiple environments, sensitive data, or security requirements are involved. Link the completed module to the project [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] copy.

> [!danger] Never record secret values
> Record credential names, owners, purposes, environments, permission needs, and secure-location references only. Do not include passwords, API keys, tokens, private keys, webhook secrets, or credential-bearing URLs.

## Project Record

- Client: `CLIENT_NAME`
- Project: `PROJECT_NAME`
- Review date: `YYYY-MM-DD`
- Module owner:
- Security approver:

## 1. Tools and Integrations

- [ ] Which existing tools, accounts, workspaces, databases, forms, folders, channels, or services are involved?  
  **Inventory:**
- [ ] What role does each system have: trigger, source, destination, approval, notification, or storage?  
  **Role by system:**
- [ ] Which objects, tables, fields, resources, regions, plans, limits, or non-secret identifiers apply?  
  **Resource details:**
- [ ] Are vendor documentation, rate limits, technical contacts, and third-party restrictions available?  
  **References and restrictions:**

## 2. APIs, Webhooks, and Test Environments

- [ ] Does each system provide an API, webhook, native n8n node, email interface, file export, or database connection?  
  **Connection method:**
- [ ] Are API or webhook features available on the client's plan and region?  
  **Availability:**
- [ ] Are test accounts, sandboxes, dummy destinations, or safe webhook endpoints available?  
  **Test resources:**
- [ ] What DEV, optional STAGING, and PROD access boundaries apply?  
  **Environment access:**
- [ ] Who approves access to each environment, and by what date?  
  **Approvers and deadlines:**

## 3. Credentials and Access Control

- [ ] Who owns each account, service connection, or credential reference?  
  **Owners:**
- [ ] What minimum permissions are required?  
  **Least-privilege scopes:**
- [ ] Can dedicated service accounts or OAuth connections be used instead of shared logins?  
  **Approved method:**
- [ ] Where will credential values be stored outside Obsidian and Git?  
  **Approved secure location:**
- [ ] Are DEV and PROD credentials separated?  
  **Separation plan:**
- [ ] Who may grant, revoke, and review access?  
  **Access-control owners:**
- [ ] What credential rotation schedule, expiry rule, and emergency-rotation process apply?  
  **Rotation policy:**

## 4. Data and Privacy

- [ ] What personal, financial, health, employee, client, or confidential information is processed?  
  **Data categories:**
- [ ] Which fields are approved, restricted, masked, encrypted, or prohibited?  
  **Field rules:**
- [ ] What consent, notice, lawful-basis, or opt-out requirements apply?  
  **Consent requirements:**
- [ ] Where may data be stored or processed?  
  **Approved locations:**
- [ ] What retention and deletion rules apply to records, files, payloads, and execution logs?  
  **Retention and deletion:**
- [ ] Could n8n execution data, errors, notifications, or backups expose sensitive values?  
  **Log-exposure controls:**
- [ ] Who may view workflow data, logs, credentials, and configuration?  
  **Access restrictions:**

## 5. Policy and Third-party Review

- [ ] Which company security, privacy, legal, contractual, or compliance policies apply?  
  **Policies:**
- [ ] Are data-processing agreements, vendor approvals, security reviews, or geographic restrictions required?  
  **Third-party requirements:**
- [ ] What evidence must be retained for security approval?  
  **Evidence:**

## Security Approval Gate

- [ ] Integration methods, environments, owners, access, and test resources are documented.
- [ ] Credential ownership, least privilege, storage, separation, rotation, and revocation are approved.
- [ ] Sensitive-data, consent, field, retention, deletion, log, and access-control rules are approved.
- [ ] Third-party and company security requirements are resolved or explicitly blocked.
- [ ] No secret values are stored in this module.

**Decision:** GO / CONDITIONAL GO / NO-GO  
**Approver:**  
**Date:**  
**Evidence:**  
**Blockers or conditions:**  
**Next action:**

## Related Notes

- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[Templates/Client Automation/Client Discovery - Operations and Support Module|Client Discovery - Operations and Support Module]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- [[Standard Automation Project Workflow]]
