# Audit Lanes

Audit lanes prevent the assistant from being trapped by the first interpretation.

They are not external agents.
They are not a harness.
They are compact critique passes used only when the depth gate requires them.

## When to use

- L0: no audit
- L1: Scope Auditor only if the fix starts expanding
- L2: Scope and Implementation Auditor
- L3: Intent, Scope, Domain, Implementation, and optional UX Auditor
- L4: all relevant auditors

## Intent Auditor

Checks whether the assistant is solving what the user actually meant.

Questions:

- What is the user likely trying to accomplish?
- Is the requested output the real goal or only a means?
- Is there a better framing?
- Is a missing decision important enough to ask?

## Scope Auditor

Checks whether the response is too heavy or too shallow.

Questions:

- Is this becoming a project when it is only a fix?
- Is this too quick for the risk involved?
- Can this be solved with a smaller reversible step?
- Is the process heavier than the task deserves?

## Domain Auditor

Checks the work category.

Questions:

- Is this a webpage, tool, game, deck, animation, editor, API, bug fix, explanation, or brainstorm?
- Does the chosen approach match that domain?
- Are we forcing the task into a familiar template?

## Implementation Auditor

Checks substrate, architecture, tests, and maintainability.

Questions:

- Is the implementation primitive appropriate?
- What breaks at 2x, 4x, or 10x scale?
- Is the change testable?
- Is the code simpler than the alternative?
- Are we introducing unnecessary dependencies or runtime behavior?

## UX/Aesthetic Auditor

Use only for UI/design work.

Questions:

- Is the design solving the user's job?
- Is the core interaction visible and usable?
- Is it relying on generic cards, borders, badges, dashboards, or filler?
- Does the design match the product archetype?

## Risk Auditor

Use for high-risk work.

Questions:

- Could this lose data, leak secrets, break auth, weaken safety, or impersonate a brand/model?
- Should the user confirm before proceeding?
- Is there a safer staged approach?

## Output

Do not expose all audit notes by default.

Only surface:

- important assumptions
- blocking questions
- material trade-offs
- risks the user must know
