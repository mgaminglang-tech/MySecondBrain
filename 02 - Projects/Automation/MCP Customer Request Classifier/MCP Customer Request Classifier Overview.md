---
type: project
status: demo-complete
phase: demo-closure
owner: Mervin
production_ready: false
priority: low
created: 2026-07-22
updated: 2026-07-24
tags:
  - project
  - automation
  - n8n
  - mcp
---

# MCP Customer Request Classifier Overview

## Objective

Document and verify a safe n8n MCP test workflow that classifies a sample customer request and generates a deterministic draft response without credentials or external services.

## Workflow

- **n8n workflow:** `MCP Test - Customer Request Classifier`
- **Workflow ID:** `9WNiW4plfGnFgvMX`
- **Operational state:** Inactive
- **Credentials:** None
- **Nodes:** Six core n8n nodes
- **Connections:** Five linear connections

## Purpose

The workflow demonstrates that the connected n8n MCP can create and validate a credential-free workflow while preserving existing workflows. It normalizes test input, applies ordered keyword rules, creates a category-specific draft response, and returns a controlled output schema.

## Current Status

The sample Access test completed successfully in manual execution `6947`. The observed category was `Access`, confidence was `0.95`, and `needs_human_review` was `false`.

Both the Access and Refund Request branches were tested successfully. The Refund Request test returned category `Refund Request`, confidence `0.95`, and `needs_human_review: true`.

The Refund execution ID was not recorded and is unavailable. The workflow remained inactive, and no credentials or production systems were used.

The project is demo-complete but is not production-ready. The workflow has not been published for production execution.

## Output Fields

- `name`
- `original_message`
- `category`
- `confidence`
- `draft_response`
- `needs_human_review`

## Next Action

Decide whether to archive the demo project or continue with a future version.

## Related Notes

- [[02 - Projects/Automation/MCP Customer Request Classifier/Architecture|Architecture]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Test Results|Test Results]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Issues and Fixes|Issues and Fixes]]
- [[02 - Projects/Automation/MCP Customer Request Classifier/Lessons Learned|Lessons Learned]]
- [[02 - Projects/Projects|Projects]]
