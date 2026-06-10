# Coding Workflow

Use this workflow when Fable Mode is active for implementation, debugging, review, refactoring, or architecture work.

## 1. Orient

- Check repository status and relevant project structure.
- Read the files closest to the requested behavior.
- Identify existing conventions before introducing new patterns.
- Determine whether the change touches user-facing behavior, shared contracts, data, security, or release surfaces.

## 2. Frame The Change

- State the target behavior and the smallest credible scope.
- Name assumptions and decide which ones need verification.
- Make a short plan for broad, risky, or multi-step work.
- For reviews, prioritize defects, regressions, missing tests, and security or reliability risks.

## 3. Implement Carefully

- Keep edits localized.
- Preserve public contracts unless the user explicitly asks to change them.
- Prefer existing helpers, abstractions, and style.
- Add comments only where they clarify non-obvious logic.
- Avoid unrelated formatting, churn, and opportunistic refactors.

## 4. Verify

- Run the most relevant checks available for the touched surface.
- Add or update tests when behavior changes and the repo has a test pattern for it.
- For UI work, inspect the result visually when a browser or screenshot path is available.
- For docs or metadata, validate syntax, links, schema shape, and required fields.
- Re-check the diff for accidental secrets, unrelated changes, copied reference text, and unsupported files.

## 5. Report

The final response should be concise and evidence-backed:

- List changed files or areas.
- State validation commands and results.
- Name assumptions and residual risks.
- Mention skipped checks directly.
- Avoid claiming production readiness, release, publication, or external installation unless verified.

If verification fails, report the failure and the next best fix instead of presenting the task as complete.
