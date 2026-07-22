---
type: project-note
status: active
created: 2026-07-22
updated: 2026-07-22
tags:
  - automation
  - n8n
  - architecture
---

# Architecture

## Workflow Flow

`Manual Trigger` → `Set Sample Customer Request` → `Normalize Input` → `Classify Request` → `Generate Draft Response` → `Final Output`

## Nodes

| Node | Core type | Responsibility |
|---|---|---|
| Manual Trigger | `n8n-nodes-base.manualTrigger` | Starts a manual test run. |
| Set Sample Customer Request | `n8n-nodes-base.set` | Supplies the credential-free test name and message. |
| Normalize Input | `n8n-nodes-base.set` | Trims the name and maps the message to `original_message`. |
| Classify Request | `n8n-nodes-base.set` | Applies ordered keyword rules and assigns category and confidence. |
| Generate Draft Response | `n8n-nodes-base.set` | Produces the category-specific response and human-review flag. |
| Final Output | `n8n-nodes-base.set` | Returns only the six required output fields. |

## Connections

1. Manual Trigger → Set Sample Customer Request
2. Set Sample Customer Request → Normalize Input
3. Normalize Input → Classify Request
4. Classify Request → Generate Draft Response
5. Generate Draft Response → Final Output

## Classification Rules

Rules are evaluated from top to bottom.

| Keywords | Category |
|---|---|
| `refund` | Refund Request |
| `access`, `login`, `password` | Access |
| `billing`, `invoice`, `payment` | Billing |
| `schedule`, `appointment`, `booking` | Scheduling |
| `error`, `bug`, `technical`, `not working` | Technical Support |
| No match | General Question |

Known keyword matches receive confidence `0.95`; the General Question fallback receives `0.60`. Only Refund Request sets `needs_human_review` to `true`.

## Safety Design

- The workflow uses only core n8n nodes.
- No credentials are configured.
- No node calls an external service.
- Input is fixed test data.
- The workflow is inactive.

## Related Notes

- [[02 - Projects/Automation/MCP Customer Request Classifier/MCP Customer Request Classifier Overview|Overview]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Test Results|Test Results]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Issues and Fixes|Issues and Fixes]]
