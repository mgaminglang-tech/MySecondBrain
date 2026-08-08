---
type: project-note
status: draft
client: CLIENT_NAME
version: v0.1.0
created: "{{date:YYYY-MM-DD}}"
updated: "{{date:YYYY-MM-DD}}"
tags:
  - client-automation
  - development
---

# Development Plan

## Objective

Define how the approved automation will be built and reviewed in DEV.

## Development Rules

- Workflow name: `DEV - Client or Project - Workflow Name`
- Credential names: `DEV - Service - Purpose`
- Data: dummy or sanitized only
- Side effects: test destinations, mocks, or controlled fixtures only
- Initial version: `v0.1.0`
- STAGING: optional and documented only if used

## Planned Components

| Component | Purpose | Owner | Dependency | Done criterion |
|---|---|---|---|---|
|  |  |  |  |  |

## Build Sequence

- [ ] Create inactive DEV workflow.
- [ ] Configure test trigger and sample input.
- [ ] Normalize and validate inputs.
- [ ] Build the main success path.
- [ ] Add error handling and alert paths.
- [ ] Add idempotency, retries, timeouts, and empty-path handling.
- [ ] Connect test credentials and destinations.
- [ ] Review node settings and connections.
- [ ] Execute the test plan.
- [ ] Export and version the validated workflow.

## Version Plan

| Version | Planned change | Approval required |
|---|---|---|
| `v0.1.0` | Initial development version | Development authorization |
| `v0.2.0` | Development feature update | Scope review |
| `v0.2.1` | Development bug fix | Reviewer verification |
| `v1.0.0` | First approved production release | Explicit PROD approval |

## Failure Handling

- Build failures remain in DEV.
- Unexpected production access or data exposure stops work immediately.
- Defects are recorded in [[Templates/Client Automation/Issues and Fixes|Issues and Fixes]].
- A known-good DEV export is preserved before risky changes.

## Definition of Done

- [ ] Requirements are implemented or explicitly deferred.
- [ ] DEV tests have evidence.
- [ ] Failure and rollback behavior are documented.
- [ ] No PROD credentials or unredacted client data were used.
- [ ] Reviewer decision and limitations are recorded.

## Approval

- Developer:
- Reviewer:
- Project owner:
- Date:

## Related Notes

- [[Templates/Client Automation/Architecture|Architecture]]
- [[Templates/Client Automation/Test Plan|Test Plan]]
- [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
