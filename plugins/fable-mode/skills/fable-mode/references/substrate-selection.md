# Substrate Selection

Before designing or implementing UI, decide the correct implementation substrate.

Do not assume every interface should be built as nested DOM cards, grids, panels, and buttons. The first design decision is the medium of interaction.

## Required Substrate Decision Record

Before coding substantial UI/design work, produce a short record:

- Product archetype:
- Primary interaction:
- Object count / data scale:
- Update frequency:
- Precision requirements:
- Accessibility requirements:
- Responsive constraints:
- Recommended substrate:
- Rejected alternatives:
- Reason:

For small tasks, keep this to 3-5 lines.
For substantial tasks, make it explicit before implementation.

## Substrate guide

Use DOM when:

- the interface is mostly semantic text, forms, navigation, settings, CRUD, documentation, lists, tables, or ordinary app controls
- accessibility and native semantics matter more than continuous rendering
- object count is moderate and individual items need native focus or interaction

Use CSS layout when:

- the task is composition, responsive structure, editorial layout, marketing sections, dashboards, or information hierarchy
- the interface does not require direct pixel-level drawing, dense visual rendering, or high-frequency updates

Use canvas when:

- the core product is drawing, painting, pixel editing, image manipulation, waveform editing, whiteboarding, particle systems, heatmaps, game boards, or dense visual surfaces
- many visual cells or objects update frequently
- representing each visual element as a DOM node would create excessive nodes or poor keyboard navigation
- pointer precision matters

Use SVG when:

- the product needs scalable vector shapes, diagrams, icon systems, annotations, connectors, node-link graphs, or directly selectable vector objects
- object count is moderate and individual elements benefit from inspectable structure

Use WebGL only when:

- the design needs thousands of moving objects, 3D, advanced shaders, heavy visual effects, or canvas/SVG is insufficient
- the added complexity is justified by scale or interaction needs

Use fixed-stage architecture when:

- the output is a deck, presentation, video, fixed-ratio prototype, storyboard, or other non-scrolling artifact
- the content should scale into the viewport while preserving aspect ratio

Use hybrid architecture when:

- DOM controls, panels, forms, and inspectors surround a canvas/SVG/WebGL work surface
- semantic controls and dense visual rendering have different needs
- accessibility overlays or semantic summaries are needed around a non-DOM visual surface

## Default rejection rule

If the design contains a large interactive surface, do not implement it as one DOM node per cell/object unless the object count is tiny and the trade-off is explicitly justified.

For pixel editors, paint tools, image editors, map-like canvases, dense boards, waveform tools, whiteboards, timeline editors, or game boards, prefer a canvas/SVG/WebGL work surface plus DOM controls.

## Domain examples

- Pixel editor: canvas work surface + DOM toolbar, palette, inspector, and export controls.
- Drawing app: canvas or SVG work surface + DOM inspector and layers panel.
- Image editor: canvas work surface + DOM controls.
- Graph editor: SVG for moderate selectable graphs; canvas/WebGL for large dense graphs.
- Dashboard: DOM/CSS layout, not canvas.
- Text-heavy settings page: DOM.
- Slide deck: fixed-ratio stage, not ordinary scrolling page.
- Animation: coherent timeline/state model, not scattered timers.
- Data table: DOM table/grid or virtualization; not canvas unless scale or custom rendering demands it.
- Game board: canvas for dense or high-frequency boards; DOM only for small semantic board games where accessibility is central.

## Design implication

The substrate shapes the design. Choose substrate before visual polish.

A pixel editor is not a dashboard.
A drawing tool is not a form.
A slide deck is not a scrolling landing page.
A graph editor is not a card grid.
A dense visual surface is not a list of buttons.
