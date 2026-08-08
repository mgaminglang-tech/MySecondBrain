---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Template Standard

## Purpose

Define how templates support consistent, concise notes in Merv’s AI OS without creating unnecessary documentation or token overhead.

## Core Principles

- Keep templates minimal and focused on current-state clarity.
- Include only fields that are likely to be used.
- Do not duplicate information already stored elsewhere.
- Link to shared system standards instead of copying their rules.
- Treat templates as starting points, not bureaucracy.
- Remove irrelevant optional sections instead of leaving empty placeholders.
- Give each note one clear purpose.

## Template Selection

### Project Hub Template

Use when:

- a real project is created after Clarify
- the project needs one current source-of-truth entry point

Every real active project requires one `Project Hub.md` under [[Project Hub Standard]].

### Decision Note Template

Use when a decision materially affects architecture, scope, safety, cost, workflow, or future implementation and its reasoning may matter later.

Do not create Decision Notes for trivial choices.

### System Standard Template

Use when defining a reusable rule, framework, SOP, convention, or operating standard that applies across projects.

### Knowledge Note Template

Use when preserving a reusable concept, lesson, technical pattern, or learned constraint that is useful beyond one project.

## When Not to Create a Note

Do not create a new note when:

- the information belongs naturally in an existing current note
- it is temporary debugging chatter or raw AI conversation
- it duplicates an active standard or existing note
- it has no likely retrieval value

## AI and Token-Efficiency Rules

- Do not automatically create every template for every project.
- Project Hub is the only default required project note.
- Create deep notes only when the task justifies them.
- Use templates that encourage concise writing.
- Prefer updating an existing note over creating a similar note.
- Prefer links over duplication.
- Preserve verified outcomes, decisions, constraints, and reusable knowledge.
- Discard temporary reasoning and debugging chatter.
- Retrieve Project Hub first, then only the specific deep notes needed under [[AI Context Standard]].

## Naming Rules

Use stable note names:

| Note Type | Naming Pattern |
| --- | --- |
| Project Hub | `Project Hub.md` |
| Decision | `Decision - <Short Name>.md` |
| System standard | `<Standard Name>.md` |
| Knowledge | `<Clear Topic Name>.md` |

Do not use `Final`, `Final Final`, `Latest`, `New`, `Copy`, or ordinary `v2`/`v3` suffixes unless a separate maintained version is genuinely required.

## Template Maintenance

- Keep reusable source templates unchanged when instantiating them.
- Remove unused optional sections from the instantiated note.
- Update the existing template when its reusable structure evolves.
- Do not create a competing template with a small naming variation.
- Follow [[Project Naming Standard]] and applicable active system standards.

## Agent Rules

- Select only the template justified by the note’s purpose.
- Search for an existing current note before creating a new one.
- Do not instantiate templates across projects automatically.
- Preserve template placeholders until the template is intentionally used.
- Keep generated notes concise and remove irrelevant optional sections.

## Do / Don't

| Do | Don't |
| --- | --- |
| Use the smallest suitable template. | Create every possible note for every project. |
| Update an existing current note when appropriate. | Create duplicate sources of truth. |
| Link to shared standards. | Copy full framework rules into project notes. |
| Preserve durable outcomes and decisions. | Preserve temporary reasoning or raw chat. |
| Remove unused optional sections. | Leave empty boilerplate throughout a note. |
