---
type: knowledge
status: active
---

# Canonical Content Fingerprinting for Duplicate Detection

## Key Idea

Content fingerprints are stable only when every input component is normalized and composed in a deterministic order before hashing. Component boundaries must remain explicit so different field combinations cannot collapse into the same concatenated text accidentally.

## Verified Pattern

The verified composition normalized sender, subject, and message components individually using:

- Unicode NFKC normalization
- lowercase conversion
- removal of zero-width characters
- normalized line endings
- collapsed repeated whitespace
- trimmed leading and trailing whitespace

The normalized components were joined in a fixed order with the Unicode Unit Separator (`U+001F`) and the resulting canonical string was hashed with SHA-256. An absent optional component remained an empty string while its separators were preserved.

This produced a repeatable content lookup value in controlled inactive DEV executions.

## Conceptual Composition

When source channel is intentionally part of the fingerprint contract, a generalized composition can be expressed as:

```text
source_channel
+ separator
+ normalized_sender
+ separator
+ normalized_subject
+ separator
+ normalized_message
```

Then hash the complete canonical string. The chosen component list, normalization rules, field order, separator, empty-value behavior, and hash algorithm must remain stable for fingerprints to remain comparable.

The verified source used channel and source-message identifiers as a separate exact-identity key rather than including channel in the three-component content hash. Including channel in the content hash is therefore a design variant, not part of the verified formula.

## Exact Identity vs Content Fingerprint

- An exact source identifier answers whether two records refer to the same source event or message under the identifier contract.
- A content fingerprint answers whether normalized content components produce the same canonical value.

These signals are related but not equivalent. Two messages can share content without sharing source identity, and formatting differences can be intentionally removed by normalization. A content match can therefore be treated as a duplicate candidate rather than automatic proof of identical origin.

## Why Explicit Boundaries Matter

Concatenating fields without separators can create ambiguous compositions. For example, components `ab` + `c` and `a` + `bc` produce the same raw concatenation. A fixed separator and field order preserve the structure of the canonical input.

## Evidence Scope and Limitations

The normalization, fixed-boundary composition, and SHA-256 input were verified in an inactive schema-alignment batch. This evidence does not prove protection against concurrent duplicate creation, race conditions, distributed locking failures, semantic paraphrases, or every duplicate case. Production-grade concurrent-arrival locking remained explicitly unverified.

## Related

- [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[Idempotent External Task Creation by Reference Reuse]]
