---
type: ai-governance
status: active
owner: Mervin
created: 2026-07-24
updated: 2026-07-24
tags:
  - ai-os
  - source-authority
  - freshness
---

# Source Authority and Freshness Rules

## Purpose

Define which evidence controls when sources conflict and how freshness should be represented. Source authority establishes truth; it does not grant permission to edit files or runtime systems.

## Authority Hierarchy

Use the highest available, applicable, and verified source:

1. Current verified runtime evidence
2. Approved Test Results or equivalent evidence
3. Current Project Overview metadata
4. Current project checklist and decision records
5. Supporting project notes
6. Current policies and SOPs
7. Templates and general references
8. Archived, superseded, or historical notes

Runtime evidence may confirm state, configuration, or behavior. It does not authorize runtime modification, workflow execution, credential use, side effects, activation, or production deployment.

## Freshness States

| State | Meaning |
|---|---|
| `current` | Verified and applicable to the present version, phase, owner, and environment. |
| `review-needed` | Potentially useful but requires confirmation because its date, version, ownership, or context may have changed. |
| `on-demand` | Intentionally verified only when a decision or action requires it. |
| `superseded` | Replaced by a newer approved source and retained only for traceability. |
| `archived` | Historical evidence outside current operating context. |

## Conflict Resolution

1. Confirm that the sources describe the same version, environment, scope, and point in time.
2. Prefer the higher authority source only when it is current and applicable.
3. Preserve the lower source as historical evidence; do not silently rewrite history.
4. Record the conflict, affected decisions, and evidence required to resolve it.
5. Escalate unresolved conflicts to Mervin before editing or acting.

## Evidence Rules

- Missing evidence remains missing. Do not infer approval, completion, execution, or production readiness.
- Do not mark historical gates complete retroactively unless contemporaneous evidence supports the claim.
- Treat historical instructions as context, not current actions, unless a current owner and trigger reactivate them.
- Prefer explicit dates, versions, environments, owners, approvers, decisions, and evidence links.
- Label assumptions, unavailable evidence, and inferences directly.
- A later note does not automatically supersede an earlier one; supersession must be clear from scope, approval, version, or decision evidence.
- Templates describe expected structure, not actual project status.
- Archived evidence must not be treated as current without re-verification.

## Escalation to Mervin

Stop and request direction when:

- authoritative sources remain inconsistent
- the applicable version or environment is unclear
- approval or ownership is missing
- runtime evidence conflicts with approved documentation
- resolving the conflict would change scope, credentials, external systems, production state, or historical evidence

## Related Notes

- [[07 - AI/Mervs AI OS Overview|Mervs AI OS Overview]]
- [[07 - AI/Mervs AI OS Audit Prompt|Mervs AI OS Audit Prompt]]
- [[07 - AI/Audits/Audits|Audits]]

