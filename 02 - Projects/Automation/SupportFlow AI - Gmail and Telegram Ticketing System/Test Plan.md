---
type: project-note
status: in-progress
phase: phase-2-architecture-alignment
testing_status: not-run-for-approved-architecture
client: internal-demo
owner: Mervin
created: 2026-07-25
updated: 2026-07-28
tags:
  - client-automation
  - testing
---

# Test Plan

## Status

- Testing status: **not-run for the newly approved compact architecture**
- Environment: DEV
- Workflow: `SupportFlow AI - Gmail and Telegram Ticketing System`
- Workflow state: existing workflow `cyiCqsjLQdB7apjP` is inactive; architecture alignment and connection audit are pending
- Credentials and destinations: preserve approved DEV references; no new credential or destination action is authorized
- Data: dummy or sanitized only
- Planned fixture count: 30

Historical Phase 1 and isolated ClickUp evidence remains recorded below but does not validate the newly approved architecture. No integration, performance, demo, or production readiness is claimed.

## Entry Criteria

- [x] Clean architecture documented and approved.
- [ ] Complete inactive main workflow exists with Gmail and Telegram triggers and no Manual DEV Trigger.
- [ ] Separate `SupportFlow - Error Handler` exists and matches its contract.
- [ ] Full connection/configuration audit passes.
- [ ] All workflow references, credentials, IDs, mappings, and stop paths resolve.
- [ ] Gmail, Telegram, and Slack send actions remain absent, disabled, or mock-only.
- [ ] Exact consolidated batch and allowed side effects receive separate approval.
- [ ] Workflow remains inactive and unpublished immediately before execution.

## Consolidated Test Strategy

Testing begins only after the entire inactive structure and connections are ready.

| Order | Scenario | Required result | Initial external-send boundary |
|---|---|---|---|
| 1 | Gmail happy path | Shared schema, Airtable reference, Gemini classification, ClickUp reuse/create, Gmail draft payload, compact audit | No email or Slack send |
| 2 | Telegram happy path | Same shared processing contract, Telegram references preserved, reply payload prepared | No Telegram or Slack send |
| 3 | Duplicate replay | Exact Airtable/ClickUp references reused; no duplicate record or task | No new notification-producing write |
| 4 | Failure and fallback | Approved stop or deterministic Gemini fallback; Error Handler returns controlled result | No external send |

Each scenario must be run sequentially with dummy or sanitized DEV data. Stop the batch on real data, unexpected writes, authentication/billing/security failure, unresolved ambiguity, broken references, or workflow activation.

## Historical Supporting Fixture Plan

Thirty fabricated or irreversibly sanitized fixtures:

- four channel-normalization happy paths
- six required-field, HTML-conversion, length, and excluded-content boundaries
- four exact/content/cross-channel/lookup-failure duplicate cases
- eight category and priority cases covering every approved category and priority
- Gemini valid-output, malformed-output, timeout, quota, retry-exhaustion, and safe-fallback cases
- four Airtable, ClickUp, Slack, replay, and workflow-state cases

Fixture IDs `SF-FX-001` through `SF-FX-030` remain reserved as supporting regression coverage. Only `SF-FX-001` through `SF-FX-006` have historical execution evidence; they must not be treated as the consolidated architecture test.

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

## Schema-Alignment Rerun Evidence

| Fixture ID | Execution ID | Result |
|---|---:|---|
| `SF-FX-001` | `7113` | passed |
| `SF-FX-002` | `7114` | passed |
| `SF-FX-003` | `7115` | passed |
| `SF-FX-004` | `7116` | passed |
| `SF-FX-005` | `7117` | passed |
| `SF-FX-006` | `7118` | passed |

The rerun verified schema `0.1.0`, approved Gmail and Telegram source mapping, fail-closed validation, ticket-ID format, the U+001F-composed SHA-256 fingerprint contract, mocked duplicate and Gemini behavior, deterministic rules, zero external effects, and final inactive state. Fixtures `SF-FX-007` through `SF-FX-030` remain not-run.

## Defined Phase 2 Fixtures — Not Run

All addresses use the reserved `.invalid` domain, Telegram identifiers are fabricated, dependency outcomes are mocked until an integration batch is separately authorized, and `schema_version` is `0.1.0`. `None` under downstream actions means no Airtable write, ClickUp task, Slack alert, or customer response.

