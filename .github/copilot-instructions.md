# GitHub Copilot Instructions

Act with Staff Engineer judgment: consider scale, operational risk, long-term maintenance, and system sustainability. Keep repository documentation in English.

Follow the repository's existing architecture, naming, folder structure, frameworks, libraries, and test style. Preserve existing patterns unless there is a clear reason to propose a change.

Prioritize clarity, automated tests, low coupling, and future maintenance. Keep code simple, explicit, and easy to review. Use DDD only for relevant business logic and design patterns only when they simplify the solution. Avoid overengineering.

Keep changes scoped to the request and avoid broad refactors, cosmetic churn, unnecessary renames, or out-of-scope changes. List useful follow-up improvements separately instead of implementing them without need.

For non-trivial changes, include trade-off reasoning in comments, PR descriptions, or review notes when useful. Consider simplicity vs flexibility, short-term delivery vs long-term maintenance, performance vs readability, coupling vs duplication, operational safety vs speed, and backward compatibility vs cleaner design.

For implementation work:

- Add or update tests for happy paths, errors, business rules, edge cases, and regressions.
- Validate external input.
- Avoid logging secrets, tokens, credentials, CPF/CNPJ, emails, payment data, or sensitive user data.
- Do not change global config, CI/CD, authentication, permissions, or infrastructure without explaining why.
- Preserve backward compatibility unless the task explicitly changes behavior.
- Consider idempotency, duplicate processing, race conditions, retries, timeouts, and data consistency for payment, billing, webhook, async, and integration flows.
- Prefer meaningful logs for important business events and failures, following existing correlation ID patterns.

For reviews, focus on security, reliability, observability, missing tests, backward compatibility, customer impact, money movement, data consistency, and important trade-offs. Return concrete findings with file references and suggested fixes.
