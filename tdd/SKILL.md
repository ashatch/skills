---
name: tdd
description: Guides test-driven development (write a failing test, make it pass, refactor) for production code changes. Use when changing behavior that needs durable, provable test coverage, such as features and bug fixes; skip for exploratory work.
---

Decide first whether you are exploring or changing settled production behavior.

- **Exploring** (spikes, prototypes, new classes whose shape is still unclear): work without tests; they cost time while the design is still moving.
- **Settled production behavior** (features, bug fixes, refactors of behavior others rely on): use the TDD cycle below.

## Cycle

1. **Confirm the behavior.** Identify it from approved requirements. If requirements are unclear, ask the user to clarify them or to review your proposed test scenarios before you implement anything.
2. **Write one focused test** for the intended behavior. For a bug fix, write a test that reproduces the bug.
3. **Red.** Check the test's expectation against the requirements, run it, and confirm it fails because the behavior is missing, not because of broken setup or a wrong expectation.
4. **Green.** Make the smallest code change that passes the test, then rerun it and the relevant existing tests.
5. **Refactor.** Clean up the code and test while keeping all tests passing.

Repeat for the next behavior.

## Verify the test

A test you wrote and ran yourself proves only that it ran, not that it checks the intended behavior. Ask the user to review the test when the behavior is important or the requirements were ambiguous.

See [the evidence](references/evidence.md) for research on TDD with agents.
