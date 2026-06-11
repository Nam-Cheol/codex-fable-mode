# Design Review Rubric

Use this checklist before claiming that UI or design work is complete.

## Substrate Review

- Did the substrate match the product archetype?
- Did the main interaction surface use the correct primitive?
- Did we avoid excessive DOM nodes for dense visual data?
- Did we separate semantic controls from visual rendering surfaces?
- Would the design work at 2x, 4x, or 10x the current object count?
- Did we preserve accessibility despite canvas/SVG/WebGL?
- Did the substrate improve performance, precision, maintainability, or UX?
- Did we avoid turning creative tools into dashboards?
- Did we avoid using visual containment as a substitute for interaction design?

## Purpose

- Is the screen's main job obvious?
- Does the first viewport answer why the user is here?
- Are primary and secondary actions distinct?

## Hierarchy

- Does the eye know where to go first?
- Are content priority and action priority aligned?
- Is emphasis created through placement, scale, contrast, and rhythm rather than weight alone?

## Composition

- Is the layout more intentional than a card grid?
- Do sections have clear roles?
- Are repeated elements actually peers?

## Rhythm

- Are spacing, scale, and density deliberately varied?
- Does the layout support scanning?
- Are compact areas appropriately compact and important areas allowed to breathe?

## Surface Model

- Are borders, backgrounds, shadows, and elevation used sparingly?
- Does each container clarify structure or interaction?
- Are nested surfaces avoided unless they represent nested objects?

## Typography

- Does type create structure rather than decoration?
- Are sizes and weights appropriate to the surface?
- Is line length comfortable?

## Originality

- Does the design avoid common AI-design tropes?
- Does it feel specific to the product and audience?
- Is visual personality coming from system choices rather than decorative add-ons?

## Context Fit

- Does it match the product, brand, and codebase?
- Does it reuse existing tokens and components where appropriate?
- Are new patterns justified?

## Accessibility

- Are contrast, focus states, and hit targets acceptable?
- Can keyboard and pointer users complete the task?
- Are states, errors, and disabled controls understandable?

## Responsiveness

- Does the layout survive small and wide screens?
- Do labels, controls, and content avoid overlap?
- Does density adapt without losing priority?

## Implementation

- Is the code maintainable and tokenized?
- Are styles scoped to the right components?
- Are layout rules explicit rather than accidental?

## Content Integrity

- Did the work avoid filler, fake stats, and unnecessary icons?
- Is copy truthful and useful?
- Does every visible element earn its place?
