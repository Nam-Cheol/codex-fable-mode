# Validation

This plugin is documentation-only. It should stay installable as a Codex plugin without adding hooks, MCP servers, app integrations, scripts, dependencies, telemetry, postinstall commands, or runtime automation.

Run the checks below from the repository root.

## Manifest JSON

```bash
python3 -m json.tool .agents/plugins/marketplace.json >/dev/null
python3 -m json.tool plugins/fable-mode/.codex-plugin/plugin.json >/dev/null
```

Expected result: both commands exit successfully and print no output.

## Starter Prompt Limits

```bash
python3 - <<'PY'
import json

p = "plugins/fable-mode/.codex-plugin/plugin.json"
with open(p, encoding="utf-8") as f:
    data = json.load(f)

prompts = data["interface"].get("defaultPrompt", [])
assert len(prompts) <= 3, "defaultPrompt must contain at most 3 entries"
for i, prompt in enumerate(prompts, 1):
    assert len(prompt) <= 128, f"defaultPrompt #{i} is over 128 chars"
print("defaultPrompt-ok")
PY
```

Expected result: the command prints `defaultPrompt-ok`.

## Metadata Alignment

```bash
python3 - <<'PY'
import json

p = "plugins/fable-mode/.codex-plugin/plugin.json"
with open(p, encoding="utf-8") as f:
    data = json.load(f)

keywords = set(data.get("keywords", []))
for keyword in ["output-lock", "procedure-budget", "tool-budget"]:
    assert keyword in keywords, f"missing keyword: {keyword}"

assert data["interface"].get("defaultPrompt") == [
    "Use $fable-mode to lock output type before planning.",
    "Use $fable-mode to fix this without over-scoping.",
    "Use $fable-mode to cap tools and verify only the touched surface.",
]
print("metadata-alignment-ok")
PY
```

Expected result: the command prints `metadata-alignment-ok`.

## Skill Frontmatter

```bash
python3 - <<'PY'
p = "plugins/fable-mode/skills/fable-mode/SKILL.md"
with open(p, encoding="utf-8") as f:
    text = f.read()

assert text.startswith("---\n"), "SKILL.md must start with YAML frontmatter"
end = text.find("\n---", 4)
assert end != -1, "SKILL.md frontmatter must be closed"
frontmatter = text[4:end]
assert "\nname: fable-mode\n" in "\n" + frontmatter + "\n", "frontmatter name is missing"
assert "\ndescription: " in "\n" + frontmatter + "\n", "frontmatter description is missing"
print("skill-frontmatter-ok")
PY
```

Expected result: the command prints `skill-frontmatter-ok`.

## Skill Invocation Policy

```bash
test -f plugins/fable-mode/skills/fable-mode/agents/openai.yaml
rg -n "allow_implicit_invocation: false" plugins/fable-mode/skills/fable-mode/agents/openai.yaml
```

Expected result: the metadata file exists and the policy line is printed.

## Required Skill Files

```bash
test -f plugins/fable-mode/skills/fable-mode/SKILL.md
test -f plugins/fable-mode/skills/fable-mode/agents/openai.yaml
test -f plugins/fable-mode/skills/fable-mode/references/output-lock.md
test -f plugins/fable-mode/skills/fable-mode/references/depth-gate.md
test -f plugins/fable-mode/skills/fable-mode/references/procedure-budget.md
test -f plugins/fable-mode/skills/fable-mode/references/constraint-integrity.md
test -f plugins/fable-mode/skills/fable-mode/references/ask-or-act.md
test -f plugins/fable-mode/skills/fable-mode/references/output-form-integrity.md
test -f plugins/fable-mode/skills/fable-mode/references/grounding-integrity.md
test -f plugins/fable-mode/skills/fable-mode/references/capability-fit.md
test -f plugins/fable-mode/skills/fable-mode/references/tool-budget.md
test -f plugins/fable-mode/skills/fable-mode/references/audience-intent.md
test -f plugins/fable-mode/skills/fable-mode/references/output-archetype.md
test -f plugins/fable-mode/skills/fable-mode/references/pre-final-critique.md
test -f plugins/fable-mode/skills/fable-mode/references/substrate-selection.md
test -f TEST_PROMPTS.md
```

Expected result: each command exits successfully.

## Exactly One User-Facing Skill

```bash
find plugins/fable-mode/skills -mindepth 1 -maxdepth 1 -type d | sort
```

Expected result: only `plugins/fable-mode/skills/fable-mode` is printed.

## Domain-Neutral Core Routing

```bash
test ! -f plugins/fable-mode/skills/fable-mode/references/audience-kids.md
test ! -f plugins/fable-mode/skills/fable-mode/references/immersive-stage.md
! rg -n "audience-kids|immersive-stage|solar system|dinosaur|animal learning|NASA" plugins/fable-mode/skills/fable-mode README.md README.en.md
```

Expected result: the deleted files do not exist, and no domain-specific evaluation example appears in core skill or README files.

## No Runtime Extensions

```bash
find plugins/fable-mode -name hooks -o -name ".mcp.json" -o -name ".app.json" -o -name scripts
```

Expected result: no output.

## Optional Full File Check

```bash
test -f plugins/fable-mode/skills/fable-mode/references/intent-framing.md
test -f plugins/fable-mode/skills/fable-mode/references/output-lock.md
test -f plugins/fable-mode/skills/fable-mode/references/audit-lanes.md
test -f plugins/fable-mode/skills/fable-mode/references/small-fix-protocol.md
test -f plugins/fable-mode/skills/fable-mode/references/procedure-budget.md
test -f plugins/fable-mode/skills/fable-mode/references/constraint-integrity.md
test -f plugins/fable-mode/skills/fable-mode/references/output-form-integrity.md
test -f plugins/fable-mode/skills/fable-mode/references/grounding-integrity.md
test -f plugins/fable-mode/skills/fable-mode/references/capability-fit.md
test -f plugins/fable-mode/skills/fable-mode/references/tool-budget.md
test -f plugins/fable-mode/skills/fable-mode/references/audience-intent.md
test -f plugins/fable-mode/skills/fable-mode/references/pre-final-critique.md
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
