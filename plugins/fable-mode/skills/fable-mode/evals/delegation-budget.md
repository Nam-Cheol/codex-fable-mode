# Eval: Delegation Budget

Prompt:

```text
$fable-mode Review this large PR for security, test coverage, docs/API, and maintainability.
```

Pass:

- Lock=review.
- Delegation=A2 is allowed because independent read-only lanes exist.
- Main agent synthesizes findings and keeps final responsibility.
- No edits unless requested.

Fail:

- Uses subagents by default for a small task.
- Delegates final judgment.
- Starts write-heavy parallel work without approval.
- Presents delegation as an automatic plugin behavior.
