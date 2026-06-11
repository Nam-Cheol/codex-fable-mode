# Tool Budget

Tools are for evidence, change, and verification. They are not for confidence theater.

Set the tool budget after capability fit. Use the fewest tools that can honestly satisfy the output lock and grounding needs.

## Budgets

### T0 - No tools

Use for direct answer locks when the answer is stable and already supported by context.

- answer directly
- do not inspect files just to look diligent
- do not browse stable facts unless required by policy or the user

### T1 - Context read

Use when the answer, review, edit, or validation depends on local context.

- read the smallest relevant files, diffs, logs, or docs
- prefer fast search before opening many files
- stop when the needed context is found

### T2 - Change and check

Use for edit and bounded implementation locks.

- inspect before editing
- edit the bounded surface
- run the narrowest meaningful check
- do not run unrelated suites unless the touched surface depends on them

### T3 - Runtime, visual, current, or source-backed

Use when fidelity requires a runtime, browser, screenshot, image/reference asset, database copy, external source, or current information.

- use the specific capability required by the lock
- report source, runtime, or visual limitations
- avoid substituting generic claims for missing evidence

### T4 - Privileged, destructive, expensive, or broad

Use only when the user asked for it or the task cannot be completed safely otherwise.

- request confirmation when required
- explain why the capability is necessary
- keep the action scoped

## Tool rules

- Do not use tools for confidence theater.
- Do not run broad discovery after the lock has already bounded the surface.
- Do not verify everything; verify the touched surface.
- Do not install dependencies, add runtime automation, create hooks, add MCP servers, add telemetry, or add background jobs for this plugin.
- Do not repeat a failed command without a new hypothesis.
- Batch independent reads when available, but keep outputs readable.
- Stop using tools when the evidence needed for the locked output is sufficient.

## Lock mapping

| Lock | Typical tool budget |
| --- | --- |
| answer | T0, or T3 when current/source-backed facts are required |
| edit | T1-T2 |
| implementation | T1-T2, or T3 when runtime/visual/current evidence is required |
| review | T1 |
| audit | T1-T3 depending on scope |
| design artifact | T1-T3 depending on fidelity and assets |
| research | T3 |
| clarification | T0, or T1 if a quick local check avoids asking |
| validation | T1-T3 |

## Verification stop rule

Verification is enough when it covers:

- the files, claims, behavior, or artifact actually touched
- the user-visible contract that could break
- the highest-risk nearby dependency introduced by the change

If a broader check would be useful but not required, mention it as unrun rather than spending the budget automatically.
