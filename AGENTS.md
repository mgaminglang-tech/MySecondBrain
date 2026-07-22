\# Merv's Second Brain — Codex Instructions



\## Purpose



This repository is a private Obsidian knowledge base for projects, SOPs, AI automation, technical learning, resources, and personal documentation.



Codex should treat this repository as a documentation and knowledge-management system, not as a normal software-code repository.



\## General Rules



1\. Preserve valid Obsidian Markdown, properties, internal links, embeds, and wikilinks.

2\. Do not delete, rename, or move existing notes unless explicitly requested.

3\. Do not modify anything inside `.obsidian/` unless explicitly requested.

4\. Never add passwords, API keys, access tokens, credentials, secrets, or sensitive personal information.

5\. Do not modify journal entries unless explicitly requested.

6\. Prefer improving an existing relevant note instead of creating a duplicate.

7\. Use clear note titles and descriptive filenames.

8\. Preserve existing YAML frontmatter when editing notes.

9\. Before making broad or structural changes, explain the proposed plan.

10\. Keep changes focused, minimal, and easy to review.

11\. Do not modify generated plugin files, caches, workspace files, or Git configuration.

12\. Do not commit, push, pull, merge, rebase, or change branches unless explicitly requested.

13\. Do not mark a task as completed unless the task was actually completed and the result can be verified.

14\. Do not invent project facts, decisions, credentials, test results, or completed work.

15\. When information is uncertain, clearly label it as an assumption or recommendation.



\## Repository Safety



Codex must not modify these paths unless explicitly requested:



\- `.git/`

\- `.obsidian/`

\- `.gitignore`

\- `Assets/`

\- `08 - Journal/`

\- `09 - Archive/`



Codex must never create or store:



\- API keys

\- Passwords

\- Authentication tokens

\- Private keys

\- Environment secrets

\- Personal account credentials

\- Client credentials

\- Unredacted sensitive data



Use placeholders when documentation requires credential examples:



```text

YOUR\_API\_KEY

YOUR\_ACCESS\_TOKEN

YOUR\_EMAIL\_ADDRESS

YOUR\_DATABASE\_URL

```



\## Folder Responsibilities



\### `00 - Inbox`



Contains temporary and unprocessed notes.



Codex may:



\- Organize inbox notes when explicitly requested.

\- Suggest appropriate destination folders.

\- Improve unclear note titles.

\- Add links to related notes.



Codex must not:



\- Automatically delete inbox notes.

\- Move notes without approval.

\- Treat inbox information as verified knowledge.



\### `01 - Dashboard`



Contains dashboards, navigation notes, and vault entry points.



Codex may:



\- Update navigation links.

\- Improve dashboard organization.

\- Create or improve Dataview queries.

\- Create or improve Tasks queries.

\- Fix broken dashboard links.



Codex must:



\- Preserve valid Dataview and Tasks syntax.

\- Avoid adding complex JavaScript queries unless explicitly requested.



\### `02 - Projects`



Contains active and planned project documentation.



Codex may:



\- Create project documentation.

\- Update objectives, requirements, scope, tasks, decisions, architecture, issues, progress, and lessons learned.

\- Add links to related SOPs, knowledge notes, resources, and AI prompts.

\- Create supporting project notes when necessary.



Codex must:



\- Mark tasks completed only when supported by actual project results.

\- Preserve the distinction between planned, active, blocked, completed, and archived projects.

\- Avoid claiming that a system was tested, deployed, or verified without evidence.



\### `03 - Areas`



Contains long-term responsibilities and ongoing areas of focus.



Examples include:



\- Career

\- Business

\- Learning

\- Finance

\- Health

\- Personal development



Codex may:



\- Add summaries and supporting notes when requested.

\- Link related projects and knowledge notes.

\- Organize recurring responsibilities.



Codex must not:



\- Turn temporary projects into permanent areas without approval.

\- Add private personal details unless explicitly provided for that purpose.



\### `04 - Knowledge`



Contains reusable technical knowledge, concepts, explanations, troubleshooting notes, and lessons learned.



Codex may:



\- Create concise technical notes.

\- Add practical examples.

\- Add troubleshooting steps.

\- Link related concepts.

\- Improve explanations.

\- Convert verified project lessons into reusable knowledge.



Codex must:



\- Separate confirmed facts from assumptions.

\- Prefer official documentation and primary sources when research is requested.

\- Avoid duplicating an existing knowledge note.



\### `05 - Resources`



