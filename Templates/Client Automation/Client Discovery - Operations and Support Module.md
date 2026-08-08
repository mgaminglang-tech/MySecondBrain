---
type: client-discovery-module
status: template
module: operations-support
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - discovery
  - operations
  - support
---

# Client Discovery - Operations and Support Module

## When to Use

Duplicate this module into the project folder when production, performance, monitoring, recovery, maintenance, support, training, or post-launch ownership is in scope. Link the completed module to the project [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]] copy.

## Project Record

- Client: `CLIENT_NAME`
- Project: `PROJECT_NAME`
- Review date: `YYYY-MM-DD`
- Module owner:
- Operational approver:

## 1. Volume, Frequency, and Performance

- [ ] What average and peak volume is expected per hour, day, week, or month?  
  **Volume:**
- [ ] What schedules, seasonal spikes, batch imports, blackout periods, or concurrency levels apply?  
  **Frequency and peaks:**
- [ ] What payload, record-count, attachment, or file-size limits apply?  
  **Limits:**
- [ ] What start-delay, completion-time, latency, accuracy, or throughput targets apply?  
  **Performance targets:**
- [ ] What performance evidence is required before launch?  
  **Evidence:**

## 2. Retry, Timeout, and Failure Behavior

- [ ] Which failures should retry, how many times, and with what delay or backoff?  
  **Retry policy:**
- [ ] What timeout applies to each external step and the complete workflow?  
  **Timeouts:**
- [ ] Which failures stop processing, continue safely, or require human review?  
  **Failure behavior:**
- [ ] How are partial success, duplicates, replay, and idempotency handled?  
  **Reliability rules:**
- [ ] What manual fallback keeps the business process operating?  
  **Fallback:**

## 3. Monitoring, Alerts, and Incidents

- [ ] Which workflow health, failure, delay, queue, and business metrics must be monitored?  
  **Monitoring:**
- [ ] Who receives which alerts, through what channel, and within what response target?  
  **Alert rules:**
- [ ] Who owns incident triage, correction, replay, communication, and closure?  
  **Incident owner:**
- [ ] What escalation path applies during and outside the support window?  
  **Escalation:**
- [ ] What incident evidence and review record must be retained?  
  **Evidence:**

## 4. Reconciliation and Recovery

- [ ] How will source and destination records be reconciled?  
  **Reconciliation:**
- [ ] Who reviews mismatches, duplicates, missed items, and partial results?  
  **Owner:**
- [ ] What must be backed up, how often, and where is the approved location?  
  **Backup plan:**
- [ ] How will restore and rollback be tested?  
  **Restore evidence:**
- [ ] What recovery time objective (RTO) and recovery point objective (RPO) apply?  
  **RTO and RPO:**

## 5. Maintenance and Support

- [ ] What workflow, credential, dependency, rule, and documentation review schedule applies?  
  **Maintenance schedule:**
- [ ] What support window, response target, communication channel, and included work apply?  
  **Support model:**
- [ ] Who owns post-launch workflow operation, credentials, business rules, and vendor coordination?  
  **Post-launch owners:**
- [ ] What training, walkthrough, runbook, and handover deliverables are required?  
  **Training and handover:**
- [ ] Who accepts ongoing operational responsibility?  
  **Receiving owner:**

## 6. Production Approval

- [ ] Who may approve production deployment?  
  **Deployment approver:**
- [ ] Who may approve workflow activation and real external side effects?  
  **Activation approver:**
- [ ] What regression, integration, UAT, performance, recovery, security, and smoke evidence is required?  
  **Release evidence:**
- [ ] What rollback conditions require launch to stop or reverse?  
  **Stop conditions:**
- [ ] What post-launch review date and acceptance period apply?  
  **Review window:**

## Operational Readiness Gate

- [ ] Volume, frequency, performance, retries, timeouts, and failure behavior are approved.
- [ ] Monitoring, alerts, incident ownership, fallback, and escalation are ready.
- [ ] Reconciliation, backup, restore, RTO, RPO, and rollback evidence are ready.
- [ ] Maintenance, support, training, handover, and post-launch ownership are accepted.
- [ ] Production deployment, activation, and side-effect approvals are explicit.

**Decision:** GO / CONDITIONAL GO / NO-GO  
**Approver:**  
**Date:**  
**Evidence:**  
**Blockers or conditions:**  
**Next action:**

## Related Notes

- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
- [[Templates/Client Automation/Client Discovery - Integrations and Security Module|Client Discovery - Integrations and Security Module]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- [[Standard Automation Project Workflow]]
