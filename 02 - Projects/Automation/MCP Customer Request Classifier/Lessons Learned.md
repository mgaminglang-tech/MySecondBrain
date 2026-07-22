---
type: project-note
status: active
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - n8n
  - lessons-learned
---

# Lessons Learned

## Workflow Design

- A deterministic customer-request classifier can be built with core Set nodes and no AI model or external API.
- Separating input, normalization, classification, response generation, and final shaping makes each stage easier to inspect.
- Limiting the Final Output node to a defined schema prevents intermediate fields from leaking into downstream use.

## Classification

- Keyword order matters when one message matches multiple categories.
- The Access test matched `access`, `password`, and `not working`; ordered evaluation correctly selected Access before Technical Support.
- A defined General Question fallback prevents unmatched requests from being dropped.
- Confidence values should be documented as deterministic rule outputs rather than model probabilities.

## Safety and Verification

- Credential-free core nodes are suitable for a controlled MCP connectivity and workflow-creation test.
- Node-level and workflow-level validation should pass before workflow creation.
- Post-creation inspection should confirm node count, connections, credential usage, and inactive state.
- A successful manual test does not require publishing or activating the workflow.
- Both the Access and Refund Request branches were tested successfully while the workflow remained inactive.

## Verified Branches

The Access branch correctly avoided human review, while the Refund Request branch correctly enabled the human-review safeguard.

## Related Notes

- [[02 - Projects/Automation/MCP Customer Request Classifier/MCP Customer Request Classifier Overview|Overview]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Architecture|Architecture]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Test Results|Test Results]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Issues and Fixes|Issues and Fixes]]
