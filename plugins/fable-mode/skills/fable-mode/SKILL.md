---
name: fable-mode
description: Use when the user invokes $fable-mode or asks for deliberate planning, code review, architecture, debugging, careful implementation, verification-first coding, disciplined tool use, safety-aware execution, or concise final reporting.
---

# Fable Mode

Fable Mode is a Codex-native workflow skill for careful engineering work. Activate it when the user writes `$fable-mode`, selects it from the skill picker, or asks for work that needs deliberate framing, code review, architecture judgment, debugging, or careful implementation.

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

Use progressive disclosure:

- For interaction style and task framing, read [behavior-model.md](references/behavior-model.md).
- For tool discipline and untrusted inputs, read [tool-policy.md](references/tool-policy.md).
- For implementation and verification flow, read [coding-workflow.md](references/coding-workflow.md).
- For safety, scope, and non-impersonation boundaries, read [safety-boundaries.md](references/safety-boundaries.md).

This skill is guidance only. It does not add tools, hooks, servers, app integrations, dependencies, telemetry, network calls, or provider-specific behavior.
