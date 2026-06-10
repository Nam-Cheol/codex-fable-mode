![Codex Fable Mode hero](./Codex-Fable-Mode_hero.png)

[한국어 README](./README.md)

`fable-mode` is a documentation-only Codex plugin that helps Codex work more deliberately: frame the task, inspect context, plan risky changes, use tools carefully, verify results, and report clearly.

This plugin is unofficial, original, and not tied to any provider. It is not affiliated with Anthropic or OpenAI. It does not reproduce or impersonate any company, model, product, private mode, or source document, and it does not include or reproduce any proprietary system prompt.

## Install With Commands

You do not need to download this repository. Open a command window and run the commands below one line at a time.

- Mac: open the `Terminal` app.
- Windows: open `CMD`, `Command Prompt`, or `PowerShell`.

Use the default method first. If it works, you do not need to run the HTTPS method.

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

Explicit invocation:

```text
$fable-mode Review this change and focus on regression risk.
```

Implementation:

```text
$fable-mode Diagnose this bug, fix it, and verify it with relevant tests.
```

Planning:

```text
$fable-mode Before implementing this feature, inspect the structure and identify risky areas.
```

Codex may also use this skill implicitly for planning, code review, architecture, debugging, or careful implementation tasks.

## What It Encourages

`fable-mode` guides Codex to:

- Inspect relevant files and state before editing.
- Make a short plan before risky or broad changes.
- State important assumptions and verify them when possible.
- Use tools narrowly and share progress during longer work.
- Run relevant tests, lint, builds, or manual checks.
- Keep hidden reasoning private while sharing concise evidence and rationale.
- End with a short report covering changes, validation, risks, and assumptions.

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

This is a documentation-only guidance plugin. It does not add tools, hooks, scripts, MCP servers, app integrations, dependencies, telemetry, or network behavior. It does not bypass Codex policy, user environment policy, repository instructions, or tool permissions.

## Repository Layout

```text
.agents/plugins/marketplace.json
plugins/fable-mode/.codex-plugin/plugin.json
plugins/fable-mode/skills/fable-mode/SKILL.md
plugins/fable-mode/skills/fable-mode/references/behavior-model.md
plugins/fable-mode/skills/fable-mode/references/tool-policy.md
plugins/fable-mode/skills/fable-mode/references/coding-workflow.md
plugins/fable-mode/skills/fable-mode/references/safety-boundaries.md
README.md
README.en.md
Codex-Fable-Mode_hero.png
LICENSE
```
