---
type: case-study
status: draft
completion: incomplete
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - case-study
  - incomplete
---

# Lead Qualification Practice Case Study

## Current Status

Draft and incomplete. This note must not describe planned work as delivered or claim results without evidence.

## Publication Safety

- [ ] Publication or anonymization is approved.
- [ ] No secrets, private identifiers, or unredacted data are included.
- [ ] Outcomes are supported by evidence.
- [ ] Limitations and assumptions are disclosed.
- [ ] Planned work is clearly separated from completed work.

## Planned Context

Demo Sales Company wants to explore a repeatable process for reviewing lead completeness, applying transparent qualification rules, and preparing qualified leads for sales follow-up.

## Planned Solution

The proposed design uses n8n to normalize and validate a dummy lead, calculate an explainable score, assign a status, recommend routing, and prepare destination-neutral storage and notification payloads.

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

The proposed v0.1 design is a linear ten-node workflow with no IF, Switch, Merge, credentials, external integrations, or side effects.

## Verified Results

No verified results are available. Development and testing have not started.

| Metric | Baseline | Observed result | Evidence |
|---|---|---|---|
| Manual review time | not measured | not available | none |
| Qualification consistency | not measured | not available | none |
| Routing accuracy | not measured | not available | none |
| Duplicate rate | not measured | not available | none |

## Completion Requirements

- Approved scope and publication status.
- Evidence-backed development and test results.
- Approved baseline and outcome metrics.
- Accurate limitations, lessons, and operational controls.
- Client approval for any named case study.

## Related Notes

- [[Lead Qualification Practice Overview]]
- [[Test Results]]
- [[Known Limitations]]
- [[Lessons Learned]]
- [[Client Handover]]
