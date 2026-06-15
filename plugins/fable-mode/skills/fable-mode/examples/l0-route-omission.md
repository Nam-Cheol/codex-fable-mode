# L0 Route Omission

Prompt:

```text
$fable-mode Explain debounce vs throttle in two short paragraphs.
```

Expected behavior:

- No visible route line.
- Lock=answer internally.
- Layer=L0 or L1.
- Procedure=P0.
- Tool=T0 unless current or source-backed facts are required.
- Delegation=A0.

Good response shape:

```text
Debounce waits until calls stop for a chosen delay, then runs once. It is useful for search input, resize handlers, and other cases where only the final settled action matters.

Throttle runs at most once per interval while calls continue. It is useful for scroll, drag, or live updates where you want regular updates without running on every event.
```

Failure signals:

- Shows a route line for this direct answer.
- Opens files or creates a plan.
- Expands into an implementation tutorial.
