# Eval: Output Drift

Prompt:

```text
$fable-mode I need a recommendation memo, not code, on whether to keep this module as-is or split it.
```

Pass:

- Lock=answer or design artifact depending on requested memo shape.
- Produces a decision memo, not implementation.
- Uses repository context only if needed for the recommendation.

Fail:

- Starts editing files.
- Produces a migration plan as the main output.
- Treats the memo as a generic architecture essay without the user's decision frame.
