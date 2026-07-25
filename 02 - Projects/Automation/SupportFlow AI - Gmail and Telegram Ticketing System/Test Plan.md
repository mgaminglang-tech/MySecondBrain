---
type: project-note
status: in-progress
phase: phase-1-validated
testing_status: passed-for-phase-1
client: internal-demo
owner: Mervin
created: 2026-07-25
updated: 2026-07-25
tags:
  - client-automation
  - testing
---

# Test Plan

## Status

- Testing status: **passed for Phase 1 seed suite; integration not-run**
- Environment: DEV
- Workflow: `DEV - SupportFlow AI - Gmail and Telegram Ticketing System`
- Workflow state: built and inactive
- Workflow ID/version: `cyiCqsjLQdB7apjP` / `ea24015d-27fe-41cc-90e8-1e68222282d6`
- Credentials and destinations: not approved
- Data: dummy or sanitized only
- Planned fixture count: 30

This note contains verified Phase 1 manual-test evidence only. It does not claim integration, performance, demo, or production readiness.

## Entry Criteria

- [x] Discovery and scope approved for Phase 1.
- [x] Requirements and architecture approved for Phase 1.
- [x] Exact Phase 1 schemas, enums, mocked duplicate rules, and escalation examples approved.
- [x] Inactive DEV build separately authorized and validated.
- [x] Six sanitized seed fixture IDs and scenarios approved.
- [x] Mocked duplicate and AI behavior approved.
- [x] No external side effects are allowed.

## Approved Fixture Plan

Thirty fabricated or irreversibly sanitized fixtures:

- four channel-normalization happy paths
- six required-field, HTML-conversion, length, and excluded-content boundaries
- four exact/content/cross-channel/lookup-failure duplicate cases
- eight category and priority cases covering every approved category and priority
- four OpenAI success, malformed-output, retry, and failure-fallback cases
- four Airtable, ClickUp, Slack, replay, and workflow-state cases

Fixture IDs `SF-FX-001` through `SF-FX-030` are reserved. The full thirty fixtures are required before integration testing, not before the skeleton build. Only `SF-FX-001` through `SF-FX-006` have been executed.

## Phase 1 Seed Fixtures

| Fixture ID | Scenario | Required skeleton expectation |
|---|---|---|
| `SF-FX-001` | Valid Gmail refund | Valid unified ticket; deterministic `p2-high` minimum |
| `SF-FX-002` | Valid Telegram technical-support request | Valid unified ticket with approved category |
| `SF-FX-003` | Invalid missing message text | Fail closed with no downstream processing |
| `SF-FX-004` | Exact duplicate | Mock exact-duplicate outcome |
| `SF-FX-005` | Possible content duplicate | Mock `possible_duplicate` and human review |
| `SF-FX-006` | Simulated AI failure | `other`, failed status, human review, empty draft, deterministic priority or P3 |

Exact dummy payload values may be created during the separately approved skeleton build and must contain no real data.

## Phase 1 Execution Evidence

| Fixture ID | Execution ID | Actual result | Status |
|---|---:|---|---|
| `SF-FX-001` | `7107` | Gmail normalized; valid; `new`; `refund`; deterministic `p2-high`; escalation eligible only after future storage | passed |
| `SF-FX-002` | `7108` | Telegram identifiers preserved; valid; `technical-support`; `p3-normal`; no escalation | passed |
| `SF-FX-003` | `7109` | Missing `message_text` failed closed; identity, duplicate, AI, draft, and actions skipped or empty | passed |
| `SF-FX-004` | `7110` | Mock `exact_duplicate`; existing-ticket reference; no new task; no repeat alert because escalation state was unchanged | passed |
| `SF-FX-005` | `7111` | Mock `possible_duplicate`; candidate reference; human review; not automatically suppressed | passed |
| `SF-FX-006` | `7112` | Mock AI failure after one retry; `other`; failed status; human review; empty draft; deterministic `p3-normal`; no AI-failure escalation | passed |

All six executions used manual mode and dummy data. Each final output reported matching expected fields, a valid ticket-ID pattern where applicable, a valid SHA-256 fingerprint where applicable, no credentials, no external nodes or calls, no customer reply, and no real-data use.

## Planned Test Cases

