# Small Fix Protocol

Use this for localized bugs and visual fixes.

## Examples

- text overflows its container
- button click does not work
- modal does not close
- layout breaks on mobile
- color or spacing needs a minor adjustment
- one component is misaligned
- one interaction has a clear failure mode

## Rules

- Do not redesign the product.
- Do not introduce a new architecture.
- Do not ask broad discovery questions.
- Do not generate a spec unless requested.
- Inspect the smallest relevant source area.
- Fix the cause, not only the symptom, when possible.
- Preserve existing visual vocabulary unless the user asks for redesign.
- Verify the specific behavior.
- Summarize briefly.

## CSS-specific checks

For overflow:

- check `min-width: 0` in flex/grid children
- check `overflow-wrap`, `word-break`, and `white-space`
- check fixed widths and max widths
- check line height and container constraints

For mobile layout:

- check viewport assumptions
- check grid/flex wrapping
- check hit target size
- check content order

For alignment:

- check parent layout model first
- avoid one-off margins unless the surrounding system already uses them

## JS-specific checks

For broken buttons:

- check event listener registration
- check disabled state
- check selector mismatch
- check event propagation
- check state update path
- check console errors

For import/export:

- validate input
- handle parse failure
- avoid data loss on invalid input
