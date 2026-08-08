---
type: resource
status: active
category: prompts
---

# Merv’s AI OS Audit Prompt

## Purpose

Provide a reusable, strict read-only audit prompt for a vault, framework area, project, or system scope.

## Copy-Ready Prompt

```text
Read and follow AGENTS.md.

Perform a strict read-only audit of Merv’s AI OS.

Audit date: [YYYY-MM-DD]
Scope: [VAULT, FOLDER, PROJECT, OR SYSTEM SCOPE]
Audit objective: [QUESTION OR CONTROL BEING AUDITED]

Use [[AI Context Standard]] for narrow-to-broad retrieval, [[Agent Operating Standard]] for evidence and audit boundaries, and [[Migration Standard]] only when migration or legacy classification is in scope. Do not read unrelated standards or the entire vault unless the stated audit scope genuinely requires it.

For project-specific audits, begin with Project Hub.md and open only relevant deep documents. For each source, check that its evidence applies to the same version, environment, scope, and relevant point in time.

Inspect only controls relevant to the stated scope, such as:

- routing, naming, and project-home integrity
- Project Hub and current-state accuracy
- conflicting, duplicated, stale, superseded, or unsupported information
- broken or ambiguous wikilinks and embeds
- evidence, verification, approval, and readiness claims
- documentation structure, bloat, and unnecessary context
- migration or archive eligibility when explicitly in scope
- Git working-state awareness and unrelated changes
- .obsidian or generated-state noise without modifying it
- secrets or prohibited sensitive-data exposure without reproducing values
- workflow, credential, production, or external-side-effect boundaries

Use this flow:

scope confirmation
→ narrow inventory
→ focused source checks
→ evidence and conflict cross-check
→ findings
→ recommendations
→ stop

For every finding, report:

- severity: Critical, High, Medium, or Low
- classification: confirmed problem, unresolved risk, or optional improvement
- exact file or system location
- concise supporting evidence
- evidence freshness or applicability concern when relevant
- why it matters
- recommended remediation
- files or systems that remediation would affect

Return:

1. audit date and exact scope
2. concise overall result
3. findings ordered by severity
4. evidence and source references for every finding
5. conflicts, unknowns, and unavailable evidence
6. recommended remediation order
7. exact files or systems a later repair phase would modify
8. GO, CONDITIONAL GO, or NO-GO when the audit objective supports a gate
9. explicit confirmation that no changes were made

Audit findings do not authorize remediation. An audit may establish facts and risks, but repairs require a separate explicitly approved scope.

Do not edit, create, delete, move, rename, archive, restore, stage, commit, push, or change branches.
Do not modify AGENTS.md, Dashboard.md, templates, .obsidian, Git settings, credentials, connected systems, or production state.
Do not create, modify, execute, activate, deactivate, import, publish, or delete workflows.
Do not perform MCP writes, external sends, schema changes, or destructive actions.
Do not expose discovered secrets, credential values, or unnecessary sensitive data; report only the affected location safely.
Do not silently resolve evidence conflicts or rewrite historical audit evidence.

Stop after the audit report and wait for a separately approved remediation task.
```

## Related Standards

- [[AI Context Standard]]
- [[Agent Operating Standard]]
- [[Migration Standard]]
