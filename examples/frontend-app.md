# Frontend App Example

Recommended files to copy:

- `templates/new-project-CLAUDE.md` to `CLAUDE.md`.

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
- Browser-based validation for changed UI flows, routing, forms, visual layout, and responsive behavior.
- Playwright, Cypress, or another end-to-end framework for affected flows when the project already uses one.
