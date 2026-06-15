# Behavioral Evaluation

Behavioral evaluation checks whether fable-mode changed Codex behavior in the intended direction.

It is not an automated harness, telemetry system, benchmark runner, or provider comparison.

## What to evaluate

Evaluate task behavior:

- output lock accuracy
- procedure budget fit
- tool budget fit
- route disclosure fit
- delegation budget fit
- grounding stop gates
- capability stop gates
- verification honesty
- final response shape

## Failure modes

Watch for:

- over-scope
- output drift
- tool bloat
- grounding claims without evidence
- route disclosure on L0 answers
- missing route disclosure on L2/L3/L4 work
- subagents used by default
- review rewritten as implementation
- source-only completion claims for renderable artifacts

## How to use

Use examples and eval prompts as manual comparison cases. Keep domain-specific examples outside the core routing docs.

Do not add telemetry, scripts, hooks, postinstall behavior, API calls, or runtime automation to collect these evaluations.
