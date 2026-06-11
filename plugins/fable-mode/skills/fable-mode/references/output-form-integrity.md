# Output Form Integrity

Do not confuse implementation tools with the desired output form.

HTML, CSS, JavaScript, Markdown, screenshots, documents, terminal commands, tests, diagrams, generated images, and code patches are tools. The output form is what the user actually asked to receive or use.

## Classify first

Before implementation, identify:

- Is the user asking for an answer, a change, a plan, a review, a document, a design, a prototype, a tool, a simulation, a test, or a shipped implementation?
- Is the requested artifact meant to be read, edited, played, operated, compared, presented, measured, or deployed?
- Is the user asking for a small fix rather than a new artifact?
- Is the user brainstorming rather than requesting implementation?
- Is the user's named format a delivery constraint or only a possible implementation method?

## Guardrails

- HTML is a tool, not automatically a webpage.
- CSS and JavaScript are tools, not automatically a card UI.
- A simulation is not automatically a dashboard.
- A small CSS bug is not automatically a redesign.
- A brainstorming request is not automatically an implementation task.
- A design request is not automatically a website.
- A review request is not automatically a rewrite.

## Result

Choose the output form before choosing the implementation substrate.

If the user explicitly asks for a format, honor it unless it conflicts with a higher-priority constraint or is impossible in the current environment.
