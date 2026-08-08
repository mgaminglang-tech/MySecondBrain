---
type: system-standard
system: Merv's AI OS
status: active
version: 1.0
---

# Migration Standard

## Purpose

Define a safe, gradual, reversible, link-aware, and token-efficient process for moving legacy vault content into Merv’s AI OS v1.

## Core Principle

Migrate by value and relevance, not by age or folder location. Never use blind mass moves.

This standard does not authorize migration. Follow `AGENTS.md` approval boundaries before moving, renaming, merging, archiving, deleting, or broadly restructuring content.

## Migration Priority

Process legacy content in this order:

1. Active projects.
2. Frequently used systems and standards.
3. Reusable knowledge.
4. Important resources.
5. Completed projects.
6. Obsolete or unclear legacy content.

Do not migrate the whole vault at once.

## Legacy Content Classification

Classify each legacy item into one destination or action:

| Destination | Use When |
| --- | --- |
| `00 Inbox` | The item is captured but not yet clarified. |
| `10 Projects` | Active work has a clear outcome and finish line. Apply [[Project Routing Standard]] and [[Project Naming Standard]]; one project has one home. |
| `20 Areas` | The item represents an ongoing responsibility without a clear completion point. |
| `30 Systems` | It is a reusable SOP, framework, standard, process, operating rule, or cross-project checklist. |
| `40 Knowledge` | It is a reusable lesson, concept, technical pattern, learned constraint, or durable insight. |
| `50 Resources` | It is external reference material, a manual, research source, source document, or reference collection. |
| `90 Archive` | It is completed, cancelled, superseded, obsolete, or inactive historical material. |
| Leave In Place | Its value or classification is uncertain, links may be risky, or migration has no current operational value. |

Do not force-classify uncertain content.

## Migration Decision Flow

For each legacy project or note:

1. Identify what it is.
2. Check whether it is active or currently used.
3. Search for an equivalent in the new structure.
4. Select the most likely destination.
5. Inspect links, embeds, and dependencies.
6. Propose one action: migrate, merge, archive, or leave in place.
7. Preview the source → destination change and any rename.
8. Obtain approval when the change is significant, protected, broad, or difficult to reverse.
9. Execute only the approved scope.
10. Verify content and links, then update source-of-truth notes only when needed.

Classification and dry-run output are proposals, not execution authorization.

## Active Project Migration

For an active legacy project:

1. Identify its primary outcome.
2. Apply [[Project Routing Standard]] and [[Project Naming Standard]].
3. Search for a matching project under `10 Projects`.
4. If no match exists and creation is approved, create exactly one project home.
5. Create `Project Hub.md` only when one does not already exist.
6. Distill the current durable state into Project Hub.
7. Preserve and link only relevant deep documents.
8. Exclude low-value historical chatter and avoid recreating every legacy note.

Project Hub should capture Goal, Current State, Current Phase, Next Action, Hard Constraints, Key Decisions, Open Items, Verification, and Key Docs under [[Project Hub Standard]]. Do not copy the entire legacy folder by default.

## Merge Rule

When legacy and new notes both exist:

- Identify the current source of truth under `AGENTS.md` precedence.
- Preserve unique, durable, relevant information.
- Merge by meaning; never concatenate files blindly.
- Keep one current summary rather than duplicating it.
- Prefer the latest verified active state when no higher-priority source conflicts.
- Preserve important historical decisions when useful.
- Flag unresolved contradictions instead of guessing.

## Duplicate Handling

Before creating or moving anything:

- Search the exact title, near matches, aliases, and relevant synonyms.
- Inspect the likely project or category first.
- Reuse or merge with an existing current item when appropriate.
- Rename or archive only with required approval.
- Leave ambiguous duplicates untouched.

Never create duplicate project homes or names using `final`, `latest`, `new`, `copy`, or small wording variations.

## Link Safety

Before moving or renaming a note or folder:

- Identify inbound links.
- Identify outbound links and embeds.
- Identify references from Project Hubs and system standards.
- Record links that may require manual repair.