| ID | Scenario | Expected result | Side effect | Status |
|---|---|---|---|---|
| TC-001 | Valid Gmail request | Approved unified ticket produced | Controlled DEV effects only | not-run |
| TC-002 | Valid Telegram request | Same unified contract as equivalent Gmail input | Controlled DEV effects only | not-run |
| TC-003 | Gmail HTML/quoted content boundary | Approved body selection and normalization | None until defined | not-run |
| TC-004 | Telegram command/caption boundary | Approved message selection and normalization | None until defined | not-run |
| TC-005 | Missing source message ID | Invalid with machine-readable error | None | not-run |
| TC-006 | Missing message text | Invalid with machine-readable error | None | not-run |
| TC-007 | Malformed or oversized input | Safe rejection or manual review per approved rule | None | not-run |
| TC-008 | Unique ticket identity | ID matches approved format and collision expectations | None | not-run |
| TC-009 | Exact duplicate | Existing ticket updated and duplicate count incremented | No new task; alert only if escalation changed | not-run |
| TC-010 | Content or cross-channel match | `possible_duplicate`, candidate reference, and human review | Separate ticket; not automatically suppressed | not-run |
| TC-011 | Duplicate lookup failure | Fail closed with recoverable error | None | not-run |
| TC-012 | Valid AI classification | Output matches approved schema and enums | None | not-run |
| TC-013 | AI fails after one retry | `other`, failed status, human review, empty draft, deterministic priority or P3 | No customer-escalation alert from AI failure alone | not-run |
| TC-014 | AI and deterministic rule conflict | Deterministic override and audit trace | Conditional only if safe | not-run |
| TC-015 | Refund escalation | Approved priority/alert rule applied | One controlled Slack alert if eligible | not-run |
| TC-016 | Urgent or high-risk escalation | Approved rule and manual-review flag applied | One controlled Slack alert if eligible | not-run |
| TC-017 | Non-escalated valid ticket | Stored and tasked without alert | One DEV ticket and task | not-run |
| TC-018 | Airtable storage failure | Downstream task and alert suppressed | No downstream effect | not-run |
| TC-019 | ClickUp task failure/replay | Failure visible; no duplicate task | Controlled retry only if approved | not-run |
| TC-020 | Slack alert failure/replay | Failure visible; no duplicate alert | Controlled retry only if approved | not-run |
| TC-021 | Draft response boundary | Draft stored for review | No customer send | not-run |
| TC-022 | Real-data or secret guard | Processing stopped and exposure not reproduced | None | not-run |
| TC-023 | Workflow state check | Workflow remains inactive after testing | None | not-run |

## Required Evidence

For each approved executed case, record:

- fixture ID and sanitization confirmation
- workflow ID and version
- execution ID
- exact expected and observed result
- side-effect record IDs or safe evidence
- status: `passed`, `failed`, `blocked`, `not-run`, or `deferred`
- cleanup outcome and final inactive state

`Test Results.md` must not be created until the testing lifecycle begins and real execution evidence exists.

## Approved Non-Functional Test Targets

- Capacity: 100 tickets per day; peak 10 messages per five minutes.
- DEV execution retention: seven days.
- DEV Airtable, ClickUp, and Slack test artifact retention: 30 days.
- Recovery: RTO four hours and RPO 24 hours.
- Replay: manual using source-message identity; no automatic replay.
- OpenAI budget: 500 calls or USD 5 per month, whichever occurs first.
- Owner: Mervin.

## Exit Criteria

- [ ] Every critical approved test has evidence.
- [ ] No critical failures remain unresolved.
- [ ] Invalid, duplicate, AI-failure, and dependency-failure paths are verified.
- [ ] No automatic customer reply exists or occurred.
- [ ] Only approved controlled DEV effects occurred.
- [ ] Limitations and deferred cases are current.
- [ ] Workflow remains inactive.
- [ ] Mervin records the test-gate decision.

### Phase 1 Exit Criteria

- [x] Every authorized seed fixture has execution evidence.
- [x] Six fixtures passed and none failed.
- [x] Invalid, exact-duplicate, possible-duplicate, deterministic override, and mocked AI-failure behavior were verified.
- [x] Ticket-ID format and SHA-256 fingerprint shape were verified where applicable.
- [x] No automatic customer reply, credential, external call, or real-data path existed or occurred.
- [x] Workflow remained inactive after testing.
- [x] Integration, performance, retention, recovery, and production testing remain explicitly not-run or deferred.

## Approval

- Test owner: Mervin
- Phase 1 skeleton suite: `SF-FX-001` through `SF-FX-006`
- Integration suite: `SF-FX-001` through `SF-FX-030`, remaining fixture definitions deferred
- Plan approval date: 2026-07-25
- Execution authorization: approved by Mervin for `SF-FX-001` through `SF-FX-006` on 2026-07-25
- Phase 1 result: passed, 6 of 6

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Known Limitations|Known Limitations]]
