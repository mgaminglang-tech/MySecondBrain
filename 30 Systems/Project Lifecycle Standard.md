---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Project Lifecycle Standard

## Purpose

Define a lightweight, consistent lifecycle for automation, CRM, GoHighLevel, funnel, website, AI-agent, internal-system, experiment, and future project types in Merv’s AI OS.

## Lifecycle

**Capture → Clarify → Plan → Build → Verify → Preserve → Archive**

The lifecycle is directional, not a strict waterfall. Move backward when new evidence, requirements, or failures make an earlier stage necessary.

This standard remains subject to `AGENTS.md` and its instruction precedence. When applicable, the [[Standard Automation Project Workflow]] remains the higher-priority lifecycle for automation projects.

## Stage Summary

| Stage | Primary Outcome | Exit Condition |
| --- | --- | --- |
| Capture | Record the raw intent without over-structuring it. | The intent can be clarified, tested, or rejected. |
| Clarify | Define what is being built and why. | Planning can begin without major ambiguity. |
| Plan | Design the smallest complete build approach. | Building can begin without redesigning from scratch. |
| Build | Implement the approved plan safely. | The planned build is complete enough to verify. |
| Verify | Confirm critical behavior and success criteria. | Criteria pass or remaining limitations are explicitly accepted. |
| Preserve | Extract durable reusable value. | Relevant reusable knowledge has been promoted or linked. |
| Archive | Remove inactive work from the active surface without deleting history. | The coherent project is safely stored and retrievable. |

## 1 — Capture

### Purpose

Capture a raw idea, request, opportunity, problem, or project concept without creating premature structure.

Examples:

- “Build a CRM for a dental clinic.”
- “Automate lead routing from Facebook to GoHighLevel.”
- “Create an AI support agent.”
- “Test whether this API integration works.”

### Required Behavior

- Record the intent and requested outcome or problem.
- Use `00 Inbox` or `18 Experiments` for obvious temporary ideas when appropriate.
- Move directly to Clarify when the request is clearly a real project.
- Do not design detailed architecture or create unnecessary deep documents.

### Minimum Information

- working project name or raw title
- requested outcome
- source or requester when relevant

### Exit Condition

The intent is clear enough to decide whether it needs clarification, experimentation, or rejection. A rejection decision does not authorize deletion.

### Project Hub Update

No Project Hub is required until the item becomes a real project.

### Token Rule

Do not generate long discovery documentation during Capture.

## 2 — Clarify

### Purpose

Determine exactly what is being built and why.

### Required Behavior

- Identify the primary outcome.
- Use [[Project Routing Standard]] to choose one category.
- Use [[Project Naming Standard]] to approve a stable name.
- Search for an existing matching project before creating anything.
- Define scope, important exclusions, constraints, success criteria, unknowns, and blockers.

### Minimum Information

- approved project name and category
- goal
- scope and important exclusions
- key constraints
- initial success criteria

### Exit Condition

The project is sufficiently defined to plan without major ambiguity.

### Clarification Rule

Stop and ask when:

- the project home would materially change
- scope is contradictory
- the required business outcome is unclear
- continuing would invent a high-impact assumption
- approval, credentials, recipients, production data, external side effects, or destructive actions are unclear

Do not stop for trivial formatting or implementation details that can safely be decided later.

### Project Hub Update

Create `Project Hub.md` when the initiative becomes a real project. Update Goal, Scope, Status, Hard Constraints, and Next Action according to [[Project Hub Standard]].

## 3 — Plan

### Purpose

Design the smallest complete plan needed to build correctly.

### Required Behavior

- Define the architecture or solution approach.
- Identify integrations, dependencies, data flow, approvals, credentials, tests, safety boundaries, and known limitations where relevant.
- Decide whether deep notes add operational value.
- Create only justified deep notes, such as `Architecture.md`, `Implementation Plan.md`, `Test Plan.md`, or `Data Model.md`.

### Minimum Information

- approved solution approach
- key dependencies and data flow
- required decisions and approvals
- testing strategy
- safety boundaries and known limitations

