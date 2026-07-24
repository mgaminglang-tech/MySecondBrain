---
type: case-study
status: draft
completion: incomplete
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-24
tags:
  - client-automation
  - case-study
  - incomplete
---

# Lead Qualification Practice Case Study

## Current Status

Draft and incomplete for publication. The controlled inactive DEV demo is complete and the evidence below is limited to verified workflow and test facts. No business outcome, client feedback, production result, or recovery result is claimed.

## Publication Safety

- [ ] Publication or anonymization is approved.
- [x] No secrets, private identifiers, or unredacted data are included.
- [x] Reported demo outcomes are supported by [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]].
- [x] Limitations and assumptions are disclosed.
- [x] Planned work is clearly separated from completed demo work.

## Demo Context

Demo Sales Company wants to explore a repeatable process for reviewing lead completeness, applying transparent qualification rules, and preparing qualified leads for sales follow-up.

## Implemented Demo Solution

The inactive DEV practice workflow uses n8n to normalize and validate a dummy lead, calculate an explainable score, assign a status, recommend routing, and prepare destination-neutral storage and notification payloads.

```text
Manual Trigger
→ Set Sample Lead
→ Normalize Input
→ Validate Required Fields
→ Generate Identity Hash — Crypto v2
→ Calculate Lead Score
→ Assign Qualification Status and Routing
→ Prepare Storage Record
→ Prepare Internal Notification
→ Final Output
```

The v0.1 demo is a linear ten-node workflow with no IF, Switch, Merge, credentials, external integrations, or side effects.

## Verified Results

- The workflow remained inactive and used dummy data only.
- The 25-test Core Release Suite passed: 25 passed, 0 failed, and 0 blocked.
- The complete v0.1 top-level and nested output contracts were demonstrated.
- Validation, scoring boundaries, statuses, routing, deterministic valid and invalid identity, null handling, notification behavior, timestamp handling, and suspicious-text handling were covered by the Core Release Suite.
- No credentials, external integrations, network requests, writes, sends, or real data were used.
- The 88-test Extended Regression Suite remains not run, and the ten v0.2 integration tests remain deferred.

| Metric | Baseline | Observed result | Evidence |
|---|---|---|---|
| Manual review time | not measured | not available | none |
| Core Release Suite | 25 selected demo tests | 25 passed; 0 failed; 0 blocked | [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]] |
| Output contract | Approved v0.1 contract | Demonstrated by Core Release Suite | [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]] |
| Workflow safety boundary | Inactive, dummy-only, no credentials or side effects | Preserved during controlled testing | [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]] |
| Duplicate rate | not measured | not available | none |

These results support a controlled practice demo only. They do not establish production performance, business savings, live routing accuracy, operational recovery, or client satisfaction.

## Completion Requirements

- Approved scope and publication status.
- Evidence-backed development and test results.
- Approved baseline and outcome metrics.
- Accurate limitations, lessons, and operational controls.
- Client approval for any named case study.
- Production evidence only if a future live deployment is separately approved.

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[02 - Projects/Automation/Lead Qualification Practice/Test Results|Test Results]]
- [[02 - Projects/Automation/Lead Qualification Practice/Known Limitations|Known Limitations]]
- [[02 - Projects/Automation/Lead Qualification Practice/Lessons Learned|Lessons Learned]]
- [[02 - Projects/Automation/Lead Qualification Practice/Client Handover|Client Handover]]
