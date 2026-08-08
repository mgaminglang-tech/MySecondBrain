# Merv's Second Brain — Codex Instructions

## Purpose

This repository is a private Obsidian knowledge base for projects, SOPs, AI automation, technical learning, resources, and personal documentation. Treat it as a documentation and knowledge-management system, not as a normal software-code repository.

## Instruction Precedence

Use this order when instructions overlap:

1. `AGENTS.md` — global safety, repository rules, and protected operations.
2. [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]] — standard lifecycle, gates, and project process.
3. The project-specific `Automation Project Checklist.md` — current phase, approvals, blockers, and next action.
4. The project `Requirements.md` and `Architecture.md` — approved behavior and technical source of truth.
5. The project `Test Plan.md` and `Test Results.md` — executable expectations and evidence.

When instructions conflict, the higher item takes precedence. Direct user instructions may narrow the current task but do not override safety or authorization boundaries. Missing project decisions must not be invented.

## Universal Vault Rules

- Preserve valid Obsidian Markdown, YAML frontmatter, properties, wikilinks, embeds, Dataview queries, Tasks queries, and template placeholders.
- Preserve existing valid content and prefer focused edits over rewrites.
- Search for an existing relevant note before creating a new one.
- Do not delete, rename, move, archive, or overwrite notes unless explicitly requested.
- Do not modify unrelated files.
- Keep project status, phase, owner, approvals, next action, and evidence accurate.
- Mark work complete only when supported by verified evidence.
- Do not invent facts, decisions, approvals, credentials, test results, execution IDs, deployment outcomes, client feedback, or business results.
- Label assumptions and recommendations clearly.
- Use descriptive filenames and avoid cross-platform-invalid characters.
- Use `YYYY-MM-DD` dates and lowercase property values where applicable.

## Merv’s AI OS v1

This section is the always-loaded global operating layer. Detailed procedures remain in `30 Systems/` and should be read only when relevant. The Instruction Precedence above and all stricter safety rules in this file remain controlling.

### Global Entry Rules

1. **Identify before acting.** Determine whether the request concerns an existing project, a new project, a system standard, reusable knowledge, a resource or reference, or a simple task that needs no vault storage. Do not create a project or note when the task has no durable retrieval value.
2. **Search before creating.** Search for an existing project or note, including near matches, before creating anything. Avoid duplicate projects and near-duplicate notes. One project has one home.
3. **Route and name new projects deliberately.** Consult [[30 Systems/Project Routing Standard]] and [[30 Systems/Project Naming Standard]]. Do not invent project categories without explicit approval.
4. **Enter established projects through `Project Hub.md`.** Treat it as the current project-state summary and read deeper documents only when required. Consult [[30 Systems/Project Hub Standard]].
5. **Use progressive context disclosure.** Retrieve L0 Context Card → L1 Project Hub → L2 task-relevant deep documents only. Do not read the whole vault “just in case.” Consult [[30 Systems/AI Context Standard]].
6. **Identify the lifecycle stage before major work.** Use Capture → Clarify → Plan → Build → Verify → Preserve → Archive. Consult [[30 Systems/Project Lifecycle Standard]].
7. **Create documentation only when justified.** `Project Hub.md` is the only default required project note. Architecture, Test Plan, Decision, Knowledge, and other deep notes are optional and must have operational or future retrieval value. Consult [[30 Systems/Template Standard]].
8. **Follow the operating flow.** For project work, use the smallest sufficient context and action scope, verify meaningful outcomes, update durable state only at meaningful milestones, and stop when the requested work is complete. Consult [[30 Systems/Agent Operating Standard]].

### Token Efficiency

Agents must:

- use narrow retrieval before broad search and summaries before deep documents
- open only task-relevant notes or sections and avoid rereading unchanged large notes
- avoid restating stable context and prefer links over duplicated framework text
- reuse system standards instead of copying them into projects
- stop expanding context once sufficient information is available
- prefer one coherent execution batch over excessive micro-steps when safe
- update durable notes only at meaningful milestones

Agents must not read the entire vault, load Archive or every linked note by default, preserve full chat transcripts, create repeated summaries, or create documentation for every small action.

### Source-of-Truth Roles

These roles are subject to the Instruction Precedence above:

- Project Hub = current project-state summary
- project deep docs = approved detailed implementation knowledge
- `30 Systems` = reusable standards, SOPs, and operating frameworks
- `40 Knowledge` = reusable knowledge, lessons, and patterns
- `50 Resources` = references and source material
- `90 Archive` = historical material, not current operational truth

When information conflicts, identify the conflict, follow the higher-priority current source, and never silently merge contradictory states. Ask only when the conflict materially changes the requested action.

### Approval Boundary

The stricter Security, Approval, Git, n8n, production, and destructive-action rules below remain controlling. Explicit approval is required before credential creation or modification, external sends or notifications, workflow activation or publication, production or customer data use, destructive actions, deletions, irreversible schema changes, broad vault migrations, significant overwrites, and Git commits or pushes unless already explicitly requested. Secrets must never be exposed and may be handled or moved only through approved secure mechanisms. Silence is not approval.

Safe read-only inspection, planning, requested local drafting, and non-destructive validation may proceed only when within scope and no stricter boundary applies.

### Project Quick Rules

For a genuinely new project:

1. Clarify the primary outcome.
2. Search for an existing match.
3. Apply the routing and naming standards.
4. Create exactly one approved project home.
5. Create `Project Hub.md` from [[Templates/Project Hub Template|Project Hub Template]].
6. Populate only known information and set the next action.
7. Do not generate the full documentation suite automatically.

