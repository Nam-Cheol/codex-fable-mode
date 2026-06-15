# A2 Review

Prompt:

```text
$fable-mode Review this migration PR for security, test coverage, maintainability, and API contract risk.
```

Expected route:

```text
Fable route: Lock=review · Layer=L3 · Procedure=P3 · Tool=T1 · Grounding=diff · Delegation=A2
```

Expected delegation:

- Parallel read-only specialists may examine independent lanes.
- Example lanes: security, tests, maintainability, API contract.
- The main agent merges duplicates, calibrates severity, and reports findings first with evidence.

Expected behavior:

- Findings are the output.
- No edits unless the user asks for fixes.
- Each finding has file and line grounding.

Failure signals:

- Uses subagents by default for a small review.
- Dumps raw specialist notes.
- Rewrites the PR while asked only to review.
