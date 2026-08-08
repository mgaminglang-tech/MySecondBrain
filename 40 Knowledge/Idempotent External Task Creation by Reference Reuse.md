---
type: knowledge
status: active
---

# Idempotent External Task Creation by Reference Reuse

## Key Idea

An external create operation becomes safer to replay when the system of record stores the external object reference and checks it before attempting another create.

## Pattern

After an external task is created successfully, store its stable external reference alongside the originating record. On later processing:

```text
Existing external reference?
→ yes: verify and reuse
→ no: deterministic lookup
   → exactly one match: reuse
   → no match: create once, then store the reference
   → ambiguous result: read and verify; do not retry blindly
```

### Reference first

A stored reference is the strongest direct signal that the originating record already has an external task. When appropriate, read the referenced object to confirm that it still exists and corresponds to the expected business record.

### Deterministic lookup second

If no stored reference exists, search using a stable business identifier designed for that purpose. Exactly one valid match can be reused. Multiple or uncertain matches should remain ambiguous rather than triggering another create automatically.

### Create once, then persist the result

When no valid reference or lookup match exists, create once and persist the returned external reference immediately. The stored reference becomes the replay guard for later runs.

### Read after ambiguous writes

A timeout or transport error does not prove that a write failed. The external service may have created the task while the response was lost. Retrying the create blindly can therefore produce duplicates. Read by stored reference or deterministic identifier before deciding whether another create is safe.

## Verified Evidence

An isolated sanitized fixture created exactly one external task and stored its reference. Replaying the same fixture reused that task, performed no additional create, and left the stored reference unchanged. This verifies the reference-reuse behavior for that controlled case.

## What the Evidence Does Not Prove

The source evidence did not verify:

- full end-to-end production wiring
- concurrent arrivals or race-condition protection
- distributed locking
- every timeout or ambiguous-write path
- missing, deleted, or mismatched referenced objects
- all search ambiguity and recovery paths

Reference reuse reduces duplicate risk but does not replace concurrency control, atomic writes, reconciliation, or provider-specific idempotency features when those are required.

## Related

- [[30 Systems/n8n/Handle a Failed Production Workflow|Handle a Failed Production Workflow]]
- [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[Canonical Content Fingerprinting for Duplicate Detection]]
