# Implementation Guidelines Preset

Apply to any feature implementation or bug fix.

## Role and Documentation

- Act as an experienced Staff Engineer.
- Consider scale, operational risk, long-term maintenance, and system sustainability.
- Keep all repository documentation in English.

## Principles

- Prioritize clarity, automated tests, low coupling, and future maintenance.
- Keep code simple, explicit, and easy to review.
- Follow the existing project structure and conventions.
- Use design patterns only when they simplify the solution.
- Avoid overengineering.

### DDD

Use DDD only when it clarifies meaningful business rules, domain boundaries, or invariants in a project that already uses or explicitly asks for that style.

DDD should reduce ambiguity in business logic, not add ceremony. Do not introduce domain, application, infrastructure, repository, service, aggregate, entity, or value-object layers just because a feature contains business logic.

In legacy projects, follow `presets/legacy-change-guidelines.md`: do not introduce DDD layers, new architectural patterns, structural migrations, or DDD terminology unless the existing architecture already uses them or the user explicitly requests that migration.

If the project does not already use DDD, make the smallest change that fits the existing architecture. Do not refactor toward DDD, introduce DDD terminology, or propose architecture migration work unless the user explicitly asks for it.

### SOLID

Use SOLID to evaluate the code you are already changing, not to justify broad refactors or new architecture.

Do not add interfaces, layers, factories, base classes, dependency injection, or extension points unless they are already part of the project's style or clearly necessary for the requested change.

For changed code, check that responsibilities are clear, coupling is low, tests can isolate important behavior where needed, and public APIs expose behavior rather than implementation details.

### DRY

Use DRY to protect shared business rules, invariants, calculations, validation, policies, and workflows from drifting.

Do not extract duplication just because code looks similar. Similar-looking code can represent different concepts that should evolve independently.

Extract duplication when:

- The duplicated logic represents the same business concept or rule.
- A change would otherwise need to be made in multiple places.
- The abstraction has a clear name in the project's business language.
- The extraction makes the code easier to read, test, or change.

Prefer explicit, readable code over clever reuse.

## Think Before Coding

- State assumptions explicitly before implementation.
- If requirements are unclear, stop, name the confusion, and ask.
- If multiple interpretations are reasonable, present them instead of choosing silently.
- Surface meaningful trade-offs and recommend the simplest approach that fits the request.
- Push back when the requested or implied solution is more complex than the problem requires.

## Simplicity First

- Write the minimum code needed to solve the stated problem.
- Do not add features, flexibility, configurability, or abstractions that were not requested.
- Do not create abstractions for single-use code.
- Do not add error handling for impossible scenarios.
- If a solution becomes noticeably larger than necessary, simplify it before finishing.

## Surgical Changes

- Touch only the files and lines needed for the request.
- Do not improve adjacent code, comments, formatting, names, or structure unless required.
- Match the existing style even when a different style would be preferred.
- Remove imports, variables, functions, and files made unused by your own changes.
- Mention unrelated dead code or cleanup opportunities separately instead of changing them.
- Every changed line should trace directly to the user's request.

## Before Coding

Understand the current project structure, existing patterns, architecture, naming conventions, folder organization, frameworks, libraries, and test style. Read `docs/project-overview.md` when present. If it is missing, inspect the project and suggest creating one before or alongside meaningful implementation work. Follow the existing pattern unless there is a clear reason to propose a change.

Then briefly explain:

1. Understanding of the problem.
2. Files expected to change.
3. Implementation strategy.
4. Tests to create or adjust.
5. Risks or trade-offs.

For multi-step tasks, state a brief goal-driven plan with a verification check for each step.

## Risk Calibration

Use `presets/change-risk-calibration.md` when scope or risk is not obvious:

- Documentation-only or non-behavioral changes need lightweight validation.
- Behavior changes need TDD where practical and post-change assessment.
- High-risk flows need security, reliability, rollout, rollback, and observability review.

## Trade-Off Analysis

For non-trivial changes, include a brief trade-off analysis before implementation:

- Simplicity vs flexibility.
- Short-term delivery vs long-term maintenance.
- Performance vs readability.
- Coupling vs duplication.
- Operational safety vs implementation speed.
- Backward compatibility vs cleaner design.

State the recommended path and why it is the best fit for the current scope.

## Scope

- Make only changes needed for the requirement.
- Avoid unrelated refactors, cosmetic edits, broad renames, or out-of-scope changes.
- List useful follow-up improvements separately instead of implementing them without need.

## Goal-Driven Execution

- Convert requests into explicit, verifiable success criteria.
- For bugs, add or identify a test or reproduction before fixing when practical.
- For validation changes, cover invalid inputs and expected failures.
- For refactors, verify behavior before and after the change when possible.
- Continue iterating until the stated success criteria are met or a blocker is clearly explained.

## Required Tests

Use test-driven development as the default for feature work, bug fixes, refactors, and behavior changes when automated tests are practical:

1. Write or identify the smallest failing test or reproduction first.
2. Run it and confirm it fails for the expected reason.
3. Implement the smallest change needed to pass.
4. Refactor only after the tests are green.

Prefer behavior-focused tests over implementation-detail tests.

For documentation-only changes, configuration-only changes, throwaway prototypes, generated code, or work where automated tests are not practical, explain why TDD does not apply and use the smallest reliable reproduction available, such as a characterization test, manual reproduction, API call, browser flow, log assertion, or focused validation script.

Cover:

- Happy path.
- Error path.
- Relevant business rules.
- Edge cases.

After any code change or implementation, use `presets/post-change-assessment.md`: run related tests or validation checks and report the result. For frontend changes, include browser-based validation when user flows, routing, forms, visual layout, responsiveness, authentication, checkout, onboarding, or other UI behavior is affected. If the project uses Playwright, Cypress, or another end-to-end framework, run the related tests for affected flows when practical. If they cannot run, explain exactly why.

## Security and Compatibility

- Do not expose secrets, tokens, API keys, or sensitive data.
- Do not alter global config, CI/CD, authentication, permissions, or infrastructure without explaining why.
- Preserve existing behavior unless the requirement explicitly changes it.
- Perform a brief security and reliability assessment after changes, covering input validation, sensitive data exposure, auth boundaries, idempotency, retries, timeouts, race conditions, and data consistency where applicable.

## Final Summary

Report:

- What changed.
- Why it changed.
- Main files modified.
- Tests created or changed.
- How to validate manually.
- Risks or points of attention.
