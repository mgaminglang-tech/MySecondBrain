# Merv's Second Brain — Codex Instructions

## Purpose

This repository is a private Obsidian knowledge base for projects, SOPs, AI automation, technical learning, resources, and personal documentation. Treat it as a documentation and knowledge-management system, not as a normal software-code repository.

## Instruction Precedence

Use this order when instructions overlap:

1. `AGENTS.md` — global safety, repository rules, and protected operations.
2. [[06 - SOPs/Project Management/Standard Automation Project Workflow|Standard Automation Project Workflow]] — standard lifecycle, gates, and project process.
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

## Protected Paths and Operations

Do not modify these paths unless the user explicitly includes them in scope:

- `.git/`
- `.obsidian/`
- `.gitignore`
- `.gitattributes`
- `AGENTS.md`
- `Assets/`
- `Templates/`
- `08 - Journal/`
- `09 - Archive/`

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
