---
name: fable-mode
description: Use when the user explicitly invokes $fable-mode or asks for fable-mode style routing. Keep ordinary simple tasks outside this skill; it is for intent, output-form, grounding, capability, and depth control.
---

# fable-mode

fable-mode is a single operating mode for intent-aware work.

It is not a harness.
It is not a rigid spec generator.
It is not a design-only mode.
It is not "think as much as possible."

The purpose of fable-mode is to choose the smallest sufficient reasoning depth and procedure that protects user intent, explicit constraints, grounding, capability fit, output form, correctness, and output quality.

fable-mode is domain-neutral. It must not push work toward one subject, audience, visual style, or artifact type. HTML, CSS, JavaScript, canvas, SVG, images, documents, tests, terminal commands, and prose are implementation tools. The desired output form comes from the user's intent.

fable-mode is not a Fable 5 clone, model bridge, provider bridge, runtime harness, automation framework, or goal engine. It does not unlock, emulate, proxy, or route to another provider. It is documentation-only guidance for Codex behavior.

## Core loop

Before planning, using tools, or acting:

1. Frame the user's intent.
2. Lock the primary output type.
3. Choose a depth level.
4. Set a procedure budget.
5. Extract explicit constraints.
6. Decide whether to ask or act.
7. Classify the requested output form.
8. Identify grounding requirements.
9. Check capability fit.
10. Set a tool budget.
11. Set a delegation budget.
12. Decide whether to expose a compact route line.
13. Infer audience intent when the user gives one.
14. Use audit lanes only when required.
15. Implement or answer.
16. Run a compact pre-final critique.
17. Report only what matters.

This is a routing loop, not a requirement to read every reference file.

The output lock must be one of: answer, edit, implementation, review, audit, design artifact, research, clarification, or validation. It determines reasoning depth, which reference docs to read, whether to ask or act, whether tools are allowed, how much verification is enough, and final response length.

Grounding and capability checks are stop gates when they protect a hard requirement. If a required source, asset, measurement, reproduction, runtime, browser, current lookup, or other capability is unavailable, do not enter implementation by substituting a plausible approximation. Stop, inspect with an available tool, ask for the missing material, or change the output to a clearly limited answer or plan.

## Visible route contract

For L2, L3, and L4 work, expose a compact route line near the start. This is a public work contract, not hidden reasoning or chain-of-thought.

Example:

```text
Fable route: Lock=implementation · Layer=L2 · Procedure=P2 · Tool=T2 · Grounding=repo+tests · Delegation=A0
```

Do not expose a route line for L0 direct answers. For L1 small edits, expose it only when file edits, verification, or tool use make the contract useful.

The route line may include:

- Lock
- Layer
- Procedure
- Tool
- Grounding
- Delegation

Do not include private deliberation, discarded hypotheses, hidden audit notes, or step-by-step reasoning in the route line.

## Delegation budget

Delegation is optional evidence-gathering, not the default behavior.

The main agent always owns the output lock, user intent, write coordination, final synthesis, and final responsibility.

- A0: no delegation. Default.
- A1: one read-only specialist for unfamiliar codebase exploration, unknown-cause debugging, API/docs confirmation, or review support.
- A2: parallel read-only specialists when independent audit lanes exist, such as security, tests, maintainability, docs/API, or UI/UX.
- A3: controlled worker split for large migrations or multi-module work. Use only when the user explicitly requests or approves it. The parent keeps write coordination and final responsibility.

Subagents are for context isolation, evidence separation, and parallel audit. They should receive one narrow question and return distilled evidence. Avoid write-heavy parallel work. Do not imply that this plugin automatically runs subagents; this is a documentation budget only.

## Routing order

Use this order for substantial work:

1. Intent framing
2. Output lock
3. Depth gate
4. Procedure budget
5. Constraint integrity
6. Ask-or-act
7. Output form integrity
8. Grounding integrity
9. Capability fit
10. Tool budget
11. Delegation budget
12. Visible route contract
13. Audience intent
14. Audit lanes only when required
15. Implementation or answer
16. Pre-final critique
17. Final response

## Reference order

Before planning or tool use, apply the minimal entry set:

- [intent-framing.md](references/intent-framing.md)
- [output-lock.md](references/output-lock.md)
- [depth-gate.md](references/depth-gate.md)

Then load only the monitor files triggered by the locked output, explicit constraints, grounding needs, capability needs, risk, or requested artifact:

- [procedure-budget.md](references/procedure-budget.md): when the task could sprawl, has multiple steps, or needs verification.
- [constraint-integrity.md](references/constraint-integrity.md): when the user gives explicit scope, wording, file, safety, or fidelity constraints.
- [ask-or-act.md](references/ask-or-act.md): when missing information might change the result.
- [output-form-integrity.md](references/output-form-integrity.md): when the requested artifact could be confused with a familiar implementation tool.
- [grounding-integrity.md](references/grounding-integrity.md): when the answer or artifact depends on sources, assets, measurements, current facts, reproduction, brand, design-system, codebase, or other evidence.
- [capability-fit.md](references/capability-fit.md): when correctness or fidelity depends on a tool, permission, runtime, browser, external source, image, dataset, or other capability.
- [tool-budget.md](references/tool-budget.md): when tools are being used or considered.
- [delegation-budget.md](references/delegation-budget.md): when subagents are being considered or the work has independent evidence lanes.
- [visible-route-contract.md](references/visible-route-contract.md): when route disclosure is required or useful.
- [audience-intent.md](references/audience-intent.md): when the user names an audience, reading level, domain, or delivery context.

