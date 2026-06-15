# Post-Change Assessment Preset

Use this preset after code changes, feature implementation, bug fixes, refactors, behavior changes, or meaningful configuration changes.

Scale the depth of the assessment to the risk of the change. Documentation-only changes can use documentation validation and a brief risk note.

## Checklist

1. Tests and validation
   - List focused tests run.
   - List broader tests, lint, typecheck, build, or manual validation run.
   - If anything could not run, explain why and what risk remains.

2. Security
   - Check external input validation.
   - Check authentication and authorization boundaries.
   - Check sensitive data exposure in logs, telemetry, URLs, errors, and persistence.
   - Check injection, SSRF, unsafe file handling, unsafe uploads, insecure deserialization, and webhook spoofing where applicable.

3. Reliability
   - Check idempotency for retryable, webhook, async, payment, billing, or external integration flows.
   - Check duplicate processing, race conditions, partial failures, retries, timeouts, fallbacks, dead-letter behavior, and data consistency where applicable.

4. Compatibility and operations
   - Check backward compatibility.
   - Check rollout and rollback expectations for risky changes.
   - Check observability for important business events and failure points.

## Output

Return:

- Tests and validation run.
- Security assessment.
- Reliability assessment.
- Compatibility, rollout, and observability notes.
- Residual risks or follow-up work.