Contains references, tools, books, courses, websites, documentation links, and useful materials.



Codex may:



\- Add or organize resources when requested.

\- Add short descriptions explaining why a resource is useful.

\- Group related resources by topic.



Codex must:



\- Avoid adding unverified or low-quality sources without explanation.

\- Avoid copying large copyrighted passages.

\- Clearly label outdated or archived resources.



\### `06 - SOPs`



Contains repeatable procedures and operational documentation.



Codex may:



\- Create or improve SOPs.

\- Add prerequisites.

\- Add numbered procedures.

\- Add validation steps.

\- Add rollback procedures.

\- Add troubleshooting sections.

\- Add expected results.

\- Link relevant project and knowledge notes.



Every SOP should include, when applicable:



\- Purpose

\- When to use

\- Requirements

\- Safety considerations

\- Procedure

\- Verification

\- Rollback

\- Troubleshooting

\- Related notes



Codex must not:



\- Claim that an SOP is tested unless evidence is available.

\- Remove safety checks to shorten a procedure.



\### `07 - AI`



Contains AI prompts, agent designs, Codex instructions, skills, automation patterns, test cases, and model-related documentation.



Codex may:



\- Create and improve prompts.

\- Document model purpose, inputs, outputs, constraints, tools, and test cases.

\- Add prompt versions and improvements.

\- Document agent workflows.

\- Create reusable AI automation patterns.



Codex must:



\- Preserve prompt code blocks.

\- Clearly distinguish draft prompts from tested prompts.

\- Avoid placing real credentials inside prompts.

\- Avoid claiming that a prompt is production-ready without testing.



\### `08 - Journal`



Contains personal daily notes and reflections.



Codex must not:



\- Modify journal entries unless explicitly requested.

\- Summarize or analyze journal entries unless explicitly requested.

\- Move journal content into other folders without approval.



\### `09 - Archive`



Contains completed, inactive, deprecated, or historical material.



Codex may:



\- Read archived notes when relevant.

\- Suggest archiving completed material.



Codex must not:



\- Permanently delete archived notes.

\- Restore archived items to active folders without approval.

\- Treat archived information as current without verification.



\### `Templates`



Contains reusable Obsidian templates.



Codex may:



\- Improve templates when explicitly requested.

\- Add useful fields and sections.

\- Standardize template structure.



Codex must:



\- Preserve Obsidian template syntax.

\- Preserve placeholders such as `{{date:YYYY-MM-DD}}`.

\- Avoid placing real project data inside reusable templates.



\### `Assets`



Contains images, screenshots, PDFs, and other attachments.



Codex must not:



\- Rename assets unless explicitly requested.

\- Move assets unless explicitly requested.

\- Delete assets.

\- Modify binary files.

\- Break existing image or attachment links.



\## Note Standards



Use YAML frontmatter where applicable.



General note structure:



```yaml

\---

type:

status:

created:

updated:

tags:

\---

```



Do not add empty properties unless they are useful for the note.



Use dates in this format:



```text

YYYY-MM-DD

```



Use lowercase values for properties such as:



```yaml

status: active

priority: high

type: project

```



Recommended project statuses:



```text

planned

active

blocked

on-hold

completed

archived

```



Recommended priorities:



```text

low

medium

high

critical

```



\## Project Note Standard



Use this structure for project notes:



```yaml

\---

type: project

status: active

priority: medium

created: YYYY-MM-DD

updated: YYYY-MM-DD

tags:

&#x20; - project

\---

```



Recommended project sections:



```markdown

\# Project Name



\## Objective



\## Problem



\## Scope



\### Included



\### Not Included



\## Requirements



\## Tasks



\## Architecture



\## Decisions



\## Issues



\## Next Action



\## Resources



\## Lessons Learned

```



\## Knowledge Note Standard



Use this structure for reusable knowledge notes:



```yaml

\---

type: knowledge

status: evergreen

created: YYYY-MM-DD

updated: YYYY-MM-DD

tags:

&#x20; - topic

\---

```



Recommended knowledge-note sections:



```markdown

\# Topic



\## Summary



\## Key Concepts



\## How It Works



\## Example



\## When to Use



\## Common Mistakes



\## Troubleshooting



\## Related Notes



\## Sources

```



\## SOP Note Standard



Use this structure for SOP notes:



```yaml

\---

type: sop

status: draft

created: YYYY-MM-DD

updated: YYYY-MM-DD

tags:

&#x20; - sop

\---

```



