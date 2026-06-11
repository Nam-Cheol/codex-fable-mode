# Substrate Selection

Before designing or implementing UI, decide the correct implementation substrate.

Do not assume every interface should be built as nested DOM cards, grids, panels, and buttons. The first design decision is the medium of interaction.

## Required Substrate Decision Record

Before coding substantial UI/design work, produce a short record containing:

- Product archetype.
- Primary interaction.
- Object count / data scale.
- Update frequency.
- Precision requirements.
- Accessibility requirements.
- Responsive constraints.
- Recommended substrate.
- Rejected alternatives.
- Reason.

For small tasks, keep this to 3-5 lines. For substantial tasks, make it explicit before implementation.

## Substrate Guide

Use DOM when:

- The interface is mostly semantic text, forms, navigation, settings, CRUD, documentation, lists, tables, or ordinary app controls.
- Accessibility and native semantics matter more than continuous rendering.
- Object count is moderate and individual items need native focus or interaction.

Use CSS layout when:

- The task is composition, responsive structure, editorial layout, marketing sections, dashboards, or information hierarchy.
- The interface does not require direct pixel-level drawing, dense visual rendering, or high-frequency updates.

Use canvas when:

- The core product is drawing, painting, pixel editing, image manipulation, waveform editing, whiteboarding, particle systems, heatmaps, game boards, or dense visual surfaces.
- Many visual cells or objects update frequently.
- Representing each visual element as a DOM node would create excessive nodes or poor keyboard navigation.
- Pointer precision matters.

Use SVG when:

- The product needs scalable vector shapes, diagrams, icon systems, annotations, connectors, node-link graphs, or directly selectable vector objects.
- Object count is moderate and individual elements benefit from inspectable structure.

Use WebGL only when:

- The design needs thousands of moving objects, 3D, advanced shaders, heavy visual effects, or canvas/SVG is insufficient.
- The added complexity is justified by scale or interaction needs.

Use fixed-stage architecture when:

- The output is a deck, presentation, video, fixed-ratio prototype, storyboard, or other non-scrolling artifact.
- The content should scale into the viewport while preserving aspect ratio.

Use hybrid architecture when:

- DOM controls, panels, forms, and inspectors surround a canvas/SVG/WebGL work surface.
- Semantic controls and dense visual rendering have different needs.
- Accessibility overlays or semantic summaries are needed around a non-DOM visual surface.

## Default Rejection Rule

If the design contains a large interactive surface, do not implement it as one DOM node per cell or object unless the object count is tiny and the trade-off is explicitly justified.

For pixel editors, paint tools, image editors, map-like canvases, dense boards, waveform tools, whiteboards, timeline editors, or game boards, prefer a canvas/SVG/WebGL work surface plus DOM controls.

## Domain Examples

- Pixel editor: canvas work surface plus DOM toolbar, palette, inspector, and export controls.
- Drawing app: canvas or SVG work surface plus DOM inspector and layers panel.
- Image editor: canvas work surface plus DOM controls.
- Graph editor: SVG for moderate selectable graphs; canvas/WebGL for large dense graphs.
- Dashboard: DOM/CSS layout, not canvas.
- Text-heavy settings page: DOM.
- Slide deck: fixed-ratio stage, not ordinary scrolling page.
- Animation: coherent timeline/state model, not scattered timers.
- Data table: DOM table/grid or virtualization; not canvas unless scale or custom rendering demands it.
- Game board: canvas for dense/high-frequency boards; DOM only for small semantic board games where accessibility is central.

## Design Implication

The substrate shapes the design. Choose substrate before visual polish.

A pixel editor is not a dashboard.
A drawing tool is not a form.
A slide deck is not a scrolling landing page.
A graph editor is not a card grid.
A data table is not a canvas unless scale demands virtualization or custom rendering.

The substrate decision should improve product fit, precision, performance, accessibility, and maintainability. If it only changes the visual style, the decision is not yet deep enough.
