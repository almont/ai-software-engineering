# Legacy Change Guidelines Preset

Use this preset when working in a legacy project, an under-tested codebase, or a codebase whose architecture is inconsistent or unfamiliar.

## Principles

- Fit the change into the current structure unless the user explicitly asks for an architecture migration.
- Do not introduce DDD layers, new architectural patterns, structural migrations, or DDD terminology unless the existing architecture already uses them or the user explicitly requests that migration.
- Prefer characterization tests or the smallest practical reproduction before changing behavior.
- Keep refactors local to the change and only when they reduce risk for the requested work.
- Preserve backward compatibility unless the user explicitly requests a behavior change.
- List broader architecture improvements as follow-up work instead of implementing them opportunistically.

## Workflow

1. Read the project overview when present.
2. Identify the current architecture, naming, test style, and local patterns.
3. Find the smallest safe place to make the requested change.
4. Write or identify a failing test or reproduction when behavior changes.
5. Implement the smallest compatible change.
6. Run focused tests and applicable validation.
7. Perform the post-change security and reliability assessment.

## Review Questions

- Did this change fit the existing architecture?
- Did it avoid unrelated modernization?
- Did it preserve existing behavior outside the requested scope?
- Are any architectural improvements listed separately as follow-up work?
- Are tests or characterization coverage sufficient for the touched legacy behavior?
