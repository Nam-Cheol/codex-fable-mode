# Design Exploration

Do not converge too early on non-trivial UI work. Explore enough directions to make the final choice intentional.

## When To Explore

Explore at least three directions when the task changes:

- A screen or flow.
- Visual hierarchy.
- Navigation.
- Interaction model.
- Dashboard density.
- Landing page structure.
- Component language.
- Design system rules.
- Brand or visual tone.

Small fixes inside an established pattern do not need a full exploration pass.

## Explore Substrate Before Aesthetics

For substantial UI work, compare at least two substrate candidates before choosing a visual direction.

Candidate examples:

- DOM-first.
- CSS-layout-first.
- Canvas-first.
- SVG-first.
- WebGL-first.
- Fixed-stage.
- Hybrid DOM + canvas.
- Hybrid DOM + SVG.
- Hybrid DOM + WebGL.

Compare each candidate by:

- Interaction fidelity.
- Accessibility.
- Performance.
- Implementation complexity.
- Scalability.
- Product metaphor.
- Fit with existing codebase.
- Maintainability.

Choose the substrate first. Then explore visual directions that fit that substrate instead of forcing every product into the same DOM/card/grid model.

## Required Directions

### 1. Grounded

Fits the existing product language and minimizes risk.

State:

- Layout concept.
- Information hierarchy.
- Surface strategy.
- Type strategy.
- Interaction model.
- What improves.
- What risks increase.

### 2. Elevated

Improves hierarchy, rhythm, typography, spacing, interaction, and visual confidence while preserving the product model.

State:

- Layout concept.
- Information hierarchy.
- Surface strategy.
- Type strategy.
- Interaction model.
- What improves.
- What risks increase.

### 3. Divergent

Changes composition, metaphor, navigation, density, or interaction pattern to escape generic AI layout.

State:

- Layout concept.
- Information hierarchy.
- Surface strategy.
- Type strategy.
- Interaction model.
- What improves.
- What risks increase.

## Choosing A Direction

Choose a direction when the task, product context, and risk profile imply a clear best path. Name the choice before implementation.

Ask the user to choose when the trade-off is material, such as:

- Familiarity versus novelty.
- Dense operations versus editorial clarity.
- Brand expressiveness versus restrained utility.
- Fast implementation versus a deeper interaction change.

## Implementation Handoff

After choosing, translate the direction into concrete rules:

- Layout grid or shell.
- Spacing scale.
- Type hierarchy.
- Surface and border rules.
- Color roles.
- Component behavior.
- Responsive behavior.
- States and transitions.

Implementation should follow those rules instead of drifting into local, one-off styling decisions.
