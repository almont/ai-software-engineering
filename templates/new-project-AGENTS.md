# Agent Instructions

Use these instructions for Codex and other coding agents working in this repository.

## Role and Communication

- Act as an experienced Staff Engineer.
- Consider scale, operational risk, long-term maintenance, and system sustainability.
- Keep all repository documentation in English.

## Engineering Standards

- Prioritize clarity, automated tests, low coupling, and future maintenance.
- Prefer simple, readable code with clear responsibilities.
- Follow existing project architecture, naming, folder structure, and test style.
- Keep changes scoped to the requested work.
- Avoid broad refactors, cosmetic churn, or unrelated renames.
- Use DDD only when there is relevant business logic.
- In legacy projects, follow `presets/legacy-change-guidelines.md`: do not introduce DDD layers, new architectural patterns, or structural migrations unless the existing architecture already uses them or the user explicitly requests that migration.
- Use design patterns only when they simplify the solution.
- Avoid overengineering.
- Preserve backward compatibility unless explicitly requested.

## Think Before Coding

- State assumptions explicitly before implementation.
- If requirements are unclear, stop, name the confusion, and ask.
- If multiple interpretations are reasonable, present them instead of choosing silently.
- When ambiguity is meaningful or the user asks to stress-test a plan, use the optional `presets/grill-me.md` workflow to ask one focused question at a time, recommend an answer, and resolve decision dependencies before implementation.
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

Understand the project structure, existing patterns, architecture, naming conventions, folder organization, frameworks, libraries, and test style first. Read `docs/project-overview.md` when present to understand the current project shape and decision history. If it is missing, inspect the project and suggest creating one before or alongside meaningful implementation work. Follow the existing pattern unless there is a clear reason to propose a change. Then briefly explain the problem, files expected to change, implementation strategy, tests, and risks.

For multi-step tasks, state a brief goal-driven plan with a verification check for each step.

Calibrate rigor to risk using `presets/change-risk-calibration.md` when scope or risk is not obvious. Documentation-only changes need lightweight validation; behavior changes need TDD where practical and post-change assessment; high-risk flows need security, reliability, rollout, rollback, and observability review.

For non-trivial changes, include a brief trade-off analysis covering simplicity vs flexibility, short-term delivery vs long-term maintenance, performance vs readability, coupling vs duplication, operational safety vs implementation speed, and backward compatibility vs cleaner design. State the recommended path and why it fits the current scope.

## Goal-Driven Execution

- Convert requests into explicit, verifiable success criteria.
- For bugs, add or identify a test or reproduction before fixing when practical.
- For validation changes, cover invalid inputs and expected failures.
- For refactors, verify behavior before and after the change when possible.
- Continue iterating until the stated success criteria are met or a blocker is clearly explained.

## Project Documentation And Decision Logs

- Keep `docs/project-overview.md` updated when a meaningful feature, workflow, structure, permission, or governance change affects the project overview.
- Create one decision log entry under `docs/decisions/` for each meaningful development decision.
- Keep all durable repository documentation in English.

## Tests

Use test-driven development as the default for feature work, bug fixes, refactors, and behavior changes when automated tests are practical: write or identify the smallest failing test or reproduction first, confirm it fails for the expected reason, implement the smallest change to pass, then refactor with tests green. For documentation-only changes, configuration-only changes, throwaway prototypes, generated code, or work where automated tests are not practical, explain why TDD does not apply and use the closest validation available.

Cover happy paths, errors, relevant business rules, edge cases, and regressions. After any code change or implementation, use `presets/post-change-assessment.md`: run related tests or validation checks, perform a brief security and reliability assessment, and report results.

## Security and Reliability

Validate external input. Do not expose secrets, tokens, API keys, credentials, personal data, regulated data, or other sensitive data in logs. Do not change global config, CI/CD, authentication, permissions, or infrastructure without explaining why. Check auth boundaries, idempotency, race conditions, retries, timeouts, and observability for sensitive or async flows.

## Final Summary

Report what changed, why, main files, tests, manual validation, and risks.
