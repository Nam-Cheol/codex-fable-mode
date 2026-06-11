# Ask-or-Act

Do not ask questions just because a workflow says to ask.

Ask only when the answer would materially change the solution.

## Act without asking when

- the task is a small fix
- the user gave enough constraints
- the missing detail has a safe default
- the change is reversible
- the cost of a wrong assumption is low
- the user likely expects immediate execution
- the next step is inspection rather than implementation

## Ask before acting when

- multiple valid outcomes conflict
- the implementation substrate is unclear and costly to change
- the user's request implies a large scope but gives little detail
- the work may destroy, migrate, rewrite, or remove existing behavior
- the result depends on audience, fidelity, platform, brand, or style
- guessing would create significant rework
- the user explicitly asks for options or strategy

## Question budget

- L0: 0 questions
- L1: 0 questions unless blocked
- L2: 0-1 questions
- L3: 1-3 focused questions, or proceed with explicit assumptions
- L4: ask first

Prefer:

> I'll assume X unless you want Y.

over long questionnaires.

## Anti-patterns

Avoid:

- starting every task with discovery questions
- turning a small fix into a strategy session
- forcing SDD/spec generation before the problem is understood
- asking questions whose answers would not change the implementation
