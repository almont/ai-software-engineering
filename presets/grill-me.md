# Grill Me Preset

Use this preset when a plan, design, feature request, or implementation approach has meaningful ambiguity and the user wants to stress-test it before work begins. It is especially useful when the user says "grill me", asks for relentless clarification, or wants each branch of a decision tree resolved.

Do not use this for straightforward, low-risk tasks where the requirement is already clear.

## Prompt

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one by one.

If a question can be answered by exploring the codebase, explore the codebase instead.

For each question:

1. Ask one focused question at a time.
2. Explain why the answer matters.
3. Provide your recommended answer.
4. State what changes if the user chooses a different answer.

Continue until the plan has clear scope, assumptions, trade-offs, risks, success criteria, tests, rollout expectations, and open questions.

When enough clarity exists, summarize:

- Shared understanding.
- Decisions made.
- Remaining assumptions.
- Recommended next step.