The output lock and depth gate decide which later reference docs to read. Do not read every reference file by default.

Monitor files are not a second checklist. They are small, conditional guardrails. Grounding and capability monitors become hard stops when their missing evidence or missing tool would make implementation dishonest.

For ambiguous, product, architecture, design, or high-risk work, also read:

- [audit-lanes.md](references/audit-lanes.md)

For UI, frontend, design, prototype, game, animation, editor, dashboard, deck, canvas, SVG, or HTML/CSS/JS artifact work, also read:

- [output-archetype.md](references/output-archetype.md)
- [substrate-selection.md](references/substrate-selection.md)
- [design-thinking.md](references/design-thinking.md)

For localized CSS, JS, layout, interaction, or bug fixes, prefer:

- [small-fix-protocol.md](references/small-fix-protocol.md)

For unknown-cause debugging, behavioral regressions, performance mysteries, or failures where the cause is not already known, also read:

- [investigation-protocol.md](references/investigation-protocol.md)

For UI, games, simulations, charts, SVG/canvas/WebGL, executable artifacts, or any work where runtime/rendered behavior is the deliverable, also read:

- [verification-gate.md](references/verification-gate.md)

Before finishing substantial work, apply a compact critique and final-shape check. Read these files only when the task is large enough that the extra guardrail helps:

- [pre-final-critique.md](references/pre-final-critique.md)
- [final-response.md](references/final-response.md)

For long L3/L4 tasks, user-visible handoffs, or resumed work where the task contract may drift, use:

- [run-card.md](references/run-card.md)
- [behavioral-evaluation.md](references/behavioral-evaluation.md)

Existing supporting references may be used after the routing layer when relevant:

- [behavior-model.md](references/behavior-model.md)
- [tool-policy.md](references/tool-policy.md)
- [coding-workflow.md](references/coding-workflow.md)
- [safety-boundaries.md](references/safety-boundaries.md)
- [design-anti-patterns.md](references/design-anti-patterns.md)
- [design-exploration.md](references/design-exploration.md)
- [design-review-rubric.md](references/design-review-rubric.md)

## Mode behavior

### Simple questions

Output lock: answer. Answer directly. Do not create a plan, spec, audit, file, or implementation.

### Small fixes

Output lock: edit. Inspect the smallest relevant source area. Fix the cause. Avoid redesigning the product. Verify the specific touched behavior.

### Standard implementation

Output lock: implementation. Use a short plan, implement the bounded change, run relevant checks, and summarize changes.

### Reviews and audits

Output lock: review or audit. Findings are the output unless the user asks for fixes. Do not rewrite the patch or expose full audit notes by default.

### Research and validation

Output lock: research or validation. Use only the tools and sources needed for the claim, date, file, behavior, or artifact being checked. Separate verified evidence from inference.

### Product, design, or architecture work

Do not jump straight to the most familiar output format. Classify the user's intent, requested output form, scope, grounding requirements, capability fit, and trade-offs. Ask only if the missing answer materially changes the result.

### Output-form sensitive work

Do not confuse an implementation tool with the user's desired output. A design request is not automatically a website. A simulation is not automatically a dashboard. A small bug is not automatically a redesign. A brainstorming request is not automatically an implementation task.

### High-risk or underspecified work

Slow down. Use audit lanes. Ask before destructive or expensive changes.

### Unknown-cause debugging

Observe or reproduce before fixing. Keep at least two plausible hypotheses active, or at least three for L3/L4 debugging. Gather evidence that distinguishes hypotheses before changing code. Fix the causal path, then verify the original failure mode and the touched surface.

### Renderable or executable artifacts

Do not claim UI, game, simulation, chart, SVG, canvas, WebGL, or executable behavior is complete from source inspection alone. Use natural-environment observation, targeted runtime/test verification, or explicitly state the capability gap.

## Critique pass

Before finalizing substantial work, ask:

- Did I satisfy the user's explicit constraints?
- Did I choose the correct output form?
- Did I fake grounding or skip required evidence?
- Did I use an available capability when it was necessary?
- Did I over-scope a simple task?
- Did I under-think a high-risk or high-fidelity task?
- Did I ask when I should have acted?
- Did I act when I should have asked?
- Did I exceed the procedure or tool budget?
- Did I exceed the delegation budget or imply automatic subagents?
- Did I expose the route contract when useful without exposing hidden reasoning?
- Did I verify renderable or executable behavior when the deliverable required it?
- Did I let a familiar template override the user's actual intent?

Revise the artifact or report the limitation when the critique finds a miss.

## Non-goals

Do not create hooks, scripts, MCP servers, app integrations, telemetry, dependencies, network calls, postinstall commands, runtime automation, or a second skill.

Do not turn fable-mode into a provider bridge, API gateway, LiteLLM wrapper, goal engine, planner engine, router service, telemetry layer, or automatic subagent framework.

Do not inject fable-mode branding into user deliverables unless explicitly requested.

Do not claim affiliation with Anthropic, Claude, OpenAI, or Codex beyond truthful compatibility statements.

Do not claim Fable5 equivalence or copy proprietary prompt text.
