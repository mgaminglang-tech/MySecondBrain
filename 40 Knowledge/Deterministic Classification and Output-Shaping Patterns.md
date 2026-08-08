---
type: knowledge
status: active
---

# Deterministic Classification and Output-Shaping Patterns

## Key Idea

A deterministic classifier is easier to inspect when transformation, rule evaluation, response logic, and final output shaping remain distinct stages.

## Conceptual Flow

```text
Input
→ Normalize
→ Classify
→ Response Logic
→ Final Shape
```

## Verified Patterns

### Normalize before classifying

Normalization gives later rules a stable representation. Typical normalization may standardize case, whitespace, missing values, and field names. Keeping it separate makes it easier to determine whether a defect came from input preparation or classification logic.

### Separate classification from response generation

Classification should determine the category or rule outcome. Response logic can then decide wording, review requirements, routing hints, or other consequences. Mixing both concerns into one transformation makes rule precedence and output contracts harder to inspect.

### Order competing rules deliberately

A message can match more than one keyword or condition. Deterministic systems therefore need an explicit precedence order. Changing rule order can change the selected category even when the individual conditions are unchanged.

Rule ordering should be treated as part of the classifier’s behavior, not as an incidental implementation detail.

### Define a deterministic fallback

A final fallback prevents unmatched inputs from being silently dropped. The fallback should be distinguishable from a positive rule match so downstream systems can route it for general handling or review.

### Label confidence accurately

A confidence label emitted by fixed rules is a rule-derived output. It is not a calibrated probability and should not be presented as model confidence. If numeric values are used, their meaning should be defined by the rule system.

### Shape the final output explicitly

The final stage should emit only the documented downstream schema. This prevents normalized text, matching flags, intermediate fields, and internal reasoning aids from leaking into later systems.

A narrow final schema also makes validation clearer: downstream consumers depend on a stable contract rather than the classifier’s internal working state.

## Evidence Scope and Limitations

The separation, precedence, fallback, and final-shaping patterns were verified through multiple branches of an inactive, credential-free deterministic workflow. The evidence supports rule-based classification behavior only. It does not establish performance for probabilistic AI classification, broad language coverage, production traffic, or untested categories.

## Related

- [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[Agent Operating Standard]]
