# Output Archetype

Use this as a concrete label set after `output-form-integrity.md`.

Do not confuse implementation format with output archetype. HTML, CSS, and JavaScript may be used to build many kinds of artifacts. The artifact is not automatically a webpage.

## Common archetypes

- direct answer
- document
- app screen
- webpage
- dashboard
- creative tool
- game prototype
- slide deck
- animation
- interactive prototype
- data visualization
- simulation
- fixed-frame experience
- spatial or scene-based experience
- spatial editor
- graph editor
- image/pixel editor
- timeline editor
- mobile mockup
- design exploration canvas

## Rule

Before implementation, classify the requested artifact.

Ask:

- What is the artifact's job?
- What is the primary user action?
- Is the user meant to read, edit, play, navigate, compare, present, or decide?
- Does the result need a work surface, stage, document flow, app layout, or fixed frame?
- Is the request actually a small fix rather than a new artifact?

## Examples

If the user asks for a Pokemon-like game, the archetype is a game prototype, not a landing page.

If the user asks for text overflowing a box, the archetype is a small CSS fix, not a design project.

If the user asks for three visual directions, the archetype is design exploration, not one final app.

If the user asks for a button behavior bug, the archetype is an interaction fix, not a redesign.

If the user asks for a deck or presentation, the archetype is fixed-stage content, not a scrolling webpage.

## Archetype implications

Use a full-viewport stage for:

- games
- interactive prototypes that depend on direct manipulation
- scene-based experiences
- animation
- canvas toys
- visual simulations

Use a fixed-ratio stage for:

- decks
- presentations
- storyboards
- video-like sequences

Use a workbench layout for:

- editors
- CAD-like tools
- creative tools
- graph tools
- pixel editors
- image tools
- timeline tools

Use semantic DOM app layout for:

- forms
- settings
- CRUD
- documents
- navigation
- text-heavy app screens

Use a design canvas for:

- visual options
- style tiles
- variant comparison
- early design exploration

Do not default to webpage structure unless the requested output is actually a webpage.

Do not default to a dashboard, card layout, or side-panel-heavy app structure unless that is the requested output form.
