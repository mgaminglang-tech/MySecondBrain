---
type: sop
status: draft
created: 2026-07-22
updated: 2026-07-22
tags:
  - sop
  - n8n
  - development
---

# Build and Test a DEV Workflow

## Purpose

Build and verify an n8n workflow safely in DEV before any production consideration.

## When to Use

Use for new workflows, features, bug fixes, and production-incident reproductions.

## Requirements

- Approved requirements and architecture
- Development plan and test plan
- Dummy or sanitized test data
- Test credentials named `DEV - Service - Purpose`
- Defined acceptance criteria, error behavior, and rollback approach

## Safety Considerations

- Never use PROD credentials or unredacted production data in DEV.
- Keep real side effects disabled, mocked, pinned, or directed to test systems.
- Confirm recipient addresses, database targets, and webhook endpoints are non-production.
- Do not modify an existing PROD workflow as a development shortcut.

## Ownership and Approval Gates

- Developer owns the DEV build and evidence.
- Reviewer checks architecture, data handling, tests, error paths, and version notes.
- Project owner approves readiness for a PROD deployment plan.
- Codex or MCP may modify DEV within the approved scope but may not modify PROD without explicit approval.

## Procedure

1. Name the workflow `DEV - Client or Project - Workflow Name`.
2. Set the development version, starting with `v0.1.0`.
3. Build the smallest complete path from trigger to controlled output.
4. Normalize input immediately and document the expected schema.
5. Add validation before side effects.
6. Configure idempotency, duplicate handling, retries, timeouts, and error paths where applicable.
7. Use DEV credentials and non-production resource identifiers.
8. Add safe test inputs for expected, empty, invalid, duplicate, boundary, retry, and failure scenarios.
9. Execute tests manually or with controlled test triggers.
10. Record inputs, expected results, observed results, execution IDs, and defects in [[Templates/Client Automation/Test Results|Test Results]].
11. Fix defects in DEV, incrementing the version appropriately:
    - `v0.2.0` for a development feature update
    - `v0.2.1` for a development bug fix
12. Export a validated DEV version according to [[06 - SOPs/n8n/Export and Version an n8n Workflow|Export and Version an n8n Workflow]].
13. Obtain review before planning PROD promotion.

## Verification

- [ ] Workflow name and version follow standards.
- [ ] Only DEV credentials and test destinations are used.
- [ ] Test data is dummy or sanitized.
- [ ] Nodes, connections, expressions, and settings were reviewed.
- [ ] Expected and failure-path tests have evidence.
- [ ] Error handling and alerts behave as designed in DEV.
- [ ] No unintended side effects occurred.
- [ ] Reviewer decision and remaining limitations are recorded.

## Failure Handling

Stop the test if it reaches a production destination, exposes client data, or produces uncontrolled side effects. Disable the affected DEV path, preserve safe evidence, notify the project owner, and correct the environment configuration before retesting.

## Rollback

Restore the last validated DEV export or reverse the documented development change. Keep the failed version and evidence when useful for troubleshooting; do not overwrite the only known-good backup.

## Troubleshooting

- **No data reaches a downstream branch:** Add explicit empty-path handling and verify item counts.
- **Credential errors:** Confirm the node references the intended DEV credential without exposing its value.
- **Unexpected duplicate actions:** Add an idempotency key or deduplication gate and retest.
- **Test passes only with production data:** Improve dummy or sanitized fixtures rather than copying production data.

## Related Notes

- [[03 - Areas/Automation Operations/Development and Production Policy|Development and Production Policy]]
- [[03 - Areas/Automation Operations/Client Data Handling Policy|Client Data Handling Policy]]
- [[Templates/Client Automation/Test Plan|Test Plan]]
- [[Templates/Client Automation/Issues and Fixes|Issues and Fixes]]
- [[06 - SOPs/n8n/Promote DEV Workflow to PROD|Promote DEV Workflow to PROD]]
