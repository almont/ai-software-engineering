# Frontend App Example

Recommended files to copy:

- `templates/new-project-AGENTS.md` to `AGENTS.md`.
- `templates/new-project-copilot-instructions.md` to `.github/copilot-instructions.md`.

Recommended presets:

- `presets/change-risk-calibration.md`.
- `presets/engineering-review.md`.
- `presets/post-change-assessment.md`.
- `presets/security-review.md`.
- `presets/test-review.md`.
- `presets/test-driven-implementation.md`.

Extra review focus:

- Broken authorization at UI boundaries.
- Sensitive data exposure in browser logs, telemetry, URLs, or local storage.
- Form validation.
- Error states.
- Accessibility.
- Regression tests for critical user flows.
