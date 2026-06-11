# Validation

This plugin is documentation-only. It should stay installable as a Codex plugin without adding hooks, MCP servers, app integrations, scripts, dependencies, telemetry, postinstall commands, or runtime automation.

Run the checks below from the repository root.

## Manifest JSON

```bash
python3 -m json.tool .agents/plugins/marketplace.json >/dev/null
python3 -m json.tool plugins/fable-mode/.codex-plugin/plugin.json >/dev/null
```

Expected result: both commands exit successfully and print no output.

## Required Skill Files

```bash
test -f plugins/fable-mode/skills/fable-mode/SKILL.md
test -f plugins/fable-mode/skills/fable-mode/references/depth-gate.md
test -f plugins/fable-mode/skills/fable-mode/references/ask-or-act.md
test -f plugins/fable-mode/skills/fable-mode/references/output-archetype.md
test -f plugins/fable-mode/skills/fable-mode/references/substrate-selection.md
```

Expected result: each command exits successfully.

## No Runtime Extensions

```bash
find plugins/fable-mode -name hooks -o -name ".mcp.json" -o -name ".app.json" -o -name scripts
```

Expected result: no output.

## Optional Full File Check

```bash
test -f plugins/fable-mode/skills/fable-mode/references/intent-framing.md
test -f plugins/fable-mode/skills/fable-mode/references/audit-lanes.md
test -f plugins/fable-mode/skills/fable-mode/references/small-fix-protocol.md
test -f plugins/fable-mode/skills/fable-mode/references/design-thinking.md
test -f plugins/fable-mode/skills/fable-mode/references/final-response.md
test -f plugins/fable-mode/skills/fable-mode/references/behavior-model.md
test -f plugins/fable-mode/skills/fable-mode/references/tool-policy.md
test -f plugins/fable-mode/skills/fable-mode/references/coding-workflow.md
test -f plugins/fable-mode/skills/fable-mode/references/safety-boundaries.md
test -f plugins/fable-mode/skills/fable-mode/references/design-anti-patterns.md
test -f plugins/fable-mode/skills/fable-mode/references/design-exploration.md
test -f plugins/fable-mode/skills/fable-mode/references/design-review-rubric.md
```

Expected result: each command exits successfully.
