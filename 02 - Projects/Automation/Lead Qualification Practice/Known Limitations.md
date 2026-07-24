---
type: project-note
status: active
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - limitations
---

# Known Limitations

## Purpose

Record finalized v0.1 scope constraints and risks that remain intentionally deferred or limited.

## Limitation Register

| ID      | Limitation                                                           | Potential impact                                          | Proposed mitigation                                                  | Status  |
| ------- | -------------------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------------------- | ------- |
| LIM-001 | Manual Trigger and dummy data only.                                  | No automatic lead capture or real lead processing.        | Deferred to a separately approved version.                           | disclosed |
| LIM-002 | Storage payload is preparation-only.                                 | No record is persisted.                                   | Airtable or Google Sheets adapter deferred to v0.2.                  | disclosed |
| LIM-003 | Notification payload is preparation-only.                            | No internal message is delivered.                         | Email or Telegram adapter deferred to v0.2.                          | disclosed |
| LIM-004 | Email key has no persistent lookup.                                  | Repeated normalized emails are not detected historically. | Persistent duplicate lookup and policy deferred to v0.2.             | disclosed |
| LIM-005 | No external retries or concurrency control.                          | v0.1 cannot validate side-effect reliability.             | External API and concurrency tests deferred to v0.2.                 | disclosed |
| LIM-006 | Need clarity uses a fixed keyword list.                              | Valid needs using synonyms may receive only five points.  | Review aggregate results before changing the versioned keyword list. | disclosed |
| LIM-007 | Free-email classification uses five exact domains.                   | Other consumer domains may receive business-email points. | Expand only through an approved scoring-rule revision.               | disclosed |
| LIM-008 | Unsupported region is invalid and falls back to General Sales Queue. | Human review is required.                                 | Preserve explicit fallback reason and review flag.                   | disclosed |
| LIM-009 | Credential-free Crypto v2 SHA-256 hashes are deterministic test identifiers only. | They do not provide historical duplicate or concurrency protection. | Design persistent identity and duplicate controls in v0.2.          | disclosed |
| LIM-010 | Valid score increments are multiples of five.                        | Scores 69 and 39, among others, are unattainable.         | Test attainable boundary representatives 70, 65, 40, and 35.         | disclosed |

## Test-Coverage Limitation

The 25-test Core Release Suite passed and is the accepted demo gate. The remaining 88 Extended Regression tests are not run. They do not block the controlled demo but are required before production deployment or after a major workflow change.

## Excluded Scope

- Airtable, Google Sheets, Email, Telegram, historical duplicate lookup, external retries, concurrency, side effects, STAGING, PROD, AI scoring, enrichment, CRM synchronization, and dashboards.

## Review Rules

- Approved v0.1 scope decisions are finalized; Project Owner and Automation Engineer review implementation evidence before development completion.
- Any v0.2 risk acceptance requires an explicit approver, rationale, and review date.
- Update [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]] and [[02 - Projects/Automation/Lead Qualification Practice/Maintenance Guide|Maintenance Guide]] when a limitation changes.

## Related Notes

- [[02 - Projects/Automation/Lead Qualification Practice/Requirements|Requirements]]
- [[02 - Projects/Automation/Lead Qualification Practice/Issues and Fixes|Issues and Fixes]]
- [[02 - Projects/Automation/Lead Qualification Practice/Maintenance Guide|Maintenance Guide]]
- [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]]
