---
type: project-note
status: active
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - n8n
  - troubleshooting
---

# Issues and Fixes

## Current Issues

No blocking issue was observed during the successful Access test.

## Design Considerations

| Consideration | Resolution |
|---|---|
| The sample contains both Access keywords (`access`, `password`) and a Technical Support phrase (`not working`). | Rules are intentionally ordered, so Access is selected before Technical Support. |
| Confidence behavior was not part of the original keyword rules. | Known keyword matches use `0.95`; the General Question fallback uses `0.60`. |
| Refund requests require human review while other categories do not. | `needs_human_review` evaluates to `true` only when the category is Refund Request. |
| The test must not depend on accounts or external services. | The workflow uses core Set nodes, fixed test data, and no credentials. |
| Production execution must remain disabled. | The workflow was created as an inactive draft and was not published. |

## Open Verification

- [ ] Run the Refund Request branch test.
- [ ] Confirm the observed category is `Refund Request`.
- [ ] Confirm `needs_human_review` is `true`.

## Related Notes

- [[02 - Projects/Automation/MCP Customer Request Classifier/MCP Customer Request Classifier Overview|Overview]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Architecture|Architecture]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Test Results|Test Results]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Lessons Learned|Lessons Learned]]