| ID | Input | Setup or mocked dependency state | Expected category | Expected priority | Duplicate state | Human review | Draft behavior | Expected downstream actions | Expected stop condition | Required evidence |
|---|---|---|---|---|---|---|---|---|---|---|
| `SF-FX-007` | Gmail `m-007`, thread `t-007`, `billing@example.invalid`, HTML-only billing question | HTML-to-text succeeds; dependencies healthy | `billing` | `p3-normal` | `new` | false | Non-empty sanitized review draft | One Airtable record and one ClickUp task; no Slack alert | Stop if HTML, IDs, or schema map incorrectly | Normalized payload, validation, fingerprint, record/task refs |
| `SF-FX-008` | Telegram update `8008`, message `108`, chat `9008`, caption-only product question | New-message update; no reply; dependencies healthy | `product-question` | `p3-normal` | `new` | false | Non-empty sanitized review draft | One record and task; no alert | Stop on edited update, missing chat filter, or non-null parent ID | Telegram mapping showing event/message/conversation and null parent |
| `SF-FX-009` | Gmail `m-009` with timestamp `not-a-date` | No dependency calls allowed | null (`not-run`) | null (`not-run`) | `unknown` | true | Empty | None | Validation failure stops before identity/dedupe/Gemini | Machine-readable timestamp error and zero effects |
| `SF-FX-010` | Gmail `m-010` order-delivery text exactly 5,000 characters | Dependencies healthy | `order-delivery` | `p3-normal` | `new` | false | Review draft within approved limits | One record and task; no alert | Stop if valid boundary is truncated or rejected | Character count, accepted validation, refs |
| `SF-FX-011` | Telegram message text 5,001 characters | No dependency calls allowed | null (`not-run`) | null (`not-run`) | `unknown` | true | Empty | None | Oversize validation failure | Count, validation code, zero effects |
| `SF-FX-012` | Gmail payload with empty `message_id` | No dependency calls allowed | null (`not-run`) | null (`not-run`) | `unknown` | true | Empty | None | Required-field failure | Missing-ID error and zero effects |
| `SF-FX-013` | Telegram message semantically identical to retained Gmail ticket but with distinct source identity | Airtable returns same fingerprint candidate within 72 hours | Candidate category | Deterministic or Gemini result, minimum unchanged | `possible_duplicate` | true | Review draft allowed | One separate record and task; conditional alert only by rules | Stop if automatically suppressed or marked exact | Candidate reference, cross-channel evidence, separate record/task |
| `SF-FX-014` | Telegram “account taken over” request | Gemini suggests lower priority; dependencies healthy | `account-access` | `p1-critical` | `new` | true | Non-empty review draft | One record, one task, one Slack alert | Stop if Gemini lowers P1 or alert occurs before storage | Rule ID, override trace, three effect refs |
| `SF-FX-015` | Gmail safety/legal threat text using fabricated facts | Gemini suggests `p3-normal` | `other` | `p1-critical` | `new` | true | Carefully bounded review draft | One record, task, alert | Stop if deterministic P1 is not applied | Sanitized input, rule trace, refs |
| `SF-FX-016` | Telegram widespread service-outage report | Gemini returns `technical-support`, `p3-normal` | `technical-support` | `p1-critical` | `new` | true | Review draft | One record, task, alert | Stop if outage rule is missed | Override and alert eligibility evidence |
| `SF-FX-017` | Gmail order-delivery request explicitly stating urgent | Dependencies healthy | `order-delivery` | `p2-high` | `new` | true | Review draft | One record, task, alert | Stop if explicit urgency does not raise P2 | Rule trace and refs |
| `SF-FX-018` | Telegram repeated serious product failure complaint | Dependencies healthy | `feedback-complaint` | `p2-high` | `new` | true | Review draft | One record, task, alert | Stop if repeated-serious-failure rule is missed | Rule trace and refs |
| `SF-FX-019` | Gmail non-urgent positive feedback | Dependencies healthy | `feedback-complaint` | `p4-low` | `new` | false | Optional review draft | One record and task; no alert | Stop if sentiment alone changes priority or alerts | Category/priority/sentiment and no-alert evidence |
| `SF-FX-020` | Telegram general “other” inquiry | Gemini returns valid approved structured JSON | `other` | `p3-normal` | `new` | false | Non-empty review draft | One record and task; no alert | Stop if JSON schema or enum validation fails | Raw sanitized Gemini structure, schema result, refs |
| `SF-FX-021` | Gmail billing inquiry | First Gemini output malformed; one retry returns valid JSON | `billing` | `p3-normal` | `new` | false | Draft from valid retry | One record and task; no alert | Stop after more than one retry or invalid second output | Attempt count, validation errors, valid retry evidence |
| `SF-FX-022` | Telegram normal support inquiry | Gemini times out twice | `other` | `p3-normal` | `new` | true | Empty | One record using fallback if storage is healthy; task allowed; no customer-escalation alert | Stop Gemini after one retry; stop downstream if fallback contract cannot be formed | Timeout attempts, fallback fields, no AI-failure alert |
| `SF-FX-023` | Gmail normal support inquiry | Gemini returns rate-limit/quota failure twice | `other` | `p3-normal` | `new` | true | Empty | Safe fallback record/task only if review-cycle stop has not been reached; no customer alert | Stop Gemini testing on exhausted quota, repeated limits, call 500, or billing signal | Attempt count, quota state, usage counter, stop record |
| `SF-FX-024` | Valid Telegram technical-support request | Airtable duplicate read fails after approved read retries | null (`not-run`) | null (`not-run`) | `unknown` | true | Empty | None | Stop before Gemini and all creates | Two retry/backoff records, 15-second timeout evidence, safe error |
| `SF-FX-025` | Valid Gmail billing request | Dedupe says new; Airtable create persistently fails | `billing` | `p3-normal` | `new` | true after failure | Draft retained in safe processing context only | No ClickUp task or Slack alert | Stop after controlled create handling; never blind retry | Dedupe recheck, create error, zero downstream effects |
| `SF-FX-026` | Replay of a valid Gmail request after ambiguous Airtable create response | Pre-create recheck finds existing ticket ID/dedupe key | Original category | Original priority | `exact_duplicate` | According to original ticket | No new draft required | Update duplicate count only; no new task; alert only if escalation state changed | Stop if a second record would be created | Lookup evidence, one record ID, count increment |
| `SF-FX-027` | Stored valid order-delivery ticket | ClickUp create fails persistently | `order-delivery` | `p3-normal` | `new` | true after failure | Stored review draft unchanged | Airtable record remains; no duplicate task; Slack only if independently eligible | Stop task branch after bounded handling | Airtable ref, task error, operational error context |
| `SF-FX-028` | Replay of stored technical-support ticket | Existing ClickUp task reference or ticket-ID custom-field match found | `technical-support` | `p3-normal` | `new` | false | Existing draft unchanged | Reuse existing task; create none | Stop if a duplicate task would be created | Existing task lookup and single task ID |
| `SF-FX-029` | Stored P2 refund ticket eligible for alert | Slack send fails | `refund` | `p2-high` | `new` | true | Review draft stored | Airtable record and ClickUp task remain; alert failure recorded | Stop alert retry when idempotency cannot be proven | Ticket/task refs, Slack error, unchanged alert-state field |
| `SF-FX-030` | Exact duplicate of previously alerted P2 refund ticket with unchanged escalation state | Existing record, task, and alerted state are present | `refund` | `p2-high` | `exact_duplicate` | true | No new draft required | Increment duplicate count only; no task or Slack alert | Stop if duplicate task/alert is attempted | One record/task/alert reference, count change, suppression trace |

