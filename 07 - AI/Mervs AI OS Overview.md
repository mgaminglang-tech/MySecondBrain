---
type: ai-system
status: foundation
owner: Mervin
created: 2026-07-24
updated: 2026-07-24
tags:
  - ai-os
  - governance
---

# Mervs AI OS Overview

## Purpose

Mervs AI OS is a governed operating system for using structured knowledge, Codex, automation, and verified evidence without confusing analysis with authorization. It supports personal, demo, internal, and client work while keeping Mervin in control of consequential decisions.

## Component Responsibilities

| Component | Responsibility |
|---|---|
| Obsidian | Stores durable knowledge, project state, evidence, decisions, SOPs, prompts, and links. |
| AGENTS.md | Defines universal repository safety, security, approval, Git, and runtime boundaries. |
| Codex | Inspects context, reports findings, performs approved edits, and validates results within the authorized scope. |
| n8n | Runs approved workflow logic in the authorized environment and state. |
| MCP | Provides scoped access to connected systems; audits remain read-only unless a specific write is approved. |
| Git and GitHub | Provide change review, history, recovery, and collaboration after explicit Git authorization. |
| Mervin | Owns approvals, resolves ambiguity, accepts risk, and authorizes credentials, side effects, activation, deployment, and archiving. |

No component has autonomous production authority.

## Folder Routing Map

| Folder | Use |
|---|---|
| `00 - Inbox` | Temporary, unverified capture awaiting processing. |
| `01 - Dashboard` | Navigation, current status, next actions, and high-level visibility. |
| `02 - Projects` | Time-bound work, project evidence, decisions, and delivery state. |
| `03 - Areas` | Ongoing responsibilities, policies, and operating standards. |
| `04 - Knowledge` | Reusable concepts, verified technical knowledge, and troubleshooting. |
| `05 - Resources` | External references, tools, courses, and supporting material. |
| `06 - SOPs` | Repeatable procedures, controls, verification, and rollback guidance. |
| `07 - AI` | AI prompts, governance, agent patterns, evaluations, and audit records. |
| `08 - Journal` | Personal dated records; access and changes require explicit instruction. |
| `09 - Archive` | Approved historical material that is no longer current. |
| `Templates` | Reusable blank structures; duplicate before project use. |
| `Assets` | Attachments and binary evidence; preserve paths and links. |

## Context Model

- **Expertise context** is durable knowledge: AGENTS.md, current policies, SOPs, templates, technical knowledge, and reusable AI guidance.
- **Situational context** is task-specific: the current request, project metadata, approved requirements, runtime evidence, test results, blockers, owners, dates, and next actions.

Expertise context guides method. Situational context determines what is true and authorized now.

## Standard Operating Cycle

**Inspect → Report → Approve → Edit → Validate → Git review**

1. Inspect relevant sources without changing them.
2. Report evidence, conflicts, risks, and proposed scope.
3. Wait for Mervin’s approval when edits or consequential actions are required.
4. Edit only the approved files or systems.
5. Validate content, behavior, safety boundaries, and diff scope.
6. Review Git status and diffs; commit or push only when separately authorized.

## Explicit Approval Required

- Editing outside the stated scope or making broad structural changes
- Deleting, renaming, moving, archiving, restoring, or overwriting material
- Assigning or changing credentials, recipients, destinations, or permissions
- MCP writes or changes to connected systems
- Workflow creation, modification, execution beyond an approved test, activation, or deactivation
- External writes, sends, side effects, live-data use, or production changes
- Git staging, commits, pushes, pulls, merges, rebases, resets, or branch changes

## Read-only by Default

- Vault, project, link, task, security, and consistency audits
- Source-authority and freshness checks
- Git status and diff inspection
- MCP capability, connectivity, naming-conflict, and environment audits
- Workflow, credential-reference, configuration, and execution-history inspection
- Production-readiness, archive-readiness, and risk reviews

Runtime evidence may establish facts but never grants permission to change runtime systems.

## Related Notes

- [[07 - AI/Mervs AI OS Audit Prompt|Mervs AI OS Audit Prompt]]
- [[07 - AI/Source Authority and Freshness Rules|Source Authority and Freshness Rules]]
- [[07 - AI/Audits/Audits|Audits]]
- [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]]

