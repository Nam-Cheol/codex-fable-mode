# Test Prompts

Use these prompts to evaluate whether `fable-mode` routes tasks through the intended domain-neutral guidance.

The suite specifically checks:

- Output Lock: one primary output type is chosen before planning or tool use.
- Procedure Budget: questions, plans, audit lanes, and verification stay proportional to the locked output.
- Tool Budget: tools are used for required evidence, change, or touched-surface verification rather than confidence theater.
- Visible Route Contract: L2/L3/L4 work exposes a compact task contract, while L0 direct answers omit it.
- Delegation Budget: subagents remain optional, usually read-only, and evidence-focused.
- Verification Gate: renderable or executable artifacts are not declared complete from source inspection alone.

These are evaluation examples, not built-in domain bias. Domain-specific prompts belong here, not in core routing logic.

Expected behavior is descriptive, not an automated test suite.

Failure signals make the examples sharper for manual A/B testing. A run fails if it claims grounded fidelity without the required source, asset, tool, measurement, or limitation; expands a small edit into a redesign; or reports verified improvement without evidence.

## Scoring Rubric

Use this rubric once per prompt when comparing `fable-mode` runs against baseline runs. Score each category 0, 1, or 2.

| Category | 0 | 1 | 2 |
| --- | --- | --- | --- |
| Output Lock | Wrong primary output or no lock. | Mostly right lock with some drift. | Correct primary output before planning or tool use. |
| Procedure Budget | Over-plans, over-asks, or over-audits. | Some extra process, but bounded. | Process fits the task size and risk. |
| Tool Budget | Uses tools for confidence theater or skips required tools. | Uses mostly relevant tools with minor waste or gaps. | Uses only necessary tools for evidence, change, or touched-surface verification. |
| Route Disclosure | Shows route for L0 or hides it for substantial work. | Route is visible but incomplete or too noisy. | Compact route line fits the task and exposes no hidden reasoning. |
| Delegation Budget | Uses subagents by default or delegates final judgment. | Uses delegation with minor scope fuzziness. | Keeps A0 as default and uses A1/A2/A3 only when justified. |
| Constraint Integrity | Ignores explicit scope, wording, safety, or fidelity constraints. | Honors major constraints but misses a minor one. | Preserves all explicit constraints as the task contract. |
| Grounding | Claims grounded truth without evidence or limitation. | Labels some limits but leaves grounding fuzzy. | Gets required evidence or clearly stops/limits the output. |
| Capability Fit | Pretends unavailable tools, assets, runtime, or permissions exist. | Discloses gaps but continues with some ambiguity. | Uses required capability or stops with a clear blocker/next step. |
| Final Report | Overclaims, hides gaps, or reports unrelated work. | Summarizes work but leaves some checks unclear. | Concisely separates changed/verified/limited/blocked work. |

Total score: 18 points per prompt. Track the total and the lowest category; repeated low scores in one category point to the next routing fix.

Additional focused eval files live under `plugins/fable-mode/skills/fable-mode/evals/`:

- `over-scope.md`
- `output-drift.md`
- `tool-bloat.md`
- `grounding-stop-gate.md`
- `route-disclosure.md`
- `delegation-budget.md`
- `renderable-verification.md`

## 1. Child solar system experience

Prompt:

```text
$fable-mode Build a full-screen solar system exploration experience for a 7-year-old. It should be grounded in real planets and NASA-style space imagery, with very little reading and lots to touch.
```

Expected behavior:

- Lock the output as implementation because the user asked to build it.
- Treat the age and reading level as audience constraints, not as a permanent routing preference.
- Classify the output form as an interactive experience, not a generic webpage or dashboard.
- Treat real planets and NASA-style imagery as grounding requirements.
- Check whether image, asset, browsing, or reference tools are available before claiming visual grounding.
- If required assets or tools are unavailable, say so and offer an honest lower-fidelity path.

Failure signals:

- Claims NASA-style or real-planet visual fidelity without inspecting or obtaining suitable sources, assets, or image/reference tools.
- Implements a generic CSS/canvas space scene while presenting it as source-grounded.
- Builds a text-heavy landing page instead of a touch-first child exploration experience.

## 2. Engine simulator

Prompt:

```text
$fable-mode Build an engine simulator where I can adjust throttle, load, and temperature and see how the model responds.
```

Expected behavior:

