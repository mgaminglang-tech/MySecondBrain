---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Project Hub Standard

## Purpose

Define the required default entry note for every active project.

## Core Rule

Every active project must have exactly one primary entry note named `Project Hub.md`.

The Project Hub is the default human and AI starting point. It summarizes the current approved state without duplicating deep documentation.

## Required Structure

```markdown
# <Project Name>

## Status
- State:
- Current Phase:
- Last Verified:
- Next Action:

## Goal
<One short paragraph describing the intended outcome.>

## Scope
- Included:
- Excluded:

## Current State
- What currently exists:
- What is working:
- What is not yet complete:

## Components
- <Important platforms, systems, tools, integrations, or components.>

## Architecture Summary
<Short high-level architecture. Link to a deep architecture note when one exists.>

## Hard Constraints
- <Safety boundaries, business rules, non-negotiable implementation constraints, and relevant context limits.>

## Key Decisions
- <Only decisions that materially affect implementation. Link to deeper decision notes when needed.>

## Open Items
- <Unresolved blockers, pending decisions, and known gaps.>

## Verification
- <Latest verified milestone and supporting tests or evidence.>

## Key Docs
- [[Architecture]]
- [[Implementation Plan]]
- [[Test Plan]]
- [[Known Limitations]]
```

Include only links that exist and matter to the project.

## Operating Principles

The Project Hub must be:

- concise, current, and operational
- a summary of approved state
- the answer to what the project is, where it is now, what matters, what comes next, and where deeper detail lives

The Project Hub must not be:

- a history dump
- a full implementation manual
- a chat transcript
- a raw test log
- an encyclopedia

## Token-Efficiency Rule

Keep the Project Hub roughly 500–1,500 words whenever practical.

If it grows too large:

1. Preserve the current-state summary, constraints, decisions, verification, and next action.
2. Extract deep details into focused linked notes.
3. Keep only the links and minimum context needed to navigate those notes.

## Update Rule

- Update the Project Hub at meaningful state changes or verified milestones.
- Do not update it after every minor action.
- Preserve stable decisions and constraints during focused updates.
- Never claim a state, test, or milestone without supporting evidence.

## One Project, One Hub

- Maintain exactly one `Project Hub.md` per project.
- Do not create competing summary notes such as `Project Summary`, `Current State`, `Master Overview`, or `Latest Status` when the Project Hub serves that role.
- Put deep material in purpose-specific linked notes rather than another overview.

## Agent Rules

- Read `Project Hub.md` before deep project documentation.
- Use it to decide which deeper notes are relevant.
- Do not assume it contains every implementation detail.
- Follow repository instruction precedence and applicable shared standards.
- Make focused updates; do not rewrite the whole hub after small changes.
- Preserve verified state, stable decisions, constraints, and evidence links.

## Do / Don't

| Do | Don't |
| --- | --- |
| Keep one concise, current entry point. | Create competing project summaries. |
| Record verified state and the exact next action. | Invent status, evidence, or completion. |
| Link to focused deep notes. | Copy all deep documentation into the hub. |
| Update at meaningful milestones. | Rewrite the hub after every minor action. |
| Preserve stable constraints and decisions. | Remove durable context during a focused update. |
