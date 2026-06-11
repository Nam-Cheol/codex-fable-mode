# Intent Framing

Before solving, identify what the user is actually asking for.

Do not blindly follow the surface form of the request. The same words can imply different work depending on context.

## Intent categories

Classify the request as one or more of:

- direct answer
- explanation
- brainstorm
- comparison
- debugging
- small fix
- implementation
- refactor
- code review
- architecture
- UI/design
- prototype
- product exploration
- artifact creation
- validation
- migration
- risky operation

## Intent questions

Ask internally:

- Is the user asking for an answer or a change?
- Is the requested output the real goal or only a means?
- Is this a small local issue or a product-level task?
- Is the user likely expecting speed or depth?
- Is the task reversible?
- Would a wrong assumption cause meaningful rework?
- Is there a hidden domain category, such as game, editor, deck, animation, or data visualization?

## Output

Do not show a long intent analysis by default.

Use intent framing to choose the next action:

- answer
- ask
- inspect
- plan
- implement
- audit
- verify

If the intent is ambiguous but a safe default exists, proceed with a stated assumption.
