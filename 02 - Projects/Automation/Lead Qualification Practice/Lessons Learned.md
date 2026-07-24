---
type: project-note
status: draft
completion: incomplete
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - lessons-learned
  - incomplete
---

# Lessons Learned

## Current Status

The demo phase is complete: the inactive DEV workflow was built and all 25 Core Release Suite tests passed using dummy data, with 0 failed and 0 blocked. This note remains incomplete for full project closure because the 88-test Extended Regression Suite, operational review, recovery evidence, client/owner approval, integrations, and production validation remain outstanding or deferred.

## Confirmed Lessons

### Validate node parameter storage types

Edit Fields / Set v3.4 JSON mode requires `jsonOutput` to be stored as a serialized JSON string. A structurally correct fixture can still fail at runtime when the node parameter uses the wrong storage type. Saved node configuration and runtime behavior should both be checked before expanding test coverage.

### Compile-check Code-node regular expressions

Schema validation alone did not expose the invalid escaped backtick in a JavaScript Unicode regex. Code-node JavaScript should receive a syntax compilation check in addition to node-schema and workflow-graph validation.

### Keep controlled DEV failures observable

The inactive, dummy-data-only design exposed both defects without credentials, external writes, notifications, or client-data risk. Preserving inert payloads and manual execution boundaries made the fixes narrow and reviewable.

### Use temporary pin data for isolated fixtures

Temporary pin data can isolate one dummy fixture per manual DEV execution without changing the saved Set node or workflow version. Each execution should confirm the pinned Set Sample Lead output and Final Output, and a post-batch inspection should verify that the workflow remains inactive and unchanged.

### Test both sides of inclusive scoring thresholds

Boundary tests should cover the value immediately below a threshold and the threshold itself. The budget executions confirmed that `499.99`, `500`, `1999.99`, `2000`, and `5000` enter the intended scoring bands and preserve the exact reason-code order.

### Compress release validation by risk, not convenience

A smaller release suite remains credible when every selected case has an explicit risk purpose and the omitted tests remain visible in an Extended Regression Suite. Combining boundary, routing, identity, null, contract, notification, timestamp, and suspicious-input coverage produced a 25-test release gate without renumbering or discarding any existing test.

### Separate demo acceptance from production readiness

A controlled demo can have a complete, evidence-backed acceptance gate without implying production readiness. The 25-test Core Release Suite closes the inactive DEV demo phase, while the Extended Regression Suite, recovery, operational approval, integrations, and production smoke tests remain separate gates.

### Retain evidence boundaries

TC-001 is recorded as passed from the result supplied for its documentation update; its successful execution ID was not supplied and must not be invented. The other 24 Core Release Suite tests have direct execution evidence recorded in [[Test Results]]. No Extended Regression Suite test is treated as passed.

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

- Approved demo requirements and architecture.
- Dummy-data Core Release Suite results and issue records.
- Version history and review decisions.
- Operational, recovery, integration, and production evidence if live deployment is later proposed.

## Related Notes

- [[Test Results]]
- [[Issues and Fixes]]
- [[Known Limitations]]
- [[Case Study]]
