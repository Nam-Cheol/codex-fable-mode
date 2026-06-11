# Test Prompts

Use these prompts to evaluate whether `fable-mode` routes tasks through the intended domain-neutral guidance.

These are evaluation examples, not built-in domain bias. Domain-specific prompts belong here, not in core routing logic.

Expected behavior is descriptive, not an automated test suite.

## 1. Child solar system experience

Prompt:

```text
$fable-mode Build a full-screen solar system exploration experience for a 7-year-old. It should be grounded in real planets and NASA-style space imagery, with very little reading and lots to touch.
```

Expected behavior:

- Treat the age and reading level as audience constraints, not as a permanent routing preference.
- Classify the output form as an interactive experience, not a generic webpage or dashboard.
- Treat real planets and NASA-style imagery as grounding requirements.
- Check whether image, asset, browsing, or reference tools are available before claiming visual grounding.
- If required assets or tools are unavailable, say so and offer an honest lower-fidelity path.

## 2. Engine simulator

Prompt:

```text
$fable-mode Build an engine simulator where I can adjust throttle, load, and temperature and see how the model responds.
```

Expected behavior:

- Classify the output form as a simulation, not automatically a dashboard.
- Determine whether the model needs real formulas, simplified behavior, or user-provided equations.
- Choose a substrate that fits continuous interaction and state updates.
- Disclose any simplified physics or missing domain grounding.

## 3. Pixel editor

Prompt:

```text
$fable-mode Make a pixel editor with brush, eraser, palette, undo, zoom, and export.
```

Expected behavior:

- Classify the output form as a creative tool or editor.
- Prefer an appropriate drawing substrate instead of one DOM control per pixel unless the scale is tiny and justified.
- Build expected tool controls and states rather than a landing page.
- Verify that the work surface, tools, and export flow behave coherently.

## 4. Small CSS overflow fix

Prompt:

```text
$fable-mode The label in this button wraps on mobile. Fix the CSS bug only.
```

Expected behavior:

- Route to small-fix protocol, not a design overhaul.
- Treat "CSS bug only" as a scope constraint.
- Inspect only the smallest relevant CSS/component area.
- Preserve existing design direction.
- Verify the button text fits at relevant viewport sizes if possible.

## 5. Code review

Prompt:

```text
$fable-mode Review this diff for regressions and missing tests.
```

Expected behavior:

- Use a code-review stance with findings first.
- Ground findings in actual changed files and line references.
- Prioritize bugs, behavioral regressions, risks, and missing tests.
- Do not rewrite the patch unless the user asks for fixes.

## 6. Architecture discussion

Prompt:

```text
$fable-mode We are deciding whether to move this service from a monolith module to an event-driven boundary. Help us choose.
```

Expected behavior:

- Use L3 or L4 depth depending on risk and available context.
- Identify decision criteria, trade-offs, reversibility, and migration risk.
- Ask only for missing information that materially changes the recommendation.
- Avoid pretending the best architecture is known without system context.

## 7. Brand-aligned UI redesign

Prompt:

```text
$fable-mode Redesign this settings screen to match our existing brand and design system.
```

Expected behavior:

- Treat brand and design-system alignment as grounding requirements.
- Inspect available code, tokens, screenshots, or docs when possible.
- State the gap if brand assets or references are missing.
- Do not default to a generic stylish screen that ignores the existing system.

## 8. Performance improvement request

Prompt:

```text
$fable-mode Make this report page faster. It feels slow with large datasets.
```

Expected behavior:

- Treat performance as a measurement-grounded request.
- Inspect code and data flow before changing behavior.
- Measure or explain what could not be measured.
- Avoid claiming a speedup without evidence.
- Verify correctness after optimization.
