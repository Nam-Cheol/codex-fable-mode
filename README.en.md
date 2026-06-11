![Codex Fable Mode hero](./Codex-Fable-Mode_hero.png)

# Codex Fable Mode

[![Documentation-only plugin](https://img.shields.io/badge/type-documentation--only-2f6f5f)](#limitations)
[![Codex plugin](https://img.shields.io/badge/Codex-plugin-111827)](#install-with-commands)
[![Version v0.2.0](https://img.shields.io/badge/version-v0.2.0-6b7280)](#version-policy)
[![Provider-neutral](https://img.shields.io/badge/guidance-provider--neutral-4b5563)](#limitations)

[한국어 README](./README.md)

`fable-mode` is a documentation-only Codex plugin that helps Codex choose only as much reasoning depth as the user's intent requires.

It installs one skill only. Users always invoke `$fable-mode`. The skill is not a harness, not a second runtime, and not a rigid spec generator. Simple questions should get direct answers, small fixes should use minimal inspection, bounded implementation should plan-implement-verify, and ambiguous product/design/architecture work should slow down enough to frame intent.

The core idea is an intent-aware depth gate: choose L0, L1, L2, L3, or L4 based on the task instead of forcing every request into the same heavy workflow. Design and substrate selection still matter, but they sit behind that first decision.

Starting in v0.2.0, fable-mode strengthens task-behavior monitoring rather than specializing in one topic or visual style. It is not a kids, design, or space-specific mode. It checks whether explicit constraints were honored, whether the output form was misread, whether required evidence and tools were used, whether insufficiency was disclosed honestly, whether the reasoning depth fit the task, and whether the final result matches the user's intent.

[Install with commands](#install-with-commands) · [Install with Codex Desktop](#install-with-codex-desktop) · [Usage](#usage) · [Validation](#manual-validation)

## At a Glance

| When you need | How fable-mode helps |
| --- | --- |
| A direct answer | Answer directly without inventing a plan. |
| A small fix | Inspect the smallest relevant area and patch it. |
| Bounded implementation | Plan briefly, implement, and verify the result. |
| Product, design, or architecture work | Classify intent, output shape, grounding, and substrate first. |
| Ambiguous output form | Separate implementation tools from the actual artifact. |
| Grounded work | Check whether files, assets, measurements, current facts, or references are needed. |
| Risky changes | Ask for confirmation and verify more strongly. |

## Workflow

```mermaid
flowchart LR
    A["User request"] --> B["Intent framing"]
    B --> C{"Depth gate"}
    C --> D["Constraint integrity"]
    D --> E["Ask or act"]
    E --> F["Output form"]
    F --> G["Grounding"]
    G --> H["Capability fit"]
    H --> I["Audience intent"]
    I --> J["Audit or substrate when needed"]
    J --> K["Pre-final critique"]
    K --> L["Brief report"]
```

## What fable-mode is

fable-mode is a single Codex operating mode for intent-aware work.

It helps Codex decide how deeply to reason:

- L0 direct answer for simple questions
- L1 small-fix path for local bugs, layout issues, and copy changes
- L2 plan, implement, and verify for bounded implementation
- L3 intent framing, output archetype, substrate choice, and scoped audit lanes for product/design/architecture work
- L4 confirmation and stronger verification for risky or hard-to-reverse work
- constraint integrity for explicit user requirements
- output-form integrity so familiar implementation tools do not override the requested medium
- grounding integrity for facts, files, assets, measurements, brand systems, and reproductions
- capability fit so unavailable tools or evidence are disclosed instead of faked
- audience intent so the response shape matches the user's target audience when specified

It also uses an ask-or-act rule: ask only when the missing answer would materially change the result. Otherwise, inspect, implement, verify, and report briefly.

For UI and design work, fable-mode does not assume the output is a webpage. It first checks output form, grounding, and capability fit, then chooses the right substrate: DOM, CSS layout, canvas, SVG, WebGL, fixed-frame, asset-grounded media, or hybrid. This helps avoid generic DOM/card implementations for tools that need a different medium.

This plugin is unofficial, original, and not tied to any provider. It is not affiliated with Anthropic or OpenAI. It does not reproduce or impersonate any company, model, product, private mode, or source document, and it does not include or reproduce any proprietary system prompt. The UI/design guidance is provider-neutral documentation and does not copy or include any source prompt.

## Install With Commands

You do not need to download this repository. Open a command window and run the commands below one line at a time.

- Mac: open the `Terminal` app.
- Windows: open `CMD`, `Command Prompt`, or `PowerShell`.

Use the default method first. It follows `main`, so marketplace upgrades can pull the currently recommended documentation. If it works, you do not need to run the HTTPS method.

Lines that start with `#` are comments, so they are safe to copy too.

```bash
# 1. Paste this line, then press Enter.
codex plugin marketplace add Nam-Cheol/codex-fable-mode --ref main

# 2. When the first command finishes, paste this line and press Enter.
codex plugin add fable-mode@codex-fable-mode
```

<details>
<summary>Only if the default method fails: install with the HTTPS URL</summary>

Use this only if the command above cannot find the repository. You do not need to run both the default method and the HTTPS method.

```bash
# 1. Paste this line, then press Enter.
codex plugin marketplace add https://github.com/Nam-Cheol/codex-fable-mode.git --ref main

# 2. When the first command finishes, paste this line and press Enter.
codex plugin add fable-mode@codex-fable-mode
```

</details>

<details>
<summary>Example fixed tagged version: v0.1.0</summary>

Use this when you need to reinstall the exact same version later, or when a team document must pin the plugin version. The example below uses an already tagged version.

```bash
# 1. Paste this line, then press Enter.
codex plugin marketplace add Nam-Cheol/codex-fable-mode --ref v0.1.0

# 2. When the first command finishes, paste this line and press Enter.
codex plugin add fable-mode@codex-fable-mode
```

</details>

Check the installation one line at a time:

```bash
# 1. Check registered marketplaces.
codex plugin marketplace list

# 2. Check that fable-mode appears in the list.
codex plugin list --marketplace codex-fable-mode
```

Installation is complete when `fable-mode@codex-fable-mode` appears as `installed, enabled`.

### If Command Installation Fails

Some Codex versions or environments may handle plugin installation through the plugin screen instead. If the command path fails, open Codex and use `/plugins`.

1. Open `/plugins` in Codex.
2. Select the `codex-fable-mode` marketplace if it appears.
3. Find `Fable Mode` or `fable-mode`.
4. Click `Install plugin`.

## Install With Codex Desktop

If you mainly use Codex Desktop, install the plugin from a command window first, then restart Codex Desktop. Once installed, it is available across Codex conversations.

1. On Mac, open `Terminal`. On Windows, open `CMD`, `Command Prompt`, or `PowerShell`.
2. Run the commands below one line at a time:

```bash
# 1. Paste this line, then press Enter.
codex plugin marketplace add Nam-Cheol/codex-fable-mode --ref main

# 2. When the first command finishes, paste this line and press Enter.
codex plugin add fable-mode@codex-fable-mode
```

3. Fully quit and reopen Codex Desktop.
4. Open a new conversation and search the skill selection menu for `Fable Mode` or `fable-mode`.
5. Select it from the menu or type `$fable-mode` directly.

If your Codex Desktop version includes a plugin or marketplace UI, you can add `Nam-Cheol/codex-fable-mode` as a marketplace source and then install `Fable Mode` from there.

If command installation fails, open `/plugins` in Codex Desktop, choose `codex-fable-mode`, then click `Install plugin`.

## Usage

For one-off tasks:

```text
$fable-mode
Fix the text overflow in this component.
```

For longer tasks:

```text
/goal Use $fable-mode for this task. Choose the smallest sufficient reasoning depth. Check constraints, output form, grounding, capability fit, audience intent, and pre-final critique.
```

You do not need to repeat `$fable-mode` on every follow-up while the goal remains active. Re-mention it after major topic changes, long compaction-heavy sessions, or if Codex starts ignoring the workflow.

Implementation or debugging:

```text
$fable-mode Diagnose this bug, fix it, and verify it with relevant tests.
```

UI and design:

```text
$fable-mode Redesign this screen around the product goal and brand constraints. Check output form and grounding before implementation.
```

Output-form sensitive work:

```text
$fable-mode This should be an interactive simulator, not a webpage. Even if you use HTML, choose the medium before building it like a dashboard.
```

Codex may also use this skill implicitly for planning, code review, architecture, debugging, careful implementation, and UI/frontend design tasks.

Domain-specific prompts live in [TEST_PROMPTS.md](./TEST_PROMPTS.md) as evaluation examples only. They are not built-in bias or core routing logic.

## Depth Gate: L0-L4

`fable-mode` helps Codex avoid treating every task as a heavy project. The first decision is the smallest sufficient reasoning depth.

- L0: answer simple questions directly.
- L1: inspect the smallest relevant area for small bugs or CSS issues.
- L2: plan, implement, and verify ordinary implementation work.
- L3: classify intent and output format for product, design, or architecture work.
- L4: use confirmation and stronger verification for risky or hard-to-reverse work.

The rule of thumb is to start lower when the cost of being wrong is low, and slow down only when user intent, correctness, or reversibility needs more protection.

Task-behavior monitoring adds a second layer:

- Constraint integrity: extract and verify explicit user requirements as contracts.
- Output form integrity: separate implementation tools from the requested artifact.
- Grounding integrity: check whether factual, visual, codebase, brand, performance, or reproduction evidence is required.
- Capability fit: determine whether the current environment can honestly satisfy the needed evidence and verification.
- Audience intent: adapt depth, language, evidence, and interaction density when the user names an audience.
- Pre-final critique: re-check constraints, form, grounding, capability, scope, depth, and intent fit before reporting.

## Ask-or-Act and Audit Lanes

fable-mode does not ask questions just because a workflow says to ask. It asks when the answer changes the solution, such as destructive work, costly substrate choices, unclear product direction, or high-risk changes.

For review, architecture, product, and high-risk work, it uses scoped audit lanes instead of an all-purpose checklist. That means risk, verification, design quality, safety, or delivery concerns are examined only when they are relevant to the task depth.

## Output Form and Medium

fable-mode does not assume the output is a webpage.

It first classifies the output form:

- direct answer
- document
- code patch
- review
- webpage
- app screen
- creative tool
- game prototype
- deck
- animation
- editor
- dashboard
- data visualization
- simulation
- fixed-frame experience
- spatial or scene-based experience
- design exploration

Then it chooses the substrate:

- DOM
- CSS layout
- canvas
- SVG
- WebGL
- fixed-frame
- asset-grounded media
- hybrid

This reduces generic card/grid implementations for tools that need a real work surface.

## Grounding and Capability Behavior

When the user asks for actual files, current facts, reproducible bugs, measurements, brand constraints, design systems, visual assets, or exact evidence, fable-mode guides Codex not to silently replace that with a plausible approximation.

If the needed capability is available, use it. If the current environment cannot provide the needed evidence or tool, say so. Separate what was verified, what was inferred, what is blocked, and what would be needed for a higher-fidelity result.

## Manual Validation

This repository is intentionally documentation-only, so it does not add a validation script. [VALIDATION.md](./VALIDATION.md) lists the manual checks for JSON manifests, required skill/reference files, and the absence of hooks, MCP servers, app configs, scripts, dependencies, telemetry, or runtime behavior.

## Version Policy

The default install uses `--ref main`. This plugin is not runtime code; it is the currently recommended reasoning workflow documentation, so most users should receive the latest guidance when they upgrade.

For team docs or reproducible installs, pin a tag such as `--ref v0.1.x`. Small wording edits may keep the same `plugin.json.version`, but changes to the default behavior philosophy, reference structure, install flow, or UI metadata should bump the patch or minor version.

## Update

When a new version is available, run each command on its own line:

```bash
# 1. Refresh the installation information.
codex plugin marketplace upgrade codex-fable-mode

# 2. Remove the current fable-mode install.
codex plugin remove fable-mode@codex-fable-mode

# 3. Install the new version.
codex plugin add fable-mode@codex-fable-mode
```

Restart Codex Desktop after updating if you use the Desktop app.

## Uninstall

Remove the plugin:

```bash
# Remove only the fable-mode plugin.
codex plugin remove fable-mode@codex-fable-mode
```

Remove the marketplace too:

```bash
# Remove the fable-mode marketplace registration too.
codex plugin marketplace remove codex-fable-mode
```

## Limitations

This is a documentation-only guidance plugin. It does not add tools, hooks, scripts, MCP servers, app integrations, dependencies, postinstall commands, API-calling examples, telemetry, or network behavior. It does not bypass Codex policy, user environment policy, repository instructions, or tool permissions.

fable-mode can guide better decisions, but it cannot invent unavailable runtime tools. If required file access, measurement, browsing, image generation, asset collection, external integrations, or automation tools are unavailable or blocked, it must say so and separate possible work from blocked work.

## Repository Layout

```text
.agents/plugins/marketplace.json
plugins/fable-mode/.codex-plugin/plugin.json
plugins/fable-mode/skills/fable-mode/SKILL.md
plugins/fable-mode/skills/fable-mode/references/intent-framing.md
plugins/fable-mode/skills/fable-mode/references/depth-gate.md
plugins/fable-mode/skills/fable-mode/references/constraint-integrity.md
plugins/fable-mode/skills/fable-mode/references/ask-or-act.md
plugins/fable-mode/skills/fable-mode/references/output-form-integrity.md
plugins/fable-mode/skills/fable-mode/references/grounding-integrity.md
plugins/fable-mode/skills/fable-mode/references/capability-fit.md
plugins/fable-mode/skills/fable-mode/references/audience-intent.md
plugins/fable-mode/skills/fable-mode/references/audit-lanes.md
plugins/fable-mode/skills/fable-mode/references/output-archetype.md
plugins/fable-mode/skills/fable-mode/references/substrate-selection.md
plugins/fable-mode/skills/fable-mode/references/small-fix-protocol.md
plugins/fable-mode/skills/fable-mode/references/pre-final-critique.md
plugins/fable-mode/skills/fable-mode/references/design-thinking.md
plugins/fable-mode/skills/fable-mode/references/final-response.md
plugins/fable-mode/skills/fable-mode/references/behavior-model.md
plugins/fable-mode/skills/fable-mode/references/tool-policy.md
plugins/fable-mode/skills/fable-mode/references/coding-workflow.md
plugins/fable-mode/skills/fable-mode/references/safety-boundaries.md
plugins/fable-mode/skills/fable-mode/references/design-anti-patterns.md
plugins/fable-mode/skills/fable-mode/references/design-exploration.md
plugins/fable-mode/skills/fable-mode/references/design-review-rubric.md
README.md
README.en.md
TEST_PROMPTS.md
VALIDATION.md
Codex-Fable-Mode_hero.png
LICENSE
```
