# Output Lock

Before planning, asking, or using tools, lock the primary output type.

The lock is a routing decision, not a public ritual. Use it to keep answer tasks from becoming implementation tasks, small fixes from becoming redesigns, and reviews from becoming rewrites.

## Primary locks

Choose exactly one primary lock:

- answer
- edit
- implementation
- review
- audit
- design artifact
- research
- clarification
- validation

Secondary needs may exist, but they must support the primary lock. For example, implementation may include validation, and review may include light research, but the final output should still match the primary lock.

## Lock questions

Ask internally:

- What does the user need to receive or use at the end?
- Did the user ask for a change, or only for an answer?
- Is this a local edit or a larger implementation?
- Is this a review/audit where findings are the output?
- Is the user asking for research grounded in current or source-backed facts?
- Is the only honest next output a clarification question?
- Is the task primarily to validate a claim, behavior, or artifact?

## Lock effects

The output lock determines:

- reasoning depth
- which reference docs to read
- whether to ask or act
- whether tools are allowed
- how much verification is enough
- final response length

## Lock table

| Lock | Default depth | Ask or act | Tool allowance | Verification | Final shape |
| --- | --- | --- | --- | --- | --- |
| answer | L0-L1 | act from context unless blocked | none unless grounding/current facts require tools | none or source check | direct answer |
| edit | L1 | act when scope is clear | narrow file read and focused edit tools | touched surface only | cause, fix, check |
| implementation | L2-L3 | short plan, then act | scoped reads, edits, and relevant checks | changed behavior and nearby contracts | changes and checks |
| review | L2-L3 | act from diff/context | read changed surface; no edits by default | finding evidence only | findings first |
| audit | L3-L4 | ask if scope or risk is unclear | scoped discovery; avoid broad sweeps unless required | evidence for material claims | concise risks and gaps |
| design artifact | L3 | ask only for blocking fidelity choices | refs/assets/tools required by fidelity | artifact-specific QA | selected direction and result |
| research | L2-L4 | ask if scope/source standard changes answer | source, docs, or web tools when required | cite or separate verified from inferred | answer with sources/limits |
| clarification | L0 | ask | no tools unless a quick local check avoids asking | none | one focused question |
| validation | L1-L3 | act when target is known | tools needed to inspect, run, or measure target | the claim or touched surface | verdict and evidence |

## Reference selection

Always apply intent framing, output lock, depth gate, and procedure budget first.

After that, read only the references required by the lock:

- answer: final-response, and grounding-integrity only if facts need support
- edit: small-fix-protocol, constraint-integrity, tool-budget
- implementation: coding-workflow, constraint-integrity, grounding-integrity, capability-fit, tool-budget
- review: audit-lanes, grounding-integrity, final-response
- audit: audit-lanes, safety-boundaries when relevant, grounding-integrity
- design artifact: output-form-integrity, output-archetype, design-thinking, substrate-selection, grounding-integrity
- research: grounding-integrity, capability-fit, tool-budget, final-response
- clarification: ask-or-act, final-response
- validation: grounding-integrity, capability-fit, tool-budget, final-response

Do not read every reference file by default. More procedure is not better when the lock does not need it.

## Lock changes

Change the lock only when new evidence shows the initial lock was wrong or the user changes the request.

If the change affects scope, say so briefly:

> I treated this as a review rather than an implementation, so I did not edit files.

Do not silently pivot from answer to implementation, edit to redesign, review to rewrite, or validation to broad audit.
