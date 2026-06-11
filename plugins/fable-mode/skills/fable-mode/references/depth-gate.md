# Depth Gate

Do not treat every request as a project.

The goal is not maximum reasoning. The goal is the smallest sufficient reasoning depth.

## L0 - Direct answer

Use for:

- simple conceptual questions
- short explanations
- low-risk comparisons
- quick confirmations
- conversational guidance

Behavior:

- answer directly
- do not create plans
- do not ask unless the question is impossible to answer
- do not invoke audit lanes

## L1 - Small fix

Use for:

- localized CSS issues
- one broken button
- text overflow
- layout misalignment
- a small JS behavior bug
- a minor copy or style adjustment
- one obvious bug in a bounded area

Behavior:

- inspect only relevant files
- make the smallest safe change
- avoid product redesign
- avoid broad discovery questions
- verify the specific issue

## L2 - Standard implementation

Use for:

- bounded feature work
- small components
- simple apps
- straightforward refactors
- ordinary tests
- contained repository changes

Behavior:

- make a short plan
- implement
- run relevant checks
- summarize changes and risks

## L3 - Product, design, or architecture work

Use for:

- new products
- UI redesign
- prototypes
- games
- editors
- decks
- animations
- architecture decisions
- multi-file changes
- ambiguous creative work

Behavior:

- frame intent
- classify output archetype
- choose substrate before implementation
- compare important trade-offs
- ask only blocking questions
- use audit lanes selectively

## L4 - High-risk or underspecified work

Use for:

- destructive changes
- migrations
- auth/security changes
- large rewrites
- unclear product direction
- expensive implementation
- tasks with irreversible consequences

Behavior:

- ask before acting
- use full audit lanes
- state assumptions and risks
- prefer staged plans
- verify aggressively

## Rule

If unsure between two levels, choose the lower level first unless the cost of being wrong is high.
