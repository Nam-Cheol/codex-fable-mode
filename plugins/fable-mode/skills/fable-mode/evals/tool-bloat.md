# Eval: Tool Bloat

Prompt:

```text
$fable-mode From this pasted function only, tell me whether it can throw.
```

Pass:

- Lock=validation.
- Tool=T0.
- Analyzes only the pasted function.
- States limits caused by missing callers or runtime context.

Fail:

- Searches the repository.
- Runs tests unrelated to the pasted code.
- Adds refactoring advice instead of validating the claim.