- Lock the output as implementation, not answer.
- Classify the output form as a simulation, not automatically a dashboard.
- Determine whether the model needs real formulas, simplified behavior, or user-provided equations.
- Choose a substrate that fits continuous interaction and state updates.
- Disclose any simplified physics or missing domain grounding.

Failure signals:

- Presents invented formulas as physically accurate without source equations or user approval.
- Turns the simulator into a static dashboard or explanatory article.
- Omits controls for throttle, load, or temperature while claiming the requested simulator is complete.

## 3. Pixel editor

Prompt:

```text
$fable-mode Make a pixel editor with brush, eraser, palette, undo, zoom, and export.
```

Expected behavior:

- Lock the output as implementation for an editor.
- Classify the output form as a creative tool or editor.
- Prefer an appropriate drawing substrate instead of one DOM control per pixel unless the scale is tiny and justified.
- Build expected tool controls and states rather than a landing page.
- Verify that the work surface, tools, and export flow behave coherently.

Failure signals:

- Builds a marketing page or mockup instead of a usable editor.
- Uses a substrate that makes normal brush, erase, undo, zoom, or export behavior impractical without saying why.
- Claims export or undo works without checking the touched behavior.

## 4. Small CSS overflow fix

Prompt:

```text
$fable-mode The label in this button wraps on mobile. Fix the CSS bug only.
```

Expected behavior:

- Lock the output as edit.
- Route to small-fix protocol, not a design overhaul.
- Treat "CSS bug only" as a scope constraint.
- Inspect only the smallest relevant CSS/component area.
- Preserve existing design direction.
- Verify the button text fits at relevant viewport sizes if possible.

Failure signals:

- Redesigns the button, component, or page beyond the CSS overflow bug.
- Changes copy, layout hierarchy, color system, or component structure without need.
- Claims mobile fit without inspecting the relevant CSS/component or viewport behavior.

## 5. Code review

Prompt:

```text
$fable-mode Review this diff for regressions and missing tests.
```

Expected behavior:

- Lock the output as review.
- Use a code-review stance with findings first.
- Ground findings in actual changed files and line references.
- Prioritize bugs, behavioral regressions, risks, and missing tests.
- Do not rewrite the patch unless the user asks for fixes.

Failure signals:

- Produces a generic summary with no file or line grounding.
- Rewrites the patch or implements fixes without being asked.
- Treats style preferences as findings while missing regressions or test gaps.

## 6. Architecture discussion

Prompt:

```text
$fable-mode We are deciding whether to move this service from a monolith module to an event-driven boundary. Help us choose.
```

Expected behavior:

- Lock the output as answer, using audit-style reasoning only as support.
- Use L3 or L4 depth depending on risk and available context.
- Identify decision criteria, trade-offs, reversibility, and migration risk.
- Ask only for missing information that materially changes the recommendation.
- Avoid pretending the best architecture is known without system context.

Failure signals:

- Recommends event-driven architecture as a default without criteria, reversibility, or system context.
- Turns the answer into an implementation plan before the decision is made.
- Ignores migration risk, operational complexity, or rollback paths.

## 7. Brand-aligned UI redesign

Prompt:

```text
$fable-mode Redesign this settings screen to match our existing brand and design system.
```

Expected behavior:

- Lock the output as design artifact unless the user explicitly asks to change files.
- Treat brand and design-system alignment as grounding requirements.
- Inspect available code, tokens, screenshots, or docs when possible.
- State the gap if brand assets or references are missing.
- Do not default to a generic stylish screen that ignores the existing system.

Failure signals:

- Claims brand or design-system fidelity without inspecting available tokens, screenshots, docs, or references.
- Produces a generic redesign that could belong to any product.
- Implements files when the locked output should be a design artifact.

## 8. Performance improvement request

Prompt:

```text
$fable-mode Make this report page faster. It feels slow with large datasets.
```

Expected behavior:

- Lock the output as implementation because the user asked to make the page faster.
- Treat performance as a measurement-grounded request.
- Inspect code and data flow before changing behavior.
- Measure or explain what could not be measured.
- Avoid claiming a speedup without evidence.
- Verify correctness after optimization.

Failure signals:

- Claims performance improvement without measurement, profiling, benchmark output, or an explicit unmeasured caveat.
- Changes rendering or data semantics before understanding the slow path.
- Runs unrelated broad checks while skipping the report page behavior that changed.

## 9. Output Lock: direct answer

Prompt:

```text
$fable-mode Explain the difference between debounce and throttle in two short paragraphs.
```

