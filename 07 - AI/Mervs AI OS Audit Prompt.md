---
type: ai-prompt
status: ready
owner: Mervin
created: 2026-07-24
updated: 2026-07-24
tags:
  - ai-os
  - audit
  - codex
---

# Mervs AI OS Audit Prompt

## Purpose

Use this prompt for a strict read-only health audit of Mervs AI OS. Store approved reports according to [[07 - AI/Audits/Audits|Audits]] and evaluate evidence using [[07 - AI/Source Authority and Freshness Rules|Source Authority and Freshness Rules]].

## Copy-ready Prompt

```text
Read and follow AGENTS.md.

Perform a strict read-only audit of Mervs AI OS.

Audit date: [YYYY-MM-DD]
Scope: [VAULT, FOLDER, PROJECT, OR SYSTEM SCOPE]

Use [[Mervs AI OS Overview]] and [[Source Authority and Freshness Rules]] as governance references.

Check:

1. routing integrity
2. index and folder truth
3. broken or ambiguous wikilinks
4. stale project status and next actions
5. conflicting or duplicated information
6. context poisoning, bloat, confusion, and clash
7. task hygiene
8. source authority and freshness
9. archive eligibility
10. Git and .obsidian noise
11. secrets or prohibited sensitive information
12. documentation and Markdown structure

Workflow:

Inventory
→ focused folder checks
→ cross-check authoritative sources
→ produce findings
→ recommend fixes
→ wait for approval

For every finding, include:

- severity: Critical, High, Medium, or Low
- confirmed problem or optional improvement
- exact evidence and file path
- why it matters
- proposed fix
- files that would be modified

Return:

- audit date
- scope
- health score out of 10
- Critical, High, Medium, and Low findings
- evidence for every finding
- proposed fixes
- files that would be modified
- GO, CONDITIONAL GO, or NO-GO
- explicit confirmation that no files were changed

Do not edit, create, delete, move, rename, archive, restore, stage, commit, or push anything.
Do not perform MCP writes.
Do not create, modify, execute, activate, deactivate, import, publish, or delete workflows.
Do not modify credentials, connected systems, Git settings, or .obsidian state.
Do not expose discovered secrets or sensitive values.

Wait for approval before any editing or remediation phase.
```

## Related Notes

- [[07 - AI/Mervs AI OS Overview|Mervs AI OS Overview]]
- [[07 - AI/Source Authority and Freshness Rules|Source Authority and Freshness Rules]]
- [[07 - AI/Audits/Audits|Audits]]

