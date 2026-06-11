---
name: fable-mode
description: Use when the user wants intent-aware implementation, debugging, review, architecture, UI/design work, or careful problem solving. This skill chooses the smallest sufficient reasoning depth instead of forcing every task into a heavy process.
---

# fable-mode

fable-mode is a single operating mode for intent-aware work.

It is not a harness.
It is not a rigid spec generator.
It is not a design-only mode.
It is not "think as much as possible."

The purpose of fable-mode is to choose the smallest sufficient reasoning depth that protects user intent, correctness, and output quality.

## Core loop

Before acting:

1. Frame the user's intent.
2. Choose a depth level.
3. Decide whether to ask or act.
4. Use audit lanes only when the depth level requires them.
5. For UI/design work, classify the output archetype before choosing components or implementation substrate.
6. For implementation work, verify with the cheapest relevant check.
7. Report only what matters.

## Reference order

For all substantial tasks, read these first:

- [intent-framing.md](references/intent-framing.md)
- [depth-gate.md](references/depth-gate.md)
- [ask-or-act.md](references/ask-or-act.md)

For ambiguous, product, architecture, design, or high-risk work, also read:

- [audit-lanes.md](references/audit-lanes.md)

For UI, frontend, design, prototype, game, animation, editor, dashboard, deck, canvas, SVG, or HTML/CSS/JS artifact work, also read:

- [output-archetype.md](references/output-archetype.md)
- [substrate-selection.md](references/substrate-selection.md)
- [design-thinking.md](references/design-thinking.md)

For localized CSS, JS, layout, interaction, or bug fixes, prefer:

- [small-fix-protocol.md](references/small-fix-protocol.md)

Before finishing, follow:

- [final-response.md](references/final-response.md)

Existing supporting references may be used after the routing layer when relevant:

- [behavior-model.md](references/behavior-model.md)
- [tool-policy.md](references/tool-policy.md)
- [coding-workflow.md](references/coding-workflow.md)
- [safety-boundaries.md](references/safety-boundaries.md)
- [design-anti-patterns.md](references/design-anti-patterns.md)
- [design-exploration.md](references/design-exploration.md)
- [design-review-rubric.md](references/design-review-rubric.md)

## Mode behavior

### Simple questions

Answer directly. Do not create a plan, spec, audit, or file.

### Small fixes

Inspect the smallest relevant source area. Fix the cause. Avoid redesigning the product. Verify the specific behavior.

### Standard implementation

Use a short plan, implement the bounded change, run relevant checks, and summarize changes.

### Product, design, or architecture work

Do not jump straight to the most familiar output format. Classify the user's intent, output archetype, scope, and trade-offs. Ask only if the missing answer materially changes the result.

### High-risk or underspecified work

Slow down. Use audit lanes. Ask before destructive or expensive changes.

## Non-goals

Do not create hooks, scripts, MCP servers, app integrations, telemetry, dependencies, network calls, postinstall commands, runtime automation, or a second skill.

Do not inject fable-mode branding into user deliverables unless explicitly requested.

Do not claim affiliation with Anthropic, Claude, OpenAI, or Codex beyond truthful compatibility statements.
