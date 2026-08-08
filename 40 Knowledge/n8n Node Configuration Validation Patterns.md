---
type: knowledge
status: active
---

# n8n Node Configuration Validation Patterns

## Key Idea

An n8n workflow can look structurally valid while still containing a parameter-storage or code-syntax defect. Configuration, graph, code, and execution validation answer different questions and should not be treated as substitutes for one another.

## Why It Matters

A fixture may be valid JSON while the node parameter holding it uses the wrong internal representation. Likewise, a Code node can fit the workflow schema while containing JavaScript that does not compile. These defects can remain hidden until execution unless each validation layer is checked deliberately.

## Verified Patterns

- In Set/Edit Fields JSON mode, `jsonOutput` may need to be stored as a serialized JSON string even when the intended output object is structurally correct.
- Saved node configuration and runtime output are separate evidence. Inspecting only the desired fixture does not prove the node stored it correctly.
- Node-schema validation does not compile JavaScript inside a Code node. A separate JavaScript syntax or compilation check can expose defects missed by schema validation.
- Temporary pin data can isolate one controlled fixture without permanently rewriting the saved input node.
- After pin-based testing, the saved configuration, pin state, workflow version, and inactive state should be inspected again.

## Validation Layers

| Layer | What it establishes | What it does not establish |
| --- | --- | --- |
| Parameter configuration | Required fields and storage types are represented correctly. | The node produces the intended runtime value. |
| Workflow graph | Nodes and connections form the expected structure. | Embedded code compiles or business behavior is correct. |
| Code syntax | JavaScript parses or compiles. | The code handles real inputs correctly. |
| Controlled execution | The tested fixture produces the observed result. | Untested inputs, integrations, or production behavior also work. |

## Generic Example

A node intended to emit an object may require a serialized value such as:

```json
{"status":"ready","count":1}
```

The visible object shape can be correct while the saved parameter type is wrong. Inspect both the stored node configuration and the controlled execution result.

## When to Use

These patterns are useful when building or reviewing Set/Edit Fields nodes, Code nodes, imported workflows, generated workflow definitions, and fixture-driven DEV tests.

## Evidence Scope and Limitations

The patterns were observed in an inactive, dummy-data DEV workflow where parameter-storage and JavaScript-syntax defects were reproduced and corrected. They do not replace controlled execution testing, integration testing, or production verification.

## Related

- [[30 Systems/n8n/Build and Test a DEV Workflow|Build and Test a DEV Workflow]]
- [[Agent Operating Standard]]
