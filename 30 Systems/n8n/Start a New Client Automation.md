---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Start a New Client Automation

## Purpose

Start an n8n automation with a clear outcome, defined ownership, known integration boundaries, and an approved DEV entry point.

## Preconditions

- A named project owner and decision-maker are available.
- The requested outcome can be clarified without using production credentials or customer data.

## Procedure

1. Clarify the business outcome, current process, success evidence, important exclusions, and required manual steps.
2. Search for an existing project and use its current home; create one project home only when separately authorized.
3. Identify each system, integration, trigger type, data source, destination, and required external action.
4. Determine whether the immediate scope is DEV, optional STAGING, or PROD. Treat each environment as a separate authorization boundary.
5. Identify data sensitivity and the approved dummy or sanitization approach under [[Client Data Handling Standard]].
6. Identify required credentials by non-secret name, environment, owner, permission, and approved storage location under [[Credential and Secrets Management Standard]].
7. Confirm who may approve access, workflow changes, test execution, external actions, publication, activation, and production release.
8. Define expected input, output, failure behavior, duplicate or idempotency needs, and the smallest complete test strategy.
9. Record unresolved dependencies, risks, assumptions, and acceptance criteria.
10. Obtain authorization for the exact inactive DEV build before modifying n8n.

## Verification

- The outcome, scope, systems, triggers, external actions, and acceptance criteria are clear.
- Data handling and environment boundaries are documented.
- Credential ownership is known without recording secret values.
- The test strategy covers critical expected and failure behavior.
- The project home and authorized next action are unambiguous.

## Stop / Escalate When

- Scope, ownership, data permission, credential ownership, recipient, destination, or production intent is unclear.
- The request would require production data, activation, publication, or external actions without explicit approval.
- Required behavior would need to be invented.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Client Data Handling Standard]]
- [[Credential and Secrets Management Standard]]
- [[Agent Operating Standard]]

## Do

- Define one approved inactive DEV starting point.
- Record decisions and unknowns before building.

## Don’t

- Activate workflows or use production data during initiation.
- Request or record credential values.
