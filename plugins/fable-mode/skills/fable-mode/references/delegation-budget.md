# Delegation Budget

Delegation budget controls optional subagent use.

Subagents are not the default. They are a context-isolation and evidence-separation tool for work where one main context may blur independent evidence lanes.

The main agent always owns:

- output lock
- user intent
- final scope
- write coordination
- verification synthesis
- final response
- residual risk

## Budgets

### A0 - No delegation

Default for most work.

Use for L0, L1, and ordinary L2 tasks unless a specific evidence lane would clearly improve correctness.

### A1 - One read-only specialist

Use when one focused evidence question would help:

- unfamiliar codebase exploration
- unknown-cause debugging
- API or documentation confirmation
- review support
- one isolated risk area

The specialist should receive one narrow question and return distilled evidence. The main agent decides what to do.

### A2 - Parallel read-only specialists

Use when independent audit lanes can be examined in parallel:

- security
- tests
- maintainability
- docs or API contracts
- UI or UX
- performance evidence

Each specialist should stay read-only and answer one lane. The main agent merges findings, removes duplicates, calibrates severity, and decides next steps.

### A3 - Controlled worker split

Use only for large migrations, multi-module work, or user-requested parallel implementation.

A3 requires explicit user request or approval. The parent must coordinate writes, avoid overlapping edits, verify integration, and keep final responsibility.

## Rules

- Delegation is for evidence, not intelligence theater.
- Prefer read-only delegation.
- Avoid write-heavy parallel work.
- Do not delegate the output lock.
- Do not delegate final judgment.
- Do not imply that this plugin automatically starts subagents.
- Do not use delegation to make L0 or L1 work heavy.
- If delegation is unavailable, continue with A0 and state limits only when that affects the result.

## Fit with other budgets

Delegation must support Output Lock, Procedure Budget, Tool Budget, Grounding, and Capability Fit.

If delegation would exceed the task's procedure or tool budget, do not use it.
