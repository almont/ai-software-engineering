# Change Risk Calibration Preset

Use this preset before planning or implementing work to choose the right level of process and validation.

## Levels

### Low Risk

Examples: documentation-only changes, copy edits, comments, and non-behavioral examples.

Expected rigor:

- Keep the change surgical.
- Run documentation or formatting validation where applicable.
- Explain why TDD does not apply.

### Medium Risk

Examples: ordinary feature work, bug fixes, refactors, validation changes, and UI behavior changes.

Expected rigor:

- Use test-driven development when automated tests are practical.
- Run focused tests plus related checks.
- For frontend UI behavior changes, include browser-based validation for affected flows when practical.
- Perform the post-change assessment.

### High Risk

Examples: authentication, authorization, payment, billing, webhooks, async processing, external integrations, migrations, permissions, infrastructure, and data consistency changes.

Expected rigor:

- Resolve ambiguity before implementation.
- Use TDD or a clear reproduction when practical.
- Run focused and broader validation.
- For high-risk frontend flows, run related Playwright, Cypress, or other end-to-end checks when the project uses them and they are practical.
- Perform security and reliability review.
- Cover rollout, rollback, observability, and compatibility.

## Output

State:

- Risk level.
- Why that level applies.
- Required tests and validation.
- Required security, reliability, rollout, or review steps.
