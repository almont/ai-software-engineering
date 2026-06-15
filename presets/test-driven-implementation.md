# Test-Driven Implementation Preset

Use this preset for feature work, bug fixes, refactors, and behavior changes where automated tests are practical.

Do not use this preset for documentation-only changes, configuration-only changes, throwaway prototypes, generated code, or work where automated tests are not practical. In those cases, explain why TDD does not apply and use the closest validation available.

## Workflow

1. Identify the behavior that must change.
2. Write or identify the smallest failing test or reproduction first.
3. Run it and confirm it fails for the expected reason.
4. Implement the smallest change needed to pass.
5. Run the focused test and the related test suite.
6. Refactor only after the tests are green.
7. Run applicable validation checks.
8. Perform a brief security and reliability assessment.

## Expectations

- Prefer behavior-focused tests over implementation-detail tests.
- Keep each test focused on one behavior.
- Use mocks only when external dependencies, time, network, queues, or storage boundaries make them necessary.
- Do not broaden scope while moving from red to green.
- If the existing project has no test framework or the behavior cannot be tested automatically, state the constraint, create the smallest practical reproduction or validation path, and recommend follow-up test infrastructure separately.

## Final Summary

Report:

- The failing test or reproduction used first.
- The expected failure observed.
- The implementation change made.
- The tests and validation checks that passed.
- Any TDD exceptions or residual test gaps.
- Security and reliability assessment results.
