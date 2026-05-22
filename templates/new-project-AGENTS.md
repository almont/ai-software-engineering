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
- Use design patterns only when they simplify the solution.
- Avoid overengineering.
- Preserve backward compatibility unless explicitly requested.

## Before Coding

Understand the project structure, existing patterns, architecture, naming conventions, folder organization, frameworks, libraries, and test style first. Follow the existing pattern unless there is a clear reason to propose a change. Then briefly explain the problem, files expected to change, implementation strategy, tests, and risks.

For non-trivial changes, include a brief trade-off analysis covering simplicity vs flexibility, short-term delivery vs long-term maintenance, performance vs readability, coupling vs duplication, operational safety vs implementation speed, and backward compatibility vs cleaner design. State the recommended path and why it fits the current scope.

## Tests

Cover happy paths, errors, relevant business rules, edge cases, and regressions. Run related tests after implementation and report results.

## Security and Reliability

Validate external input. Do not expose secrets, tokens, API keys, credentials, personal data, or payment data in logs. Do not change global config, CI/CD, authentication, permissions, or infrastructure without explaining why. Check auth boundaries, idempotency, race conditions, retries, timeouts, and observability for sensitive or async flows.

## Final Summary

Report what changed, why, main files, tests, manual validation, and risks.
