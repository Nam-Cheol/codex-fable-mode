# Visible Route Contract

The visible route contract is a compact public summary of the task contract. It helps the user see how fable-mode bounded the work without exposing hidden reasoning.

It is not chain-of-thought. It is not a transcript of deliberation. It is not a plan unless the locked output needs a plan.

## When to show it

- L0 direct answer: do not show a route line.
- L1 small edit or simple task: show it only when file edits, verification, or tool use make the contract useful.
- L2 standard implementation: show it by default.
- L3 product, design, architecture, review, audit, research, or ambiguous work: show it by default.
- L4 high-risk or underspecified work: show it by default before acting, after any required confirmation.

## Format

Use one short line:

```text
Fable route: Lock=implementation · Layer=L2 · Procedure=P2 · Tool=T2 · Grounding=repo+tests · Delegation=A0
```

Allowed fields:

- Lock: answer, edit, implementation, review, audit, design artifact, research, clarification, or validation
- Layer: L0, L1, L2, L3, or L4
- Procedure: P0, P1, P2, P3, or P4
- Tool: T0, T1, T2, T3, or T4
- Grounding: short public evidence need, such as none, repo, repo+tests, sources, runtime, visual, measurement, or blocked
- Delegation: A0, A1, A2, or A3

Keep field values short. If the route changes materially, state the new route briefly.

## What not to expose

Do not expose:

- hidden reasoning
- chain-of-thought
- full hypothesis trees
- private critique notes
- discarded strategies
- subagent transcripts
- audit scratchpads

The route line says what contract is being used, not why every internal choice was made.

## Route discipline

The route line should protect the user from over-scoping:

- answer locks should not become implementation
- edit locks should not become redesign
- review locks should not become rewrite
- research locks should not become generic opinion
- validation locks should not become broad audit

If the route line would make an L0 answer heavier, omit it.
