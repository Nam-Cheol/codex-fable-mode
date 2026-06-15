# Investigation Protocol

Use this when the cause of a bug, regression, performance issue, or behavioral failure is unknown.

The protocol is reproduce-first and evidence-first. It is not a mandate to over-investigate simple fixes.

## Before fixing

1. Observe or reproduce the failure when possible.
2. Name the original failure mode.
3. Keep at least two plausible hypotheses active.
4. For L3/L4 investigations, keep at least three plausible hypotheses active.
5. Gather evidence that distinguishes the hypotheses.
6. Fix the causal path, not only the nearest symptom.

## Evidence examples

- failing test
- reproduction steps
- log line
- screenshot
- runtime behavior
- changed diff
- data shape
- API response
- timing or profile measurement
- user-provided evidence

## Verification

After the fix, verify:

- the original failure mode
- the touched surface
- the highest-risk nearby behavior introduced by the change

If reproduction or runtime evidence is unavailable, say what could not be verified. Do not present the fix as proven.

## Budget fit

For L1, keep this local and quick.

For L2, use targeted tests or runtime checks.

For L3/L4, preserve multiple hypotheses longer and avoid committing to a root cause before evidence distinguishes it.