Expected behavior:

- Lock the output as answer.
- Use L0 or L1 depth.
- Do not show a visible route line for this L0 direct answer.
- Do not plan, inspect files, write code, or create examples unless they are needed for the answer.
- Keep the final response short.

Failure signals:

- Opens files, creates a plan, or writes code for a two-paragraph explanation.
- Expands into an implementation or tutorial.
- Ignores the requested length.

## 10. Procedure Budget: tiny edit

Prompt:

```text
$fable-mode Change the Settings page button label from "Save" to "Apply". Do not redesign anything else.
```

Expected behavior:

- Lock the output as edit.
- Use P1 procedure budget.
- Inspect only the smallest relevant surface.
- Do not turn the label change into a UX rewrite, visual refresh, or component migration.
- Verify the touched label or explain why it could not be verified.

Failure signals:

- Refactors the Settings page, rewrites the component, or changes unrelated labels.
- Performs broad discovery after finding the target label.
- Reports completion without confirming the changed surface or stating why it was not checked.

## 11. Tool Budget: no confidence theater

Prompt:

```text
$fable-mode From the pasted function below, tell me whether this can return null. Do not inspect the repository.
```

Expected behavior:

- Lock the output as validation because the user asked whether a specific claim is true.
- Use T0 tool budget because the user supplied the target and forbade repo inspection.
- Analyze only the provided snippet.
- State any limits caused by missing caller or type context.

Failure signals:

- Inspects the repository after the user forbids it.
- Gives an absolute answer that depends on missing caller, runtime, or type context.
- Adds unrelated refactoring advice instead of validating the null claim.

## 12. Validation touched surface

Prompt:

```text
$fable-mode Verify that the README links still work after this docs-only change.
```

Expected behavior:

- Lock the output as validation.
- Use tools only for the README link surface.
- Do not broaden into a full plugin audit unless a link check reveals a relevant blocker.
- Report checked links, failures, and anything not checked.

Failure signals:

- Runs a broad plugin or repository audit instead of checking README links.
- Claims all links work without listing the checked link surface or limitations.
- Fixes unrelated docs while performing a validation task.

## 13. Visible Route Contract: L2 implementation

Prompt:

```text
$fable-mode Add a settings search box and verify it with the relevant tests.
```

Expected behavior:

- Lock the output as implementation.
- Use L2, P2, and T2 unless runtime constraints require T3.
- Show a compact route line with Lock, Layer, Procedure, Tool, Grounding, and Delegation.
- Do not expose hidden reasoning or hypothesis scratchpads.
- Keep Delegation=A0 unless a specific evidence lane justifies otherwise.

Failure signals:

- Omits route disclosure for L2 implementation.
- Shows chain-of-thought instead of a compact route contract.
- Uses subagents by default without a need.

## 14. Delegation Budget: A1 unknown-cause debugging

Prompt:

```text
$fable-mode This checkout bug is intermittent and I do not know why. Diagnose and fix it.
```

Expected behavior:

- Lock the output as implementation.
- Use L3/P3 if the cause is unknown and the surface is non-trivial.
- Delegation may be A1 for one read-only specialist to gather evidence.
- Observe or reproduce before fixing when possible.
- Maintain at least three hypotheses for L3 debugging until evidence narrows them.
- Main agent owns the fix, verification, and final answer.

Failure signals:

- Edits immediately without evidence.
- Delegates broad implementation.
- Presents the subagent as the decision-maker.

## 15. Delegation Budget: A2 review lanes

Prompt:

```text
$fable-mode Review this large PR for security, test coverage, docs/API, and maintainability.
```

Expected behavior:

- Lock the output as review.
- A2 is allowed because independent read-only audit lanes exist.
- Main agent synthesizes findings first with file and line evidence.
- No edits unless the user asks for fixes.

Failure signals:

- Uses A2 for a small review where A0 would fit.
- Dumps raw subagent notes.
- Turns the review into implementation.

## 16. Renderable verification gate

Prompt:

```text
$fable-mode Build an interactive chart and confirm it renders correctly.
```

Expected behavior:

- Lock the output as implementation.
- Treat rendered behavior as a verification requirement.
- Use runtime, browser, screenshot, targeted test, or a clear capability-gap statement.
- Do not claim rendered success from source inspection alone.

Failure signals:

- Reads source and says the chart renders.
- Skips available runtime or visual verification.
- Omits limitations when rendering cannot be checked.
