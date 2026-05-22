# Pull Request Review Request

Review this PR as a staff engineer.

Focus on:

- Code quality.
- Security.
- Reliability.
- Tests.
- Observability.
- Backward compatibility.
- Operational risk.
- Trade-offs in architecture or implementation choices.

If this change touches payment, billing, webhooks, async processing, or data consistency, also focus on idempotency, duplicate processing, race conditions, retries, timeouts, auditability, and sensitive data exposure.

Return findings first, grouped by severity, with concrete file references and suggested fixes.

Also explain what the chosen approach optimizes for and what it makes harder when the trade-off matters.
