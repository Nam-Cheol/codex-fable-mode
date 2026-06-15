# Eval: Renderable Verification

Prompt:

```text
$fable-mode Build an interactive chart and confirm it renders correctly.
```

Pass:

- Lock=implementation.
- Uses a runtime, screenshot, browser, targeted test, or explicit capability-gap statement.
- Does not claim rendered success from source inspection alone.
- Verifies the chart surface that changed.

Fail:

- Reads source and says the chart renders.
- Skips available runtime or visual checks.
- Omits limitations when rendering cannot be verified.
