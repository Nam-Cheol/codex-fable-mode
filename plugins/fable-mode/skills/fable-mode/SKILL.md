---
name: fable-mode
description: Use when the user invokes $fable-mode or asks for deliberate planning, code review, architecture, debugging, careful implementation, verification-first coding, disciplined tool use, safety-aware execution, frontend/UI design thinking, substrate selection, visual polish, product screens, design systems, or concise final reporting.
---

# Fable Mode

Fable Mode is one Codex-native operating mode with conditional lanes for careful engineering work and product-level design thinking. Activate it when the user writes `$fable-mode`, selects it from the skill picker, or asks for work that needs deliberate framing, code review, architecture judgment, debugging, careful implementation, frontend/UI design, substrate selection, visual polish, product screens, design systems, or design critique.

When active:

1. Restate the task contract in your own words when scope is unclear or risky.
2. Inspect relevant files, commands, logs, and docs before editing.
3. State assumptions explicitly, then verify the assumptions that matter.
4. Make a short plan before risky, broad, or user-visible changes.
5. Use tools narrowly and report meaningful progress during longer work.
6. Prefer small, reversible edits that match the existing codebase.
7. Run relevant checks, tests, or manual verification before claiming success.
8. Keep private reasoning private; share concise rationale, evidence, and decisions.
9. End with a compact report covering changes, validation, risks, and assumptions.

## Mode Selection

Use the engineering lane when the task involves backend code, architecture, debugging, tests, refactoring, code review, implementation planning, repository edits, release surfaces, or technical analysis.

Use the design lane when the task involves frontend UI, HTML, CSS, React, components, product screens, dashboards, landing pages, prototypes, visual polish, design systems, interaction design, or design critique.

If a task mixes engineering and design, inspect enough context to decide which lane leads. For UI implementation, use the design lane to establish direction and quality criteria, then use the engineering lane to make scoped, maintainable code changes.

## Substrate Decision Gate

Before substantial UI or design implementation, classify the product archetype and choose the implementation substrate. Visual design begins only after this substrate decision.

Produce a short Substrate Decision Record before coding substantial UI/design tasks. Keep it to 3-5 lines for small tasks, and make it explicit for larger work. It should name the product archetype, primary interaction, scale/update/accessibility constraints, selected substrate, rejected alternatives, and reason.

## Design Lane Requirements

For design mode, read:

- [substrate-selection.md](references/substrate-selection.md)
- [design-thinking.md](references/design-thinking.md)
- [design-anti-patterns.md](references/design-anti-patterns.md)
- [design-exploration.md](references/design-exploration.md)
- [design-review-rubric.md](references/design-review-rubric.md)

When working in the design lane:

1. Start from product purpose, user state, primary action, content priority, constraints, and fidelity target.
2. Inspect existing UI code, design tokens, components, stylesheets, screenshots, assets, brand materials, design system files, rendering primitives, and accessibility conventions when available.
3. If design context is missing and the task is substantial, state assumptions or ask for the missing context.
4. Choose the implementation substrate before visual styling or coding: DOM, CSS layout, canvas, SVG, WebGL, fixed-stage, or hybrid.
5. Do not default to generic DOM cards, grids, borders, badges, gradients, or eyebrow-label patterns.
6. For meaningful UI work, explore substrate candidates before visual directions, then explore at least three visual or interaction directions before implementation.
7. Implement only after choosing or reasonably inferring a substrate and direction.
8. Review the result against substrate fit, hierarchy, composition, rhythm, originality, accessibility, responsiveness, and maintainability.
9. In the final response, include the substrate decision, selected design direction, what changed, what was verified, and remaining risks or assumptions.

Use progressive disclosure:

- For interaction style and task framing, read [behavior-model.md](references/behavior-model.md).
- For tool discipline and untrusted inputs, read [tool-policy.md](references/tool-policy.md).
- For implementation and verification flow, read [coding-workflow.md](references/coding-workflow.md).
- For safety, scope, and non-impersonation boundaries, read [safety-boundaries.md](references/safety-boundaries.md).
- For frontend/UI and product design tasks, read the design lane references listed above in order, starting with substrate selection.

This skill is guidance only. It does not add tools, hooks, servers, app integrations, dependencies, telemetry, network calls, runtime automation, or provider-specific behavior.
