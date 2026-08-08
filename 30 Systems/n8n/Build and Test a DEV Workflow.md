---
type: system-standard
system: Merv's AI OS
status: draft
version: 1.0
---

# Build and Test a DEV Workflow

## Purpose

Build and verify a coherent n8n workflow in an inactive DEV boundary before production consideration.

## Preconditions

- Requirements, architecture, acceptance criteria, and the approved build scope are available.
- Dummy or sanitized fixtures and non-production destinations are defined.
- Required DEV credential references and owners are known.

## Procedure

1. Create or update only the approved DEV workflow and keep it inactive.
2. Build a coherent end-to-end path from controlled trigger to controlled output; normalize input and validate it before side effects.
3. Configure only approved DEV credentials, resource identifiers, recipients, URLs, and destinations.
4. Keep external actions mocked, disabled, pinned, or directed to approved test systems unless the exact action is authorized.
5. Validate node parameters, expressions, code syntax, connections, settings, credential references, and workflow structure before execution.
6. Define consolidated scenarios covering the critical happy path and, when relevant, boundaries, empty or invalid input, duplicates or idempotency, retries, fallback, and failure behavior.
7. Run only the approved scenarios with controlled fixtures and compare expected with actual results.
8. Group related fixes, validate the changed configuration, and rerun affected scenarios. Run broader regression only when justified.
9. Record verified outcomes, evidence references, defects, limitations, and not-run scenarios; do not infer results.
10. Remove temporary pin data or fixtures when required and confirm the saved workflow remains inactive with no unintended external effects.

## Verification

- The workflow is inactive and uses only approved DEV references.
- Nodes, connections, expressions, code, and settings pass the applicable validation.
- Critical expected, duplicate or idempotency, fallback, and failure scenarios have evidence where relevant.
- Actual results and remaining limitations are recorded accurately.
- No unintended production destination or external action was reached.

## Stop / Escalate When

- A test reaches production data, credentials, recipients, or destinations.
- An uncontrolled external action or sensitive-data exposure occurs.
- A failure makes later test results unreliable.
- Additional execution or workflow scope requires new approval.

## Related Standards

- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Client Data Handling Standard]]
- [[Credential and Secrets Management Standard]]
- [[Agent Operating Standard]]

## Do

- Validate configuration before execution.
- Prefer a small complete scenario set over unnecessary micro-tests.

## Don’t

- Modify a production workflow as a DEV shortcut.
- Report an unexecuted or blocked scenario as passed.
