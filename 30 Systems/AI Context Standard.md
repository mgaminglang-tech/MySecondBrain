---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# AI Context Standard

## Purpose

Define how AI agents retrieve and consume vault context while minimizing tokens and avoiding unnecessary whole-vault reads.

## Core Principle

Use progressive disclosure: consume the smallest sufficient context needed to complete the task safely and accurately.

Move from L0 → L1 → L2 only when needed.

## L0 — Context Card

Use L0 for routing and simple tasks when project identity and state are sufficient.

Target: approximately 100–250 words.

Recommended fields:

- project name
- project type or category
- goal
- current state and phase
- next action
- hard constraints
- key references
- last verified state

Rules:

- Keep L0 highly compressed.
- Exclude long explanations, raw logs, and duplicated deep documentation.
- A concise Project Hub may include L0 as its top section.
- Do not force a separate Context Card file unless it adds real value.

## L1 — Project Hub

`Project Hub.md` is the default context for most project work.

Use L1 when:

- planning next work
- updating project state
- making implementation decisions
- reviewing progress
- determining which deep documents matter

Do not automatically open every linked document.

## L2 — Deep Docs

Examples include:

- Architecture and Data Model
- API mappings
- Implementation Plan and Test Plan
- SOP and Known Limitations
- Evidence, Research, and decision records

Rules:

- Read only documents relevant to the current task.
- Prefer a direct link, narrow search, or exact section.
- Do not load every deep document or unrelated project history by default.

## Context Retrieval Order

For project work:

1. Identify the project.
2. Read L0 when available.
3. Read `Project Hub.md`.
4. Identify the minimum missing information.
5. Read only the relevant L2 notes or sections.
6. Expand the search only when current context is insufficient.

Never default to reading the entire vault, all project folders, all archived notes, every linked note, or long historical conversations.

## Search Strategy

Use narrow-to-broad retrieval:

1. Exact project path.
2. Exact project name.
3. Likely project category.
4. Directly relevant system standard.
5. Broader vault search only when necessary.

For a known project, use [[Project Routing Standard]] to search its likely home first. For a known standard, open that specific note directly.

## Source-of-Truth Priority

Always apply `AGENTS.md` and its repository instruction precedence first. Within the remaining project context, prefer:

1. current Project Hub
2. current active system standard
3. latest verified decision or architecture note
4. implementation notes
5. historical notes
6. archived material

Do not silently merge contradictory states. Surface a conflict when it materially affects the task, and follow the higher-priority source.

## Evidence Applicability and Freshness

`AGENTS.md` remains authoritative for instructions, permissions, and approval boundaries. Runtime or execution evidence may establish facts about what occurred, but it never grants permission or overrides those boundaries.

Before relying on evidence, confirm that it applies to the same version, environment, scope, and relevant point in time. Use this small freshness vocabulary when a label is useful:

| State | Meaning |
| --- | --- |
| `current` | Verified and applicable to the present version, environment, and scope. |
| `stale` | Previously useful, but its date or operating context requires re-verification. |
| `superseded` | Explicitly replaced by a newer approved source and retained for traceability. |
| `unknown` | Applicability cannot be established from available evidence. |

Rules:

- Prefer a higher-priority source only when it is current and applicable.
- A later note does not automatically supersede earlier verified evidence. Supersession must be explicit through scope, approval, version, or a recorded decision.
- Templates describe expected structure; they do not prove execution, approval, completion, or runtime state.
- Historical or archived evidence must be re-verified before being treated as current.
- Missing evidence remains missing. Label assumptions and unresolved applicability instead of inferring a result.
- When applicable sources conflict, preserve the conflict and identify the evidence needed to resolve it; do not silently rewrite history.

## Context Compression Rules

Store:

- decisions and verified outcomes
- constraints and reusable patterns
- current state
- important evidence references

Avoid storing:

- full AI conversations
- repeated explanations
- every intermediate thought
- temporary debugging chatter
- duplicated status summaries
- raw logs unless needed as evidence

Store outcomes, not conversations. Store decisions, not debate transcripts. Store evidence references, not endless execution history.

## Context Escalation Examples

| Request | Minimum Context |
| --- | --- |
| “What is the next action?” | L0 or Project Hub only |
| Architecture change | Project Hub + relevant Architecture sections |
| Testing request | Project Hub + Test Plan + relevant Architecture sections |
| Credential or integration task | Project Hub + relevant integration note only |

Do not load unrelated documents.

## Cross-Project Rule

- Identify each relevant Project Hub first.
- Do not load full deep documentation for every project automatically.
- Escalate context only for projects materially involved in the task.

## System-Standard Reuse

Projects should link to shared standards under `30 Systems/` instead of copying their full rules.

Examples:

- [[Project Routing Standard]]
- [[Project Naming Standard]]
- [[Project Hub Standard]]
- [[AI Context Standard]]

Future standards should follow the same reuse principle.

## Agent Rules

- Read the smallest sufficient context and stop expanding once the task is safe to complete.
- Prefer summaries, direct links, and exact sections before whole files or broad searches.
- Avoid reopening unchanged documents and repeating stable context.
- Reuse shared standards instead of duplicating them in each project.
- Summarize newly verified outcomes into compact, durable notes.
- Preserve raw tool output only when it is useful evidence.

## Do / Don't

| Do | Don't |
| --- | --- |
| Move from L0 to L1 to L2 only as needed. | Read the whole vault “just in case.” |
| Search exact paths and likely categories first. | Scan unrelated projects by default. |
| Load only task-relevant deep sections. | Open every linked document automatically. |
| Link to shared standards. | Copy framework rules into every project. |
| Store verified outcomes and evidence references. | Preserve conversations or debugging chatter as durable context. |
| Surface material source conflicts. | Silently merge contradictory states. |
