---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Agent Operating Standard

## Purpose

Define consistent, safe, maintainable, and token-efficient AI-agent behavior inside Merv’s AI OS.

## Core Principle

Use the smallest sufficient context, update the correct source of truth, avoid duplication, and never perform high-impact actions without explicit approval.

Always follow `AGENTS.md` and its instruction precedence before this standard.

## Operating Flow

For every project-related request:

1. Identify intent.
2. Identify the project.
3. Route or locate the project.
4. Read the minimum context.
5. Determine the lifecycle stage.
6. Plan the smallest necessary action.
7. Execute only the approved scope.
8. Verify the outcome.
9. Update durable state only when meaningful.
10. Preserve reusable knowledge when justified.
11. Stop.

Do not create extra documentation or perform extra actions after the requested task is complete.

## 1 — Identify Intent

Classify the request before acting. Common intents include:

- capture an idea
- create or continue a project
- plan, build, test, troubleshoot, or document
- preserve knowledge or archive work
- research or retrieve information

Do not assume every request needs a project. For simple work with no durable retrieval value, answer or execute without creating notes.

## 2 — Identify the Project

For project-related work:

- Search the exact project name or known path first.
- Use [[Project Routing Standard]] when a new project or its location is uncertain.
- Use [[Project Naming Standard]] before creating a project.
- Search exact names, near matches, and likely synonyms before creation.
- Never create a second project because the wording differs slightly.

One project has one home.

## 3 — Route or Locate

For a new project:

- Identify the primary outcome and dominant platform when relevant.
- Choose exactly one approved category.
- Create one project folder only after Clarify and only within approved scope.

For an existing project:

- Use its current home.
- Do not create parallel folders for secondary components.
- Record secondary technologies under Project Hub Components.

## 4 — Read Minimum Context

Follow [[AI Context Standard]] using progressive disclosure:

- L0 — Context Card
- L1 — Project Hub
- L2 — specific deep documents

Use this narrow-to-broad retrieval order:

1. Exact known file or path.
2. Project Hub.
3. Directly relevant deep note or section.
4. Relevant system standard.
5. Likely project or category search.
6. Broader vault search only when necessary.

For established projects, read Project Hub first. Do not read the whole vault, every linked note, or `90 Archive/` unless historical context is required. Stop loading context when the task can be completed safely.

## 5 — Determine Lifecycle Stage

Use [[Project Lifecycle Standard]] and identify the current stage before making changes:

**Capture → Clarify → Plan → Build → Verify → Preserve → Archive**

Do not:

- build while critical clarification is missing
- treat planning as implementation
- treat implementation as verified
- archive before preservation review and required approval

Backward movement is allowed when evidence exposes a problem.

## 6 — Plan the Smallest Necessary Action

Before editing or building:

- Define the requested outcome.
- Identify only the files or systems that need changes.
- Identify required approvals and safety boundaries.
- Exclude unrelated cleanup and speculative redesign.
- Avoid documentation with no likely retrieval value.

Use no elaborate plan for a simple task. For large work, prefer one coherent plan and meaningful execution batches over excessive micro-gating.

## 7 — Execute the Approved Scope

- Preserve existing working behavior unless the requested change requires otherwise.
- Prefer simple, maintainable implementation.
- Update current notes instead of creating near-duplicates.
- Reuse system standards and link to them instead of copying their rules.
- Do not modify unrelated files or opportunistically clean up the vault.
- Build coherent sections and avoid documenting every click or command.

For testing, prefer consolidated scenarios. Group related fixes and rerun only affected scenarios when safe, unless broader regression testing is justified.

## 8 — Verify

Never claim completion based only on creation or editing. Verify in proportion to the task.

| Work Type | Minimum Verification |
| --- | --- |
| Files | Confirm expected files exist and no unintended files changed. |
| Code or workflows | Validate configuration, run approved tests, and compare expected with actual results. |
| Documentation | Check required sections, syntax, links, and consistency with active standards. |

If verification cannot be performed, state exactly what remains unverified and do not label the result fully complete.

## Audit Evidence Rules

- An approved audit report is immutable historical evidence. Do not silently rewrite it.
- Audit findings and recommendations do not authorize remediation. Audit and repair are separate scopes, and repair requires its own approved action.
- Correct an approved report through a later report or an explicit linked correction record that preserves the original.
- Audit evidence may establish facts about what was observed; it does not grant permissions or override `AGENTS.md`.

## 9 — Update Durable State

Update Project Hub only for:

- a lifecycle-stage change or verified milestone
- a major blocker
- a material architecture or decision change
- a material next-action change
- project closure

Do not update it for trivial edits, every execution, temporary debugging, or unchanged status.