### Exit Condition

The build can begin without redesigning the project from scratch.

### Project Hub Update

Update Current Phase, Architecture Summary, Key Decisions, Hard Constraints, Open Items, and Next Action.

### Token Rule

Plan enough to remove implementation ambiguity, then stop. Prefer one concise architecture note over fragmented planning notes.

## 4 — Build

### Purpose

Implement the approved plan.

### Required Behavior

- Follow the current Project Hub and approved deep documents.
- Reuse shared standards under `30 Systems/` rather than copying them.
- Build in meaningful batches and group related changes where practical.
- Preserve approved IDs, mappings, decisions, and constraints.
- Keep implementation maintainable and readable.
- For automation and system builds, prefer a complete inactive or otherwise safe build before fragmented testing when appropriate.

### Minimum Information

- approved plan and current constraints
- resolved prerequisites for the current build batch
- expected build outcome
- safe validation approach

### Authorization Boundary

Building does not authorize activation, publication, deployment, external sends, production data, credential assignment, or destructive actions. Obtain explicit approval when required by `AGENTS.md`.

### Exit Condition

The planned build is complete enough for verification.

### Project Hub Update

Update only when the build is substantially complete, architecture materially changes, a major blocker appears, or an important decision changes.

### Token Rule

Do not preserve raw implementation chatter or document every node, click, command, or minor edit.

## 5 — Verify

### Purpose

Confirm that the system works as intended.

### Required Behavior

- Validate configuration first where relevant.
- Run the smallest complete test set covering critical behavior.
- Prefer consolidated scenarios over excessive micro-tests.
- Test happy paths, duplicate or idempotency behavior, and failure or fallback behavior when relevant.
- Group related fixes before rerunning tests where practical.
- Rerun only failed scenarios unless broader regression testing is justified.
- Record verified outcomes and evidence references.

### Minimum Information

- what was tested
- expected result
- actual result
- pass or fail
- important evidence reference
- unresolved limitation

### Exit Condition

Success criteria are met, or remaining limitations are explicitly accepted by the authorized decision-maker.

### Project Hub Update

Update State, Last Verified, Verification, Open Items, known limitations, and Next Action.

### Token Rule

Summarize multiple executions into one compact verification result. Store evidence references, not endless raw logs.

## 6 — Preserve

### Purpose

Convert verified project outcomes into durable reusable knowledge.

### Preserve Only

- reusable patterns, prompts, and architecture
- important decisions and lessons learned
- SOPs, standards, and templates
- known failure patterns
- important operational knowledge

### Possible Destinations

- `30 Systems` for reusable operating standards and systems
- `40 Knowledge` for reusable knowledge and lessons
- `50 Resources` for reference material

### Required Behavior

- Extract only reusable value; do not copy the whole project.
- Link back to the source project when useful.
- Avoid duplicate standards and update an existing standard when appropriate and approved.
- Keep client-specific implementation details in the project.

Examples:

| Project Outcome | Preservation Decision |
| --- | --- |
| Proven n8n idempotency design | Preserve as a reusable automation pattern. |
| Client-specific GoHighLevel pipeline | Keep in the project. |
| Reusable GoHighLevel onboarding checklist | Preserve under `30 Systems`. |
| Lesson about a specific API limitation | Preserve under `40 Knowledge`. |

### Minimum Information

- verified outcome being reviewed
- reusable value identified
- chosen destination or reason not to preserve
- source-project reference when useful

### Exit Condition

Reusable value has been extracted, linked, or deliberately declined; no unique lesson remains unreviewed.

### Project Hub Update

Add links to preserved outputs when useful.

## 7 — Archive

### Purpose

Remove inactive work from the active operating surface without deleting useful history.

### Archive When

- the project is completed, cancelled, superseded, or inactive
- an experiment is concluded
- no immediate active work remains

### Before Archiving

- Ensure the Project Hub reflects the final verified state.
- Complete the preservation review.
- Record important known limitations.
- Ensure active references do not incorrectly present obsolete state as current.

