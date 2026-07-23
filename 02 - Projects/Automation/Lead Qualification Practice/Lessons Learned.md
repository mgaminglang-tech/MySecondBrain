---
type: project-note
status: draft
completion: incomplete
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - lessons-learned
  - incomplete
---

# Lessons Learned

## Current Status

Incomplete. The inactive DEV workflow has been built, and TC-001 has one user-confirmed controlled PASS using dummy data. The broader v0.1 test suite, operational review, and any future deployment evidence remain incomplete.

## Confirmed Lessons

### Validate node parameter storage types

Edit Fields / Set v3.4 JSON mode requires `jsonOutput` to be stored as a serialized JSON string. A structurally correct fixture can still fail at runtime when the node parameter uses the wrong storage type. Saved node configuration and runtime behavior should both be checked before expanding test coverage.

### Compile-check Code-node regular expressions

Schema validation alone did not expose the invalid escaped backtick in a JavaScript Unicode regex. Code-node JavaScript should receive a syntax compilation check in addition to node-schema and workflow-graph validation.

### Keep controlled DEV failures observable

The inactive, dummy-data-only design exposed both defects without credentials, external writes, notifications, or client-data risk. Preserving inert payloads and manual execution boundaries made the fixes narrow and reviewable.

### Retain evidence boundaries

TC-001 is recorded as passed from the result supplied for this documentation update. The successful execution ID was not supplied and must not be invented. No other v0.1 test is treated as passed.

## Questions for the Retrospective

- Which discovery questions most affected the design?
- Which normalization and validation rules prevented ambiguity?
- Did the score distribution match the sales team’s expectations?
- Which edge cases caused defects or changed requirements?
- Did the regional routing and deterministic v0.1 identity rules work as intended?
- Did the inactive DEV-only boundary remain effective?
- Were backup, rollback, monitoring, and handover procedures usable?

## Future v0.2 Retrospective

Persistent duplicate controls, integrations, retries, concurrency, STAGING, PROD, and reconciliation are future-work topics and are not evaluated by v0.1.

## Evidence Required

- Approved requirements and design decisions.
- Dummy-data test results and issue records.
- Version history and review decisions.
- Approved production metrics, if a deployment occurs.

## Related Notes

- [[Test Results]]
- [[Issues and Fixes]]
- [[Known Limitations]]
- [[Case Study]]