Recommended SOP sections:



```markdown

\# SOP Title



\## Purpose



\## When to Use



\## Requirements



\## Safety Considerations



\## Procedure



\## Verification



\## Rollback



\## Troubleshooting



\## Related Notes

```



\## AI Prompt Note Standard



Use this structure for AI prompt notes:



```yaml

\---

type: ai-prompt

status: testing

model:

created: YYYY-MM-DD

updated: YYYY-MM-DD

tags:

&#x20; - ai-prompt

\---

```



Recommended AI prompt sections:



```markdown

\# Prompt Name



\## Purpose



\## Context



\## Inputs



\## Prompt



\## Expected Output



\## Constraints



\## Test Cases



\## Results



\## Improvements



\## Final Version

```



\## Naming Standards



Use descriptive filenames.



Good examples:



```text

n8n Error Handling Patterns.md

Solar Monitoring Architecture.md

Deploying Next.js to Vercel.md

Customer Request Classification Prompt.md

```



Avoid filenames such as:



```text

Note.md

Untitled.md

Test 1.md

New Document.md

Final Final Version.md

```



Do not include characters that cause cross-platform filename problems:



```text

< > : " / \\ | ? \*

```



\## Obsidian Link Standards



Prefer Obsidian wikilinks for internal notes:



```markdown

\[\[Knowledge]]

\[\[Obsidian Second Brain Setup]]

\[\[06 - SOPs/SOPs|SOP Hub]]

```



Before creating a new wikilink:



1\. Check whether the target note already exists.

2\. Use the exact existing note title.

3\. Avoid creating multiple links that refer to the same concept under different names.



Preserve embeds:



```markdown

!\[\[image.png]]

!\[\[Document.pdf]]

```



\## Task Standards



Use standard Markdown tasks:



```markdown

\- \[ ] Open task

\- \[x] Completed task

```



For important tasks, include context where useful:



```markdown

\- \[ ] Connect the vault to Codex

\- \[ ] Review Codex changes before committing

\- \[ ] Test the dashboard after updating Dataview queries

```



Codex must not mark a task complete based only on an assumption.



\## Source and Research Standards



When research is requested:



1\. Prefer official documentation, primary sources, and trusted technical references.

2\. Record the source in the relevant note.

3\. Include the date accessed when the information can change.

4\. Clearly identify assumptions and inferences.

5\. Do not present outdated information as current.

6\. Avoid copying large sections from a source.

7\. Summarize information in original wording.



Recommended source format:



```markdown

\## Sources



\- Source title — accessed YYYY-MM-DD

```



\## Required Workflow



When handling a vault task:



1\. Read this `AGENTS.md` file first.

2\. Inspect the relevant existing folders and notes.

3\. Search for an existing note before creating a new one.

4\. Identify broken links, duplicates, conflicts, and relevant context.

5\. Explain the proposed files to create or update when the change is broad.

6\. Make only the requested changes.

7\. Preserve valid Markdown, YAML, wikilinks, Dataview queries, and Tasks queries.

8\. Update related links only when necessary.

9\. Review the final diff for accidental or unrelated changes.

10\. Summarize every created, updated, moved, or deleted file.

11\. Do not commit or push unless explicitly requested.



\## Broad Change Approval



Codex must request approval before:



\- Renaming multiple notes

\- Moving multiple notes

\- Reorganizing folders

\- Editing templates used across the vault

\- Modifying dashboard queries

\- Changing YAML property standards

\- Archiving multiple projects

\- Removing duplicate notes

\- Changing `.obsidian/`

\- Performing a repository-wide formatting update



\## Final Response Format



After making changes, report:



\### Files Created



\- List each created file.

\- State its purpose.



\### Files Updated



\- List each updated file.

\- Summarize the changes.



\### Files Moved or Renamed



\- List the original and new paths.

\- Explain why the move was necessary.



\### Important Decisions



\- List architecture, organization, naming, or documentation decisions.



\### Tasks Completed



\- List tasks that were actually completed.



\### Validation



\- Report whether Markdown, YAML, wikilinks, Dataview queries, and Tasks queries were checked.



\### Remaining Actions



\- List recommended next steps that were not completed.



\## Default Behavior



When the request is ambiguous:



1\. Do not make broad changes.

2\. Inspect the relevant notes.

3\. State the safest interpretation.

4\. Ask for approval when the decision could affect multiple files.



When no edits are requested, operate in read-only mode.

