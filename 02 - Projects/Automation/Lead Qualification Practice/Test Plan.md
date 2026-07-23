---
type: project-note
status: draft
client: Demo Sales Company
created: 2026-07-23
updated: 2026-07-23
tags:
  - client-automation
  - testing
  - lead-qualification
---

# Test Plan

## Objective

Define repeatable tests before any workflow is built or executed.

## Test Environment

- DEV: Required; manual execution, dummy/sanitized data, and test-only destinations.
- STAGING: Optional; only if explicitly approved.
- PROD: Limited to an approved smoke test after all gates pass.
- Proposed workflow version: `v0.1.0`.
- Current execution status: not-run.

## Sanitized Fixtures

| Fixture | Purpose |
|---|---|
| `TEST-LEAD-001` | Complete, high-fit business lead |
| `TEST-LEAD-002` | Valid nurture-range lead |
| `TEST-LEAD-003` | Valid low-score lead |
| `TEST-LEAD-004` | Missing required fields |
| `TEST-LEAD-005` | Malformed email and unsupported enums |
| `TEST-LEAD-006` | Boundary values and extra whitespace |
| `TEST-LEAD-007` | Duplicate of a prior normalized email or approved key |
| `TEST-LEAD-008` | Unicode name and punctuation |

Use reserved/example domains and fictional names only.

## Test Cases

| ID | Scenario | Expected result | Priority |
|---|---|---|---|
| TC-001 | Complete high-fit lead | Valid; score 70–100; `qualified`; score breakdown present | high |
| TC-002 | Valid medium-fit lead | Valid; score 40–69; `nurture` | high |
| TC-003 | Valid low-fit lead | Valid; score 0–39; `unqualified` | high |
| TC-004 | Missing full name | `invalid`; `full_name` listed; never qualified | high |
| TC-005 | Missing consent | `invalid`; consent error; notification not sendable | high |
| TC-006 | Malformed email | `invalid`; format reason code | high |
| TC-007 | Uppercase email and padded strings | Values normalized without meaning changes | medium |
| TC-008 | Score exactly 70 | `qualified` if valid | high |
| TC-009 | Score exactly 69 | `nurture` if valid | high |
| TC-010 | Score exactly 40 | `nurture` if valid | high |
| TC-011 | Score exactly 39 | `unqualified` if valid | high |
| TC-012 | Missing optional scoring fields | Valid if required fields exist; missing criteria earn zero | medium |
| TC-013 | Unsupported product or enum | Controlled validation error | high |
| TC-014 | Duplicate input | Duplicate flagged; no repeated future side effect | high |
| TC-015 | Empty object | Controlled invalid result; no crash | high |
| TC-016 | Null values | Controlled normalization and validation | high |
| TC-017 | Long need summary | Length cap or validation behavior follows approved rule | medium |
| TC-018 | Unicode name/company | Preserved safely; no false validation failure | medium |
| TC-019 | Routing value has no match | `UNASSIGNED_REVIEW_REQUIRED` | high |
| TC-020 | Re-run same fixture | Same rule version yields same score and reasons | high |
| TC-021 | Storage payload schema | Required destination-neutral fields and idempotency key present | high |
| TC-022 | Notification payload for qualified lead | Correct safe summary and recipient role; no secret or excess personal data | high |
| TC-023 | Invalid lead notification behavior | No sendable sales notification; review/error payload only if approved | high |
| TC-024 | Future storage timeout | Bounded retry/alert behavior; no false success | high |
| TC-025 | Future notification fails after storage | Partial failure recorded; notification-only retry avoids duplicate storage | high |

## Edge Cases

- Free-email or uncommon email domains.
- Apostrophes, hyphens, accents, and non-Latin characters in names.
- Phone numbers with extensions or international prefixes.
- Conflicting score signals, such as high budget with no clear need.
- Required fields containing whitespace only.
- Consent supplied as ambiguous text rather than boolean.
- Values at every threshold boundary.
- Duplicate email with changed company or product.
- Missing routing table entry or inactive salesperson.
- Future rate limit, timeout, expired credential, or destination schema change.

## Output Verification

- Score stays between 0 and 100 and equals breakdown total.
- Rule and workflow versions are present.
- Invalid input cannot receive `qualified`, `nurture`, or `unqualified`.
- Storage payload excludes secrets and unnecessary raw data.
- Notification payload contains only minimum necessary lead context.
- Final output does not claim a storage write or notification send.

## Entry Criteria

- [ ] Requirements and scoring rules approved.
- [ ] Inactive DEV workflow is ready.
- [ ] Fixtures reviewed as dummy/sanitized.
- [ ] Expected values are calculated independently.
- [ ] Any test credentials and destinations are non-production.

## Exit Criteria

- [ ] All high-priority cases pass with evidence.
- [ ] Failures are fixed or accepted explicitly.
- [ ] Results are recorded in [[Test Results]].
- [ ] [[Known Limitations]] and [[Issues and Fixes]] are current.
- [ ] Reviewer decision is recorded.

## Related Notes

- [[Requirements]]
- [[Architecture]]
- [[Test Results]]
- [[Issues and Fixes]]

