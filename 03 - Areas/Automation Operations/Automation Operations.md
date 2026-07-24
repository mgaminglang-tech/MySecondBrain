---
type: area
status: active
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - operations
  - n8n
---

# Automation Operations

## Purpose

Provide a reusable operating system for designing, testing, deploying, supporting, and handing over client automations safely.

## Operating Principles

- Keep DEV and PROD separate in naming, credentials, data, approvals, and activation.
- Use dummy or sanitized data and test credentials in DEV.
- Treat STAGING as optional and define it per project when needed.
- Require explicit approval, a current backup, rollback planning, smoke testing, and controlled activation for PROD.
- Codex and MCP must not modify PROD without explicit approval for the specific change.
- Record ownership, decisions, test evidence, limitations, and handover status.
- Never store secrets or unredacted client data in this vault.

## Policies

- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[03 - Areas/Automation Operations/Secrets Management Policy|Secrets Management Policy]]
- [[03 - Areas/Automation Operations/Backup Policy|Backup Policy]]
- [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]]

## Core Project Workflow

- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]] — Use as the permanent lifecycle, safety-gate, and evidence reference for every automation project.
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]] — Duplicate into each project folder and use the copy to track actual phase status, approvals, evidence, and blockers.
- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] — Duplicate and complete during intake to capture the business process, scope, stakeholders, data, risks, and open questions.
- [[06 - SOPs/n8n/Start a New Client Automation|Start a New Client Automation]] — Use before development to establish ownership, scope, requirements, architecture, and authorization.
- [[06 - SOPs/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]] — Use after development approval to build and test safely within the defined DEV boundary.

## n8n SOPs

- [[06 - SOPs/n8n/Start a New Client Automation|Start a New Client Automation]]
- [[06 - SOPs/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[06 - SOPs/n8n/Promote DEV Workflow to PROD|Promote DEV Workflow to PROD]]
- [[06 - SOPs/n8n/Export and Version an n8n Workflow|Export and Version an n8n Workflow]]
- [[06 - SOPs/n8n/Restore an n8n Workflow from Backup|Restore an n8n Workflow from Backup]]
- [[06 - SOPs/n8n/Rotate an API Credential|Rotate an API Credential]]
- [[06 - SOPs/n8n/Handle a Failed Production Workflow|Handle a Failed Production Workflow]]
- [[06 - SOPs/n8n/Client Automation Handover|Client Automation Handover]]

## Client Project Templates

- [[Templates/Client Automation/Client Automation Project|Client Automation Project]]
- [[Templates/Client Automation/Requirements|Requirements]]
- [[Templates/Client Automation/Architecture|Architecture]]
- [[Templates/Client Automation/Development Plan|Development Plan]]
- [[Templates/Client Automation/Test Plan|Test Plan]]
- [[Templates/Client Automation/Test Results|Test Results]]
- [[Templates/Client Automation/Deployment Checklist|Deployment Checklist]]
- [[Templates/Client Automation/Client Handover|Client Handover]]

## Lifecycle

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]] as the authoritative lifecycle. Project copies of the checklist and discovery template hold the actual project evidence.

## Review Cadence

Review these policies and SOPs when tooling, client obligations, security requirements, or deployment practices change. Procedures remain drafts until evidence shows they have been tested in the relevant environment.
