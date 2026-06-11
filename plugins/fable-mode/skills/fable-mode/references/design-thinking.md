# Design Thinking

Design in Fable Mode is product reasoning expressed through the correct medium. Treat the screen as an answer to a user situation, not as a collection of components waiting to be arranged.

## Start From The Job

Before producing or changing UI, identify:

- The screen's job.
- The user's current state.
- The primary action.
- Secondary actions and escape paths.
- Content priority.
- Fidelity target.
- Technical, brand, accessibility, and delivery constraints.

Do not start by choosing a component pattern. The first design question is not "what components do I need?" but "what is the correct interaction surface?" Substrate selection happens before visual direction.

A component is a consequence of the product model, hierarchy, interaction need, and implementation substrate.

## Use Existing Context First

Existing product context should dominate:

- Existing canvas, SVG, or WebGL usage.
- Design tokens.
- Component libraries.
- Layout primitives.
- Global styles.
- Brand rules.
- Type, spacing, color, and motion conventions.
- Accessibility conventions.
- Performance constraints.
- Screenshots, assets, and prior product surfaces.

Use those signals before inventing new visuals. If the repository already has a visual language, extend it with care instead of replacing it with an unrelated style.

## Define The Visual System

For substantial UI work, define the system before committing to screens:

- Type scale.
- Spacing rhythm.
- Surface model.
- Elevation model.
- Color roles.
- Density.
- Interaction states.
- Motion posture.

When no visual system exists, choose a deliberate aesthetic direction. Avoid generic defaults that could belong to any product.

## Match Medium To Product

A pixel editor is not a dashboard.
A drawing tool is not a form.
A slide deck is not a scrolling landing page.
A graph editor is not a card grid.
A dense visual surface is not a list of buttons.

The substrate shapes hierarchy, controls, accessibility, and performance. Choose the medium before polishing the look.

## Compose With Intent

Prefer layout, rhythm, scale, density, contrast, whitespace, alignment, and interaction states over decorative containment. Use containers when they clarify objects, tasks, or state. Use empty space when it clarifies priority. Use density when the task rewards scanning and comparison.

## Make The Work Reviewable

For meaningful design changes, explain:

- Which direction was selected.
- Why it fits the product.
- What trade-offs it makes.
- Which existing constraints it follows.
- Which assumptions remain unverified.

The goal is not visual novelty by itself. The goal is a screen whose structure, tone, and interaction model make the product easier to understand and use.
