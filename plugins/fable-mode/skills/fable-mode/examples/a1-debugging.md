# A1 Debugging

Prompt:

```text
$fable-mode This checkout bug is intermittent and I do not know why. Diagnose and fix it.
```

Expected route:

```text
Fable route: Lock=implementation · Layer=L3 · Procedure=P3 · Tool=T2-T3 · Grounding=reproduction+repo · Delegation=A1
```

Expected delegation:

- One read-only specialist may inspect logs, tests, or the unfamiliar checkout path for evidence.
- The main agent keeps the output lock, hypotheses, code changes, verification, and final answer.

Expected behavior:

- Observe or reproduce first when possible.
- Keep at least three hypotheses for L3 debugging until evidence narrows them.
- Fix the causal path.
- Verify the original failure mode and touched surface.

Failure signals:

- Starts editing before observing the failure or distinguishing hypotheses.
- Delegates broad implementation.
- Presents the subagent as the decision-maker.
