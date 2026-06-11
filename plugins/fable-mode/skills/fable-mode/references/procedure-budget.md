# Procedure Budget

Procedure budget caps how much process the task deserves.

The budget is an upper bound, not a checklist to spend. Use the smallest procedure that protects the output lock, constraints, grounding, and user trust.

## Budgets

### P0 - Direct

Use for answer locks and simple clarification locks.

- no plan
- no audit lanes
- no tools unless required by current facts or explicit grounding
- final response is short

### P1 - Local

Use for edit locks, small validation locks, and tightly scoped fixes.

- inspect the smallest relevant surface
- make the smallest safe change
- do not redesign the product
- verify only the touched behavior, file, or claim
- final response states cause, change, and check

### P2 - Bounded

Use for implementation locks with clear scope.

- short plan when it helps execution
- scoped implementation
- relevant tests, build, lint, smoke check, or manual check
- no unrelated refactor
- final response summarizes changed files and checks

### P3 - Structured

Use for review, audit, research, design artifact, architecture, and ambiguous product work.

- identify decision criteria or evidence needs
- use only relevant audit lanes
- compare trade-offs when they materially affect the output
- expose conclusions, not full internal notes
- final response is organized but still concise

### P4 - High-risk

Use only when the task is destructive, hard to reverse, security-sensitive, legally/financially/medically sensitive, or too underspecified to act safely.

- ask before irreversible action
- stage the work
- verify more strongly
- state risks and blocked decisions
- final response separates confirmed work from unconfirmed assumptions

## Budget rules

- Do not let answer tasks become implementation tasks.
- Do not let small fixes become redesigns.
- Do not turn review into rewrite unless the user asks for fixes.
- Do not expose full audit notes by default.
- Do not verify everything; verify the touched surface.
- Do not create process artifacts unless they help the locked output.
- Decrease the budget when the task becomes clearer and smaller.
- Increase the budget only when risk, ambiguity, reversibility, or grounding requires it.

## Planning budget

- P0: no plan
- P1: no plan unless the edit has multiple small steps
- P2: short plan
- P3: short structured approach or criteria
- P4: staged plan after confirmation

## Question budget

- P0: no question unless impossible to answer
- P1: no question unless blocked
- P2: at most one focused question, or proceed with a stated assumption
- P3: one to three focused questions when the answers change the result
- P4: ask before acting

## Verification budget

Match verification to the surface touched:

- prose answer: no verification unless facts are current, disputed, or source-dependent
- docs edit: read the changed docs and check links/required references when relevant
- code edit: run the narrowest meaningful test, type check, build, smoke check, or manual reproduction
- review: verify findings against changed lines
- research: verify sources and dates when recency matters
- design artifact: inspect the rendered or visual surface when available

If verification is unavailable or too costly for the lock, say what was not verified instead of expanding into a broader process.
