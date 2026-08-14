# Change Impact Analysis

Explain what the modification can affect, based on repository evidence.

## Layers

### Direct
Files, classes, methods, or configuration changed.

### Behavioral
Observable behavior changed or intentionally preserved.

### Indirect
Known callers, consumers, state transitions, persistence, network/device boundaries, or tests affected.

### Risk
Potential regressions and assumptions.

## Evidence rule

Do not infer a dependency solely because a name looks related. Use imports, references, call sites, tests, configuration, and actual data flow.

## Report shape

```text
Direct:
- ...

Behavior:
- ...

Indirect:
- ...

Risk:
- ...

Verification:
- ...
```
