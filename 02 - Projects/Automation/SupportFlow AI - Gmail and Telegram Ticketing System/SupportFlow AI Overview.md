---
type: project
project_type: ai-automation
status: planned
phase: discovery
priority: medium
client: internal-demo
owner: Mervin
production_ready: false
version: v0.1.0
created: 2026-07-25
updated: 2026-07-25
tags:
  - project
  - client-automation
  - n8n
  - customer-support
  - ai
---

# SupportFlow AI — Gmail and Telegram Ticketing System

## Objective

Design a centralized DEV-only support-ticket process that converts dummy or sanitized Gmail and Telegram messages into one validated ticket structure, detects duplicates, classifies requests, prepares unsent draft responses, stores approved test records, creates controlled test tasks, and produces controlled escalation alerts.

## Initial State

- Status: planned
- Current phase: discovery
- Owner and current approver: Mervin
- Target date: Not Yet Defined
- Production ready: false
- Canonical workflow name: `DEV - SupportFlow AI - Gmail and Telegram Ticketing System`
- Workflow state: unbuilt and inactive
- Testing state: not-run
- Data classification: dummy and sanitized test data only
- External side effects: not approved
- Production credentials, integrations, deployment, and activation: not approved

## Business Problem

Support inquiries arrive through Gmail and Telegram but are managed separately. This creates risk of missed or delayed requests, duplicate tickets, inconsistent classification, missed refund or urgent escalations, limited post-assignment visibility, and unreliable response and resolution-time measurement.

## Desired Outcome

Both channels produce the same auditable ticket structure and follow a controlled path through validation, identity generation, duplicate checking, classification, draft preparation, storage, task preparation or creation, and conditional escalation. No response is automatically sent to a customer.

## Scope

### Included

- Gmail and Telegram intake design
- Channel-specific normalization into a unified ticket
- Required-field validation and unique ticket ID generation
- Airtable duplicate checking and ticket storage
- AI-assisted category, priority, sentiment, escalation, and draft response
- Deterministic business-rule enforcement after AI output
- ClickUp task creation for valid, non-duplicate tickets
- Slack alerts for approved urgent, refund, or high-risk conditions
- Controlled DEV testing with dummy or sanitized data

### Not Included

- Website forms, voice, or phone support
- Automatic customer replies
- Real customer data or production credentials
- Production integrations, activation, or deployment
- Automatic ticket closure or deletion
- Full SLA enforcement, analytics dashboard, or customer portal

## Planned Workflow

```text
Gmail intake ─┐
              ├→ Normalize → Validate → Generate ticket ID
Telegram ─────┘              → Duplicate check
                              → AI classification and draft
                              → Apply deterministic rules
                              → Store ticket
                              → Create controlled ClickUp task
                              → Send controlled Slack alert when eligible
                              → Return audit summary
```

This is a proposed architecture, not evidence of an implemented workflow.

## Success Criteria

- Both inputs produce the approved unified structure.
- Invalid inputs stop safely without downstream ticket, task, or alert side effects.
- Every valid new request receives a unique ticket ID.
- Documented duplicate rules prevent duplicate downstream actions.
- AI output is schema-validated and constrained to approved values.
- Draft responses are stored for review and never automatically sent.
- Airtable, ClickUp, and Slack actions occur only under approved DEV test controls.
- Evidence distinguishes `passed`, `failed`, `blocked`, `not-run`, and `deferred`.
- The workflow remains inactive and credential-safe throughout development.

## Current Decision

**CONDITIONAL GO — documentation and discovery refinement only.** The DEV build is not authorized. The conditions are recorded in [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]].

## Next Action

Mervin reviews and resolves the blocking discovery questions, then separately approves or rejects the scope, requirements, architecture, and inactive DEV build phase.

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Automation Project Checklist|Automation Project Checklist]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Discovery and Scope|Discovery and Scope]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Architecture|Architecture]]
- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
