---
type: resource
status: active
category: prompts
---

# Automation Project Prompt Library

## How to Use

- Select only the prompt needed for the current lifecycle stage; do not paste this whole library into an agent.
- Replace bracketed placeholders before use.
- For an established project, `Project Hub.md` is the default context. Read deeper documents only when the task requires them.
- Each prompt starts with `AGENTS.md`, names the smallest relevant standards, verifies its result, and stops at the requested boundary.
- Approval for one phase does not authorize the next phase, production, credentials, activation, external actions, migration, or Git operations.

## Clarify / Create Project

```text
Read and follow AGENTS.md.

Clarify and, only when justified and authorized, create the automation project:
[PROJECT REQUEST OR SOURCE]

Read [[Project Routing Standard]], [[Project Naming Standard]], and the Clarify stage of [[Project Lifecycle Standard]]. Search exact and near matches first. Determine the primary outcome, one project home, scope, exclusions, constraints, success criteria, unknowns, and approval boundaries.

If creation is authorized, create exactly one project folder and one Project Hub.md. Populate only known information. Do not generate a full document suite or begin planning/building unless requested.

Verify the created files and report assumptions, open questions, and the exact next action. Stop.
```

## Project / Status Update

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Update only:
[APPROVED FILES]

Use Project Hub.md as the current-state entry point and [SOURCE MATERIAL] as the update evidence. Follow [[AI Context Standard]] and read only deep documents needed to resolve the update.

Separate verified decisions and outcomes from assumptions, blockers, and deferred ideas. Update Project Hub only if a meaningful phase, milestone, blocker, decision, next action, or verification state changed.

Validate consistency and report files changed and unresolved conflicts. Do not change workflows or external systems. Stop.
```

## Plan / Pre-Build Review

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Operate read-only. Read Project Hub.md, [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]], and only the relevant requirements, architecture, and test sections.

Assess the outcome, scope, executable contracts, data handling, credential boundaries, integrations, architecture, failure behavior, duplicate/idempotency needs, test strategy, acceptance criteria, dependencies, and unresolved risks.

Return GO, CONDITIONAL GO, or NO-GO for the requested inactive DEV scope with exact evidence, blockers, and files that would need changes. Make no changes. Stop.
```

## Troubleshoot / Resolve Approved Blocker

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Approved blocker and scope:
[BLOCKER AND APPROVED ACTION]

Read Project Hub.md and only the deep documents directly relevant to the blocker. Follow [[Agent Operating Standard]]. Diagnose the confirmed cause before editing. Resolve only the approved blocker in [APPROVED FILES OR SYSTEM].

Preserve unsupported gates as incomplete. Validate the affected behavior, update durable state only if meaningful, and report resolved and remaining blockers. Do not expand into build, testing, production, or Git work without explicit scope. Stop.
```

## Configuration Audit

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Perform a strictly read-only n8n capability and configuration audit for [WORKFLOW SCOPE]. Read Project Hub.md, the relevant architecture sections, and the capability-audit section of [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Check connectivity, applicable versions, required nodes, parameters, expressions, code syntax, connections, credentials by non-secret reference, environment compatibility, naming conflicts, triggers, external-action risks, and inactive state where observable.

Do not create, edit, execute, activate, deactivate, import, publish, delete, or change settings or credentials.

Return GO, CONDITIONAL GO, or NO-GO with evidence, unresolved blockers, and the recommended inactive DEV configuration. Stop.
```

## Build

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Approved inactive DEV build scope:
[BUILD SCOPE]

Read Project Hub.md, the relevant approved architecture and requirements sections, and [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]. Build only the approved coherent end-to-end DEV flow using dummy or sanitized data and approved non-production references.

Validate saved node configuration, expressions, code syntax, connections, credential references, external nodes, and inactive state. Do not execute, activate, publish, or enable unapproved external actions.

Report the created or changed structure, validation evidence, limitations, and blockers. Stop before testing.
```

## Test

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]
Approved workflow and test scope:
[WORKFLOW REFERENCE]
[TEST SCENARIOS]

Read Project Hub.md, the relevant test expectations, and [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]. Execute only the approved consolidated scenarios with approved fixtures.

Cover the critical happy path and, when relevant, boundaries, duplicates/idempotency, invalid input, fallback, and failure behavior. Stop when a failure makes later results unreliable. Do not fix defects unless that repair is separately approved.

Record expected versus actual results and PASS, FAIL, BLOCKED, or NOT RUN evidence. Clear temporary artifacts when required, confirm final inactive state, report results, and stop.
```

## Demo Review

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Operate read-only. Read Project Hub.md and only the evidence, test results, issues, and limitations needed to review the accepted demo scope.

Confirm which features are verified, the workflow state, disclosed limitations, blocked or not-run work, and separation between demo acceptance and production readiness.

Return GO, CONDITIONAL GO, or NO-GO for the stated demo with exact evidence and blockers. Do not execute tests, change files or workflows, or imply production approval. Stop.
```

## Production Readiness

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Operate read-only. Read Project Hub.md, the production-promotion section of [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]], and only the relevant release, test, security, credential, backup, rollback, monitoring, recovery, support, and limitation evidence.

Assess the exact release scope, verified DEV evidence, known limitations, environment mappings, credential ownership, external side effects, recovery readiness, smoke test, deployment window, monitoring, handover, and explicit approvals.

Do not assign credentials, use production data, enable side effects, activate, publish, deploy, or modify production.

Return GO, CONDITIONAL GO, or NO-GO with missing evidence and unresolved ownership. Stop and wait for a separately approved production scope.
```

## Handover

```text
Read and follow AGENTS.md.

Project:
[PROJECT PATH]

Read Project Hub.md and only the current workflow inventory, evidence, dependencies, limitations, credential ownership, backup, recovery, monitoring, maintenance, support, and acceptance records needed for handover. Use [[30 Systems/n8n/Client Automation Handover|Client Automation Handover]].

Assess the final verified state, receiving owner, access process, recovery readiness, support boundary, open actions, accepted risks, and escalation path. Refer to credentials by non-secret name only.

Return GO, CONDITIONAL GO, or NO-GO for handover with exact remaining actions. Do not transfer secrets, archive or move files, or perform Git operations. Stop.
```

## Related Standards

- [[Project Routing Standard]]
- [[Project Naming Standard]]
- [[Project Lifecycle Standard]]
- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[AI Context Standard]]
- [[Agent Operating Standard]]
