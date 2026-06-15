# L3 Design Route

Prompt:

```text
$fable-mode Redesign the onboarding flow to match our existing product tone and design system.
```

Expected route:

```text
Fable route: Lock=design artifact · Layer=L3 · Procedure=P3 · Tool=T1-T3 · Grounding=brand+design-system · Delegation=A0
```

Expected behavior:

- Treat design-system and product tone as grounding requirements.
- Inspect available brand, token, screenshot, or design docs when possible.
- Ask only if missing brand context blocks the result.
- Produce the requested design artifact rather than implementing files unless asked.

Failure signals:

- Implements a generic stylish screen without design-system evidence.
- Treats the request as a webpage by default.
- Claims brand fidelity when no brand source was inspected or provided.
