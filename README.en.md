![Codex Fable Mode hero](./Codex-Fable-Mode_hero.png)

[한국어 README](./README.md)

`fable-mode` is a documentation-only Codex plugin that helps Codex choose only as much reasoning depth as the user's intent requires.

It installs one skill only. Users always invoke `$fable-mode`. The skill is not a harness, not a second runtime, and not a rigid spec generator. Simple questions should get direct answers, small fixes should use minimal inspection, bounded implementation should plan-implement-verify, and ambiguous product/design/architecture work should slow down enough to frame intent.

The core idea is an intent-aware depth gate: choose L0, L1, L2, L3, or L4 based on the task instead of forcing every request into the same heavy workflow. Design and substrate selection still matter, but they sit behind that first decision.

## What fable-mode is

fable-mode is a single Codex operating mode for intent-aware work.

It helps Codex decide how deeply to reason:

- L0 direct answer for simple questions
- L1 small-fix path for local bugs, layout issues, and copy changes
- L2 plan, implement, and verify for bounded implementation
- L3 intent framing, output archetype, substrate choice, and scoped audit lanes for product/design/architecture work
- L4 confirmation and stronger verification for risky or hard-to-reverse work

It also uses an ask-or-act rule: ask only when the missing answer would materially change the result. Otherwise, inspect, implement, verify, and report briefly.

For UI and design work, fable-mode does not assume the output is a webpage. It first classifies the output archetype, then chooses the right substrate: DOM, CSS layout, canvas, SVG, WebGL, fixed-stage, or hybrid. This helps avoid generic DOM/card implementations for tools that need a different medium, such as pixel editors, drawing tools, graph editors, and slide decks.

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
<summary>Install a fixed version: v0.1.0</summary>

Use this when you need to reinstall the exact same version later, or when a team document must pin the plugin version.

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
/goal Use $fable-mode for this task. Choose the smallest sufficient reasoning depth. For UI/design work, classify the output archetype and substrate before implementation.
```

You do not need to repeat `$fable-mode` on every follow-up while the goal remains active. Re-mention it after major topic changes, long compaction-heavy sessions, or if Codex starts ignoring the workflow.

Implementation or debugging:

```text
$fable-mode Diagnose this bug, fix it, and verify it with relevant tests.
```

UI and design:

```text
$fable-mode Redesign this dashboard around the product goal and compare three directions before implementation.
```

Codex may also use this skill implicitly for planning, code review, architecture, debugging, careful implementation, and UI/frontend design tasks.

## Depth Gate: L0-L4

`fable-mode` helps Codex avoid treating every task as a heavy project. The first decision is the smallest sufficient reasoning depth.

- L0: answer simple questions directly.
- L1: inspect the smallest relevant area for small bugs or CSS issues.
- L2: plan, implement, and verify ordinary implementation work.
- L3: classify intent and output format for product, design, or architecture work.
- L4: use confirmation and stronger verification for risky or hard-to-reverse work.

The rule of thumb is to start lower when the cost of being wrong is low, and slow down only when user intent, correctness, or reversibility needs more protection.

## Ask-or-Act and Audit Lanes

fable-mode does not ask questions just because a workflow says to ask. It asks when the answer changes the solution, such as destructive work, costly substrate choices, unclear product direction, or high-risk changes.

For review, architecture, product, and high-risk work, it uses scoped audit lanes instead of an all-purpose checklist. That means risk, verification, design quality, safety, or delivery concerns are examined only when they are relevant to the task depth.

## Design Behavior

For UI, frontend, and design work, fable-mode does not assume the output is a webpage.

It first classifies the output archetype:

- webpage
- app screen
- creative tool
- game prototype
- deck
- animation
- editor
- dashboard
- data visualization
- design exploration

Then it chooses the substrate:

- DOM
- CSS layout
- canvas
- SVG
- WebGL
- fixed-stage
- hybrid

This reduces generic card/grid implementations for tools that need a real work surface.

## Manual Validation

This repository is intentionally documentation-only, so it does not add a validation script. [VALIDATION.md](./VALIDATION.md) lists the manual checks for JSON manifests, required skill/reference files, and the absence of hooks, MCP servers, app configs, scripts, dependencies, telemetry, or runtime behavior.

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

## Repository Layout

```text
.agents/plugins/marketplace.json
plugins/fable-mode/.codex-plugin/plugin.json
plugins/fable-mode/skills/fable-mode/SKILL.md
plugins/fable-mode/skills/fable-mode/references/intent-framing.md
plugins/fable-mode/skills/fable-mode/references/depth-gate.md
plugins/fable-mode/skills/fable-mode/references/ask-or-act.md
plugins/fable-mode/skills/fable-mode/references/audit-lanes.md
plugins/fable-mode/skills/fable-mode/references/output-archetype.md
plugins/fable-mode/skills/fable-mode/references/substrate-selection.md
plugins/fable-mode/skills/fable-mode/references/small-fix-protocol.md
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
VALIDATION.md
Codex-Fable-Mode_hero.png
LICENSE
```
