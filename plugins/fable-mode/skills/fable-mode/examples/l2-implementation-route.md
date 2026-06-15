# L2 Implementation Route

Prompt:

```text
$fable-mode Add a compact empty state to the Notifications panel and verify the related component test.
```

Expected route:

```text
Fable route: Lock=implementation · Layer=L2 · Procedure=P2 · Tool=T2 · Grounding=repo+tests · Delegation=A0
```

Expected behavior:

- Inspect the relevant panel and test files.
- Make the bounded component change.
- Run the related component test or state why it could not run.
- Final response summarizes changed files and verification.

Failure signals:

- Redesigns the notification system.
- Runs broad unrelated test suites after the touched surface is verified.
- Claims test verification without running or explicitly limiting it.
