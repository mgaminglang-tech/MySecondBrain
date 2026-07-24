---
type: index
status: active
owner: Mervin
created: 2026-07-24
updated: 2026-07-24
tags:
  - ai-os
  - audits
---

# Audits

## Purpose

Store approved Mervs AI OS audit reports in:

`07 - AI/Audits/`

Use this filename standard:

`AI OS Audit - YYYY-MM-DD.md`

## Evidence Rules

- An approved audit report is immutable historical evidence.
- Later audits may link to earlier reports and record what changed.
- An audit report identifies findings and recommendations; it does not authorize fixes.
- Remediation requires a separate, explicitly approved editing phase.
- If a correction to an approved report is necessary, preserve the original and document the correction in a later report.
- Audit reports must not contain secrets, credential values, or unnecessary sensitive data.

## Audit Workflow

1. Run [[07 - AI/Mervs AI OS Audit Prompt|Mervs AI OS Audit Prompt]] in read-only mode.
2. Review the report and evidence.
3. Obtain approval before storing the report or starting fixes.
4. Store the approved report using the filename standard.
5. Handle fixes as a separate scoped task.

## Related Notes

- [[07 - AI/Mervs AI OS Overview|Mervs AI OS Overview]]
- [[07 - AI/Mervs AI OS Audit Prompt|Mervs AI OS Audit Prompt]]
- [[07 - AI/Source Authority and Freshness Rules|Source Authority and Freshness Rules]]

