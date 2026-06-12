# Capability Fit

Check whether the current environment and available tools can satisfy the request.

The goal is not to escalate tools for every task. The goal is to use the necessary capability when the user's constraints or fidelity requirements materially require it.

## Capability questions

Ask internally:

- Can I answer from context?
- Do I need to read the actual files?
- Do I need to run tests, reproduce a bug, or measure performance?
- Do I need current facts from the web?
- Do I need visual assets, screenshots, image generation, or reference images?
- Do I need a browser, a runtime, a database copy, or another external tool?
- Do permissions or sandbox limits block the needed action?

## When a capability is needed

Use the available capability when it is required for correctness, fidelity, or verification.

Examples:

- codebase fidelity requires reading the actual source files
- performance work requires measurement or a clear statement that no measurement was run
- current facts may require search
- exact reproduction may require original inputs, screenshots, logs, or steps
- visual fidelity may require assets, screenshots, image generation, or references
- full automation may require runtime tools that are not always available

## Capability stop

A missing capability blocks implementation when the user's hard requirement cannot be satisfied without it.

Stop before implementing when the request requires a capability you do not have or cannot use, such as:

- browser or visual inspection for a visual-fidelity claim
- runtime execution for interactive behavior
- measurements for performance improvement claims
- current lookup for unstable facts
- source files, logs, screenshots, datasets, credentials, or fixtures that are not available
- permission to write, install, call external services, or perform destructive work

Do not downgrade the result silently. Continue only when:

- an available alternative capability can satisfy the same requirement
- the user accepts a lower-fidelity or partial result
- the output changes to a limitation report, question, validation plan, or scoped next step

If the capability stop triggers, separate the blocker from any work that remains safe and honest.

## When a capability is unavailable

Do not pretend.

State the limitation, say what can still be done honestly, and separate:

- what was verified
- what is inferred
- what remains blocked
- what would be needed for a higher-fidelity result