Store current state, verified outcomes, important constraints, decisions, and the next action. Do not store full chat transcripts, private chain-of-thought, repeated summaries, temporary tool chatter, or low-value raw logs.

## 10 — Preserve Reusable Value

After meaningful verified work, ask whether anything has value beyond the project.

| Reusable Value | Destination |
| --- | --- |
| Operating rule, SOP, framework, or standard | `30 Systems` |
| Technical or business knowledge and lessons | `40 Knowledge` |
| Reference material | `50 Resources` |

Promote only information with likely retrieval value. Prefer updating an existing standard or knowledge note over creating a competing duplicate.

## 11 — Stop Condition

When the requested task is complete:

- Stop.
- Report the result concisely.
- State blockers or one next action when relevant.

Do not automatically continue into another lifecycle phase, Git operation, migration, refactor, or external action unless explicitly requested and authorized.

## Approval Boundaries

Require explicit approval or an explicit in-scope request before:

- credential creation, assignment, or modification
- handling secrets outside approved secure mechanisms
- external sends or notifications
- workflow activation, publication, or production deployment
- production-data use
- destructive actions or deletions
- irreversible schema changes
- broad migrations
- overwriting significant existing content
- Git commits or pushes

Planning, read-only inspection, local documentation drafting, and safe non-destructive validation may proceed when they are within the requested scope. Never interpret silence as approval.

## Source-of-Truth Rules

Apply `AGENTS.md` and its instruction precedence first. Then use these roles:

| Source | Role |
| --- | --- |
| Project Hub | Current project state |
| Deep docs | Approved detailed project knowledge |
| `30 Systems` | Reusable operating standards |
| `40 Knowledge` | Reusable knowledge and lessons |
| `50 Resources` | Reference material |
| `90 Archive` | Historical material, not current truth |

When sources conflict:

1. Identify the conflict.
2. Follow the higher-priority current source.
3. Do not silently merge contradictory states.
4. Ask only when the conflict materially changes the action.

## Token-Efficiency Rules

Agents must:

- use narrow retrieval and summaries before deep documents
- open exact sections when possible
- avoid rereading unchanged large notes
- avoid restating full project context in every response
- link to system standards instead of copying them
- summarize verified outcomes compactly
- stop context expansion once sufficient
- prefer one coherent operation over many tiny context-expensive steps when safe

Agents must not:

- read the entire vault or Archive “just in case”
- create duplicate summaries
- preserve raw AI conversations as project documentation
- generate excessive templates or notes
- write long documentation when a short operational update is sufficient

## File Creation Rules

Before creating a file:

1. Determine its single purpose.
2. Check whether an existing file already serves that purpose.
3. Use [[Template Standard]] when appropriate.
4. Create it only when it has durable retrieval value.

`Project Hub.md` is the only default required project note. Architecture, Implementation Plan, Test Plan, Decision, and Knowledge notes are optional and task-driven.

## Project Creation Flow

For a genuinely new project:

1. Capture the request.
2. Clarify the outcome.
3. Search for duplicates.
4. Apply [[Project Routing Standard]].
5. Apply [[Project Naming Standard]].
6. Create one project folder within approved scope.
7. Create `Project Hub.md` from `Templates/Project Hub Template.md`.
8. Populate only known information.
9. Set the next action.
10. Stop unless planning or building was also requested.

Do not generate a full documentation suite automatically.

## Experiment Promotion Rule

An experiment under `10 Projects/18 Experiments/` may be promoted only after verified findings justify a real initiative.

When promoting:

- Choose the correct category and approved project name.
- Preserve relevant verified findings.
- Avoid unnecessary duplication between the experiment and real project.
- Link or archive the original experiment as appropriate.
- Obtain approval before moving or archiving content when required by `AGENTS.md`.

## Agent Communication Style

- Routine work: be concise, direct, and result-focused; state one next action when useful.
- Blockers: explain exactly what is missing and ask only the minimum clarification required.
- Large work: summarize the plan when needed without overwhelming the user with micro-steps.
- Do not create artificial approval gates for low-risk, reversible, in-scope work.

## Do

- Use the active framework standards.
- Identify the correct project and retrieve minimum context.
- Keep one source of truth.
- Verify meaningful work.
- Preserve reusable value selectively.
- Favor simplicity, maintainability, retrieval quality, and token efficiency.

## Don't

- Scan the vault unnecessarily.
- Create duplicate projects or documentation by default.
- Over-engineer folder structures or micro-document actions.
- Treat unverified output as correct.
- Mix archived history with current truth.
- Perform external or destructive actions without approval.
- Continue beyond the requested scope.

## Related Standards

- [[Project Routing Standard]]
- [[Project Naming Standard]]
- [[Project Hub Standard]]
- [[AI Context Standard]]
- [[Project Lifecycle Standard]]
- [[Template Standard]]
