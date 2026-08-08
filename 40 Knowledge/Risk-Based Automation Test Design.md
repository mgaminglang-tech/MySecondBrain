---
type: knowledge
status: active
---

# Risk-Based Automation Test Design

## Key Idea

A compact release suite can provide credible evidence when scenarios are chosen for explicit risks and omitted regression cases remain visible. Test count alone is not a measure of coverage.

## Verified Patterns

### Test boundaries explicitly

For an inclusive rule such as `value >= threshold`, test the meaningful value immediately below the threshold and the threshold itself. When relevant, also test a value above it. This distinguishes the comparison operator from assumptions about the surrounding band.

Boundary values should respect the domain’s real precision. For currency, dates, counts, and timestamps, “immediately below” may mean different things.

### Select scenarios by risk

A release suite can consolidate multiple concerns into a smaller number of scenarios when each case has a documented purpose. Useful risk dimensions can include:

- critical happy paths
- boundary and null behavior
- routing and identity rules
- duplicates or idempotency
- invalid or suspicious input
- output contracts and timestamps
- controlled notifications or side effects
- fallback and failure behavior

Consolidation is valuable only when it preserves observability. A scenario that fails should still make the affected behavior identifiable.

### Keep omitted coverage visible

Deferred or extended regression cases should remain listed as not executed rather than disappearing from the test record. This prevents a smaller release gate from being mistaken for complete regression coverage.

### Preserve evidence states

| State | Meaning |
| --- | --- |
| Passed | Observed behavior matched the stated expectation and has supporting evidence. |
| Failed | Observed behavior did not match the expectation. |
| Blocked | The test could not proceed because a prerequisite or safe boundary was missing. |
| Not executed | No execution evidence exists. |

**Not tested is not the same as passed.** Missing execution evidence should remain missing rather than being inferred from nearby successes.

### Retest proportionally

After related defects are grouped and fixed, rerunning the affected scenarios can be sufficient when the change has a narrow impact. Broader regression remains appropriate when shared logic, contracts, integrations, or risk boundaries changed.

## Evidence Scope and Limitations

These patterns were verified in a controlled inactive DEV release suite using dummy data, explicit boundary cases, and recorded pass evidence. A larger regression suite, integrations, recovery behavior, and production operation were not verified by that evidence. The knowledge describes test-design reasoning, not a mandatory universal fixture set.

## Related

- [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[30 Systems/Standard Automation Project Workflow|Standard Automation Project Workflow]]
