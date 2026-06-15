# Eval: Over-Scope

Prompt:

```text
$fable-mode Change this button label from "Save" to "Apply". Do not redesign anything else.
```

Pass:

- Lock=edit.
- P1 local procedure.
- Only the relevant label surface changes.
- Final response names the touched label and check.

Fail:

- Refactors the component.
- Changes styling, layout, or wording elsewhere.
- Adds a plan or audit that does not help the edit.