### Fixture Coverage Index

- Categories: refund (`001`, `029`, `030`), technical-support (`002`, `016`, `024`, `028`), billing (`007`, `021`, `025`), product-question (`008`), order-delivery (`010`, `017`, `027`), account-access (`014`), feedback-complaint (`018`, `019`), other (`015`, `020`, `022`, `023`).
- Priorities: P1 (`014`–`016`), P2 (`001`, `017`, `018`, `029`, `030`), P3 (normal/default fixtures), P4 (`019`).
- Gmail and Telegram mapping: `001`, `002`, `007`, and `008`; invalid fields and boundaries: `003`, `009`–`012`.
- Duplicate and idempotency: `004`, `005`, `013`, `026`, `028`, `030`.
- Gemini: `006`, `020`–`023`; Airtable: `024`–`026`; ClickUp: `027`–`028`; Slack: `029`–`030`.
- Retry, stop, and operational-error behavior: `021`–`030`.

Fixtures `SF-FX-007` through `SF-FX-030` are definitions only. Their status is `not-run`; no execution, credential, connection, or external effect is authorized.

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

## ClickUp Fixture Execution Evidence

| Stage | Execution IDs | Actual result | Status |
|---|---|---|---|
| `SF-CUP-001` creation | `7127`, `7128`, `7129` | Airtable record `rechUtKgq1V0poegN` produced task `86d3ut8nt`; one task created; assigned to Mervin; status `to do`; Airtable changed only at `clickup_task_id` | passed |
| `SF-CUP-001` replay | `7130`, `7131`, `7132` | Existing task `86d3ut8nt` reused; zero new tasks; final task count `1`; Airtable reference unchanged; zero ClickUp writes, notification-producing writes, or Airtable writes | passed |

The isolated workflow `ths9GF0Z819GrHYe` remained inactive and unpublished. The retained task name is `[P3] SF-20260727-7A3F1C2D — billing — Dummy invoice question`, linked to ticket `SF-20260727-7A3F1C2D`. Production-grade concurrency locking remains deferred.

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
| TC-019 | ClickUp task failure/replay | Failure visible; no duplicate task | Controlled retry only if approved | replay passed; failure path not-run |
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
- Gemini: free tier only and maximum 500 calls per review cycle; paid usage prohibited.
- Airtable: maximum 100 created DEV test records per review cycle.
- ClickUp: maximum 100 created DEV tasks per review cycle.
- Slack: maximum 30 DEV test alerts per review cycle.
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
- Approved architecture suite: Gmail happy path, Telegram happy path, duplicate replay, and failure/fallback
- Approved architecture execution status: not-run
- Execution authorization for the consolidated suite: Not Yet Defined
- Phase 1 skeleton suite: `SF-FX-001` through `SF-FX-006`
- Integration suite: `SF-FX-001` through `SF-FX-030`; fixtures `SF-FX-007` through `SF-FX-030` are defined but not-run
- Plan approval date: 2026-07-25
- Execution authorization: approved by Mervin for `SF-FX-001` through `SF-FX-006` on 2026-07-25
- Phase 1 result: passed, 6 of 6

## Related Notes

- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Requirements|Requirements]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Business Rules|Business Rules]]
- [[02 - Projects/Automation/SupportFlow AI - Gmail and Telegram Ticketing System/Known Limitations|Known Limitations]]
