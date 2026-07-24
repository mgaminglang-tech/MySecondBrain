---
type: ai-prompt-library
status: active
created: 2026-07-24
updated: 2026-07-24
tags:
  - ai
  - prompts
  - client-automation
  - project-management
---

# Automation Project Prompt Library

## Purpose

Provide concise phase-specific prompts for automation projects governed by [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

## Usage Guide

- Use one prompt per major phase.
- Do not paste the full project context when it already exists in Obsidian.
- Replace every bracketed placeholder before use.
- Refer to exact project paths, workflow IDs, document names, and test IDs.
- Request concise reports.
- Repeat high-risk restrictions only for production, credentials, destructive actions, and real external side effects.
- Keep the project-specific `Automation Project Checklist.md` current after approved work.

## 1. Create a Project from Client Details

```text
Read and follow AGENTS.md.

Use [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]] and [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]].

Create the automation project "[PROJECT NAME]" only inside:
[PROJECT PATH]/

Use these client details as intake evidence:
[CLIENT DETAILS OR SOURCE FILE]

Create the applicable project documents and a project copy of Automation Project Checklist.md. Treat that checklist, Requirements.md, and Architecture.md as the project source of truth. Use placeholders only for unknown facts and credentials.

Report created files, assumptions, open questions, and the discovery recommendation. Do not build or audit a workflow. Stop and wait for approval before the next phase.
```

## 2. Create or Update Documents from a Meeting Transcript

```text
Read and follow AGENTS.md.

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/

Use [TRANSCRIPT PATH] as the meeting source. Update only [APPROVED FILES]. Reconcile the project-specific Automation Project Checklist.md, Requirements.md, Architecture.md, and applicable plans without inventing decisions, approvals, credentials, or outcomes.

Separate confirmed decisions, assumptions, open questions, blockers, and deferred ideas. Report files changed and unresolved decisions. Do not change workflows or external systems. Stop and wait for approval.
```

## 3. Run a Strict Pre-development Review

```text
Read and follow AGENTS.md.

Use [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]] and review:
[PROJECT PATH]/

Operate read-only. Treat the project-specific Automation Project Checklist.md, Requirements.md, Architecture.md, Test Plan.md, and existing project evidence as authoritative.

Assess scope, executable contracts, security, privacy, credentials, architecture, test coverage, acceptance criteria, risks, and document conflicts. Return GO, CONDITIONAL GO, or NO-GO with exact files needing changes.

Make no changes. Stop and wait for approval.
```

## 4. Resolve Approved Blockers

```text
Read and follow AGENTS.md.

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/

Resolve only these approved blockers:
[APPROVED BLOCKERS]

Update only [APPROVED FILES]. Use the project-specific Automation Project Checklist.md, Requirements.md, Architecture.md, Test Plan.md, and latest review as the source of truth. Preserve unsupported gates as incomplete.

Validate consistency and report resolved and remaining blockers. Do not expand scope. Stop and wait for approval before development or MCP use.
```

## 5. Run a Read-only n8n MCP Capability Audit

```text
Read and follow AGENTS.md.

Use [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/

Use n8n MCP strictly read-only. Audit support for the workflow defined by the project-specific Automation Project Checklist.md, Requirements.md, and Architecture.md. Check connectivity, available version information, required nodes and versions, expressions, compatibility, naming conflicts, credentials, and environmental blockers.

Do not create, edit, execute, activate, deactivate, delete, import, publish, or change credentials or settings.

Return GO, CONDITIONAL GO, or NO-GO with the recommended inactive DEV architecture. Stop and wait for approval.
```

## 6. Build an Approved Inactive DEV Workflow

```text
Read and follow AGENTS.md.

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/
Workflow name:
[DEV WORKFLOW NAME]

Use the project-specific Automation Project Checklist.md, Requirements.md, Architecture.md, and Development Plan.md as the source of truth. Create or update only the approved inactive DEV workflow with approved dummy or sanitized data.

Validate the saved workflow, nodes, connections, credential references, external nodes, and inactive state. Do not execute or activate it.

Report the workflow ID, structure, validation result, and blockers. Stop and wait for approval before testing.
```

## 7. Execute an Approved Core Release Suite

```text
Read and follow AGENTS.md.

Use [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/
Workflow ID:
[WORKFLOW ID]
Approved Core Release tests:
[TEST IDS]

Use the project-specific Automation Project Checklist.md, Requirements.md, Architecture.md, Test Plan.md, and current Test Results.md as the source of truth. Execute only the listed tests independently with approved fixtures.

Keep the workflow inactive. Stop the batch if a failure or runtime error makes later results unreliable. Record exact evidence and clear temporary test artifacts.

Report passed, failed, blocked, differences, workflow changes, and cleanup status. Do not fix defects or run more tests. Stop and wait for approval.
```

## 8. Run a Final Demo-readiness Review

```text
Read and follow AGENTS.md.

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/
Workflow ID:
[WORKFLOW ID]

Operate read-only. Review the project-specific Automation Project Checklist.md, Requirements.md, Architecture.md, Test Plan.md, Test Results.md, Issues and Fixes.md, and Known Limitations.md.

Confirm the accepted test gate, inactive state, demo scope, disclosed limitations, deferred work, and separation from production readiness. Return GO or NO-GO for the demo with exact blockers and documents requiring updates.

Do not execute tests or change files or workflows. Stop and wait for approval.
```

## 9. Prepare for Real-client Production Review

```text
Read and follow AGENTS.md.

Use [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/
Candidate workflow ID:
[WORKFLOW ID]

Operate read-only. Use the project-specific Automation Project Checklist.md, Requirements.md, Architecture.md, Test Plan.md, Test Results.md, Deployment Checklist.md, Credentials Checklist.md, Backup and Restore.md, Maintenance Guide.md, and Known Limitations.md as the source of truth.

Assess production scope, security, privacy, credential ownership, external side effects, tests, backup, rollback, monitoring, recovery, support, handover, and explicit approvals.

Do not assign credentials, use real data, enable side effects, activate, deploy, or change production. Return GO, CONDITIONAL GO, or NO-GO with missing evidence. Stop and wait for explicit production authorization.
```

## 10. Finalize Handover and Archive Readiness

```text
Read and follow AGENTS.md.

Follow [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]].

Project:
[PROJECT PATH]/

Use the project-specific Automation Project Checklist.md and all current project evidence as the source of truth. Review handover, ownership, credentials by name only, access, monitoring, recovery, maintenance, limitations, deferred work, case-study evidence, final status, phase, production readiness, and next action.

Assess the archive gate in [[09 - Archive/Archive|Archive]]. Do not invent acceptance, delete evidence, move files, archive the project, or perform Git operations.

Return GO, CONDITIONAL GO, or NO-GO for handover and archive readiness with exact remaining actions. Stop and wait for owner approval before any move, commit, or push.
```

## Related Notes

- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]
- [[Templates/Client Automation/Automation Project Checklist|Automation Project Checklist]]
- [[Templates/Client Automation/Client Discovery Checklist|Client Discovery Checklist]]