### Minimum Information

- final state and archive reason
- last verified state
- preserved outputs or knowledge links
- known limitations and unresolved items

### Archive Rules

- Use `90 Archive/` as the destination.
- Preserve the project as a coherent unit when possible.
- Do not delete completed work to reduce clutter.
- Do not create `final-final-v2` duplicates.
- Do not treat archived material as current operational truth.
- Moving content into the protected archive requires explicit approval under `AGENTS.md`; entering the Archive stage does not provide that approval.

### Exit Condition

The project is safely removed from active work while remaining coherent and retrievable.

## Project States

Use this small, stable vocabulary:

- `idea`
- `clarifying`
- `planned`
- `building`
- `verifying`
- `active`
- `blocked`
- `completed`
- `cancelled`
- `archived`

Lifecycle stage and state are related but not identical. For example, a project may be in Build with state `blocked`. Do not create micro-status values when an existing state plus a concise explanation is sufficient.

## Promotion and Demotion Rules

- Verification exposes an architecture flaw → return to Plan or Build.
- An experiment proves valuable → return to Clarify, then route it to the appropriate category with approval before moving files.
- An active project becomes obsolete → Preserve, then Archive.
- A new requirement materially changes scope → return to Clarify.
- A failed or incomplete test → remain in Verify or return to Build as appropriate.

Do not force one-way progression, and do not treat a stage change as authorization for a protected operation.

## Project Hub Update Policy

The Project Hub is the current-state summary. Update it when:

- the lifecycle stage changes
- a meaningful milestone is verified
- a major blocker appears or resolves
- architecture materially changes
- a key decision changes
- the next action materially changes
- the project closes

Do not update it for minor edits, every command, every test execution, temporary debugging, or repeated unchanged status.

## AI Context by Stage

| Stage | Minimum Context |
| --- | --- |
| Capture | Minimal request context only. |
| Clarify | [[Project Routing Standard]] and [[Project Naming Standard]]. |
| Plan | Project Hub plus relevant standards and deep docs only. |
| Build | Project Hub plus implementation-specific docs only. |
| Verify | Project Hub, Test Plan, and relevant Architecture sections. |
| Preserve | Verified outcomes plus relevant system or knowledge standards. |
| Archive | Final Project Hub plus preservation outputs. |

Always follow [[AI Context Standard]] and move from L0 → L1 → L2 only as needed.

## Source-of-Truth Rule

Apply `AGENTS.md` and its instruction precedence first.

- Project Hub: current project state
- deep documents: detailed approved implementation knowledge
- `30 Systems`: reusable operating standards
- `40 Knowledge`: reusable knowledge and lessons
- `50 Resources`: reference material
- `90 Archive`: historical context, not current operational truth

Do not duplicate current-state summaries across notes or silently merge conflicting sources.

## Documentation Principle

Document decisions, verified outcomes, constraints, reusable knowledge, and necessary evidence references.

Avoid full chat transcripts, post-decision brainstorming, temporary debugging chatter, repeated summaries, redundant checklists, and raw logs without evidentiary value.

## Agent Rules

- Identify the current lifecycle stage before acting.
- Do not skip Clarify when major ambiguity exists.
- Do not over-plan or build before required decisions are resolved.
- Do not treat unverified output as complete.
- Do not archive before preservation review and explicit authorization.
- Update the Project Hub only at meaningful milestones.
- Use progressive context disclosure and reuse system standards.
- Never silently invent approval for external, destructive, credential, production-data, activation, publication, or deployment actions.

## Do / Don't

| Do | Don't |
| --- | --- |
| Keep the lifecycle lightweight. | Turn every stage into bureaucracy. |
| Move backward when verification exposes problems. | Force a one-way waterfall. |
| Preserve reusable value. | Create documents with no operational value. |
| Keep the Project Hub current at meaningful milestones. | Micro-document every step. |
| Verify before declaring success. | Confuse planning or building with completion. |
| Treat archived material as history. | Treat archived notes as current truth. |