After an approved migration:

- Verify that links and embeds still resolve.
- Update references when required and approved.
- Do not assume Obsidian repaired every reference safely.

If link impact is unclear, leave the item in place and report the blocker.

## Dry-Run Policy

Before any meaningful migration, produce a dry run containing:

- items identified
- proposed source → destination mapping
- proposed renames
- merge candidates
- archive candidates
- leave-in-place candidates
- link and embed risks
- unresolved ambiguity or source conflicts

For broad, protected, or difficult-to-reverse changes, do not execute until the plan is explicitly accepted.

## Batch Size

Prefer one active project or one small coherent note group at a time.

For larger batches, list mappings, conflicts, and link risks first and obtain approval. Avoid full-vault migrations, whole-category moves without review, and hundreds of renames in one operation.

## Token-Efficiency Rules

Migration agents should:

- inspect the most likely paths first
- read current summaries before deep legacy content
- use this flow: likely legacy project → current summary → relevant deep docs → destination decision
- migrate one project or coherent batch at a time
- extract only durable current-state information
- avoid raw chats, debug logs, repeated summaries, and unchanged deep-doc rewrites
- stop loading context when the migration decision is safe to make

Never use this flow: entire vault → all historical notes → mass reorganization.

## Preservation Rule

During migration, selectively extract reusable value:

| Reusable Value | Destination |
| --- | --- |
| SOP, standard, framework, or operating rule | `30 Systems` |
| Lesson, pattern, concept, or learned constraint | `40 Knowledge` |
| Reference or source material | `50 Resources` |

Do not duplicate the whole project into reusable layers. Prefer updating an existing reusable note over creating a competing one.

## Archive Rule

Archive only when:

- the item is no longer active
- reusable knowledge has been preserved when needed
- its important final state is understood
- it is not required as a current source of truth
- archiving has been explicitly approved when required

Preserve coherent history. Do not delete an item merely because it is old.

## Leave-In-Place Rule

Leaving legacy content in place is valid when classification is uncertain, migration has little immediate value, link risk is high, content is rarely used, or the item may be revisited later.

The new framework does not require immediate migration of everything.

## Migration Completion

A project migration is complete only when:

- one clear project home exists
- Project Hub reflects the current verified state
- essential deep documents are linked
- no obvious active duplicate remains
- important links and embeds resolve
- reusable value has been preserved when justified
- old content is archived, intentionally retained, or clearly superseded
- verification is complete

Moving files alone does not complete a migration.

## Source of Truth After Migration

Apply `AGENTS.md` instruction precedence first:

- Project Hub = current project state
- deep docs = approved detailed project knowledge
- `30 Systems` = reusable operating standards
- `40 Knowledge` = reusable knowledge
- `50 Resources` = references
- `90 Archive` = historical material

Legacy notes left outside the new structure do not automatically override an approved active source of truth. Surface material conflicts rather than silently merging them.

## Agent Rules

- Search before moving and classify before migrating.
- Migrate active and high-value content first.
- Apply routing and naming standards.
- Prefer a careful merge over duplication.
- Preserve links and coherent history.
- Never mass-move blindly.
- Leave uncertain content in place.
- Verify every meaningful migration batch.
- Update Project Hub only with current durable state.
- Use narrow context retrieval and stop after the approved scope.

## Do

- Migrate gradually and preview significant changes.
- Preserve useful history and verify links.
- Extract reusable value selectively.
- Maintain one current source of truth.
- Leave uncertain content untouched.

## Don't

- Migrate the whole vault at once or move content for cosmetic cleanliness.
- Duplicate project homes or blindly concatenate notes.
- Delete old material without review.
- Rename heavily linked notes casually.
- Archive active source-of-truth material.
- Consume the entire vault for every migration task.

## Related Standards

- [[Project Routing Standard]]
- [[Project Naming Standard]]
- [[Project Hub Standard]]
- [[AI Context Standard]]
- [[Project Lifecycle Standard]]
- [[Template Standard]]
- [[Agent Operating Standard]]