For an existing project:

1. Locate `Project Hub.md` and read its Context Card or current state.
2. Identify the lifecycle stage.
3. Read only the deep documents needed for the request.
4. Perform the smallest complete action and verify when applicable.
5. Update Project Hub only when a meaningful state change occurred.

### Preservation and Stop Rules

After verified work, preserve only genuinely reusable value: operating rules, SOPs, and frameworks go to `30 Systems`; reusable lessons, concepts, and technical patterns go to `40 Knowledge`; references and source material go to `50 Resources`. Do not copy an entire project into reusable knowledge. Prefer updating an existing standard or knowledge note over creating a competing one.

Once the requested task is complete, stop, report concisely, and state blockers or one useful next action. Do not automatically continue into another lifecycle phase, migration, Git operation, activation, external send, or unrelated cleanup.

### Detailed Standards

- [[30 Systems/Project Routing Standard]]
- [[30 Systems/Project Naming Standard]]
- [[30 Systems/Project Hub Standard]]
- [[30 Systems/AI Context Standard]]
- [[30 Systems/Project Lifecycle Standard]]
- [[30 Systems/Template Standard]]
- [[30 Systems/Agent Operating Standard]]

Read only the standards relevant to the current task.

## Protected Paths and Operations

Do not modify these paths unless the user explicitly includes them in scope:

- `.git/`
- `.obsidian/`
- `.gitignore`
- `.gitattributes`
- `AGENTS.md`
- `Assets/`
- `Templates/`
- `90 Archive/`

Additional restrictions:

- Never modify generated plugin files, caches, or Obsidian workspace/UI-state files unless explicitly requested.
- Never modify binary assets, rename attachments, or break embeds unless explicitly requested.
- Never analyze, summarize, move, or edit journal content unless explicitly requested.
- Never permanently delete archived evidence.

## Security and Privacy

Never create, store, expose, or commit:

- passwords
- API keys
- access or authentication tokens
- private keys
- webhook secrets
- environment secrets
- personal or client credentials
- unredacted sensitive client or personal data

Use placeholders such as:

```text
YOUR_API_KEY
YOUR_ACCESS_TOKEN
YOUR_EMAIL_ADDRESS
YOUR_DATABASE_URL
```

Documentation may record a credential's name, purpose, environment, owner, minimum permission, and approved secure location—but never its value.

Use dummy or sanitized data unless real data use is explicitly authorized and documented. If a secret or sensitive value is discovered, do not reproduce it; report the location safely and request direction.

## Approval Requirements

Obtain explicit approval before:

- broad or repository-wide edits
- renaming or moving multiple notes
- reorganizing folders
- editing reusable templates
- changing dashboards or queries
- changing YAML property standards
- modifying protected paths
- archiving projects
- removing duplicates
- destructive or difficult-to-reverse operations
- assigning credentials
- enabling external writes, sends, or other side effects
- activating workflows
- changing production systems
- deploying to production

When the request is ambiguous, inspect first, state the safest interpretation, and stop for approval if the choice could affect multiple files, live systems, credentials, data, or people.

## Git Safety

- Do not stage, commit, push, pull, merge, rebase, restore, reset, change branches, or modify Git configuration unless explicitly requested.
- Inspect status and the relevant diff before reporting file changes.
- Preserve unrelated user changes.
- Never use destructive Git commands as a cleanup shortcut.
- Never commit secrets, credentials, unredacted client data, generated noise, or accidental broad changes.
- A request to edit files does not authorize a commit or push.

## n8n MCP and Workflow Safety

- Use n8n MCP only when explicitly requested.
- Treat capability audits as strictly read-only: do not create, edit, import, execute, activate, deactivate, delete, publish, or change settings or credentials.
- Before an approved workflow change, inspect the current workflow, project checklist, requirements, architecture, and test plan.
- Modify only the approved workflow and nodes; preserve unrelated workflows and credentials.
- Keep new or changed DEV workflows inactive until activation is explicitly approved.
- Use dummy or sanitized DEV fixtures and approved non-production destinations.
- Do not execute tests beyond the approved IDs or batch.
- Validate changed nodes and the full workflow, then confirm saved state, connections, credentials, external nodes, and active status.
- Never claim that a workflow was built, tested, deployed, or verified without evidence.

## Production, Credentials, and External Side Effects

- DEV, optional STAGING, and PROD are separate authorization boundaries.
- Approval for discovery, documentation, build, testing, or demo does not authorize production.
- Real-client projects require explicit approval before credential assignment, external side effects, workflow activation, or production deployment.
- Do not use PROD credentials, production data, live recipients, live databases, or production endpoints in DEV.
- Production changes require approved scope, current backup, rollback plan, required tests, operational ownership, monitoring, and explicit deployment and activation approvals.
- If any production, credential, recipient, destination, or side-effect target is unclear, stop without acting.

## Vault Task Workflow

1. Read this file.
2. Inspect the relevant notes and applicable higher-priority project sources.
3. Search for duplicates, conflicts, broken links, and unrelated working changes.
4. Explain the plan before broad changes.
5. Make only the requested changes.
6. Validate Markdown, YAML, wikilinks, queries, and task syntax as applicable.
7. Review the final diff for accidental changes.
8. Report every created, updated, moved, renamed, or deleted file.

When no edits are requested, operate in read-only mode.

## Final Reports

Keep final reports concise and evidence-based. Include:

- files created or updated
- important decisions or limitations
- validation actually performed
- unresolved blockers or next actions
- exact diff scope when requested

State clearly when runtime, external-system, or visual validation was not performed. Do not commit or push unless explicitly requested.
