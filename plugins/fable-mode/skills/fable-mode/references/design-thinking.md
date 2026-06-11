# Design Thinking

Design is product reasoning expressed through the correct medium.

Do not start from components. Start from the job of the artifact.

## Before designing

Identify:

- output archetype
- user's job-to-be-done
- user state of mind
- primary action
- secondary actions
- content priority
- expected fidelity
- interaction model
- constraints
- existing visual vocabulary
- implementation substrate

The first design question is not:

> What components do I need?

The first design question is:

> What is the correct interaction surface for this user intent?

## Context first

When a codebase or existing UI exists, inspect it before inventing a new system.

Look for:

- design tokens
- layout primitives
- component libraries
- global styles
- type scale
- spacing scale
- color roles
- interaction states
- accessibility conventions
- existing canvas/SVG/WebGL usage
- performance constraints

Do not infer from file names alone. Read the relevant source.

## Medium before polish

HTML may be the container, but the output may be:

- a game
- an editor
- a deck
- an animation
- a prototype
- a document
- a dashboard
- a visual workbench

A pixel editor is not a dashboard.
A drawing tool is not a form.
A slide deck is not a scrolling landing page.
A graph editor is not a card grid.

## Visual system

Before building substantial UI, define:

- type scale
- spacing rhythm
- surface model
- color roles
- density
- motion posture
- interaction states
- responsive behavior

Prefer layout, rhythm, scale, density, contrast, whitespace, alignment, and interaction states before decorative containment.

## Anti-slop rule

Avoid defaulting to:

- generic rounded cards
- nested panels
- badge-heavy interfaces
- fake metrics
- dashboard tiles
- arbitrary gradients
- unnecessary icons
- eyebrow labels above every heading
- dark panels as a substitute for design direction

Cards, borders, grids, gradients, and badges are allowed only when they earn their place.
