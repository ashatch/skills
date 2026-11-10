---
name: implement
description: Implement requested software changes by inspecting the project, making focused edits, and verifying behavior. Use when asked to build, modify, or fix code.
---

# Implement software changes

## Understand the change

- Inspect the relevant code, tests, configuration, and repository status before editing. Follow existing patterns and preserve unrelated working-tree changes.
- Confirm the requested behavior and scope. Ask the user when a material design or behavior choice is unresolved; otherwise make the smallest reasonable assumptions and state them when useful.
- Identify the most relevant existing tests and checks before implementation.
- Choose a test strategy based on how settled the behavior is. For production features and bug fixes with defined expected behavior, follow the `tdd` skill's test-first workflow. For exploratory spikes or prototypes whose design is still changing, do not force tests prematurely; validate the result appropriately and add tests when the behavior settles.

## Make the change

- Implement the root cause or requested behavior with the smallest coherent change. Reuse existing helpers and update directly dependent call sites, types, and documentation.
- Avoid unrelated cleanup, unnecessary abstractions, and dependencies the request does not need.
- Handle errors explicitly and preserve existing behavior outside the requested change.

## Refactor

- After the intended behavior works and relevant tests pass, refactor when it improves clarity, reduces duplication, or better fits established project patterns.
- Keep refactoring behavior-preserving and incremental. Do not mix unrelated cleanup or behavior changes into the refactor.
- Rerun relevant tests after each meaningful step. If a test fails, diagnose the change rather than weakening the test or silently changing behavior.
- For a refactor-only request on settled production code, follow the `tdd` skill: add focused tests for important behavior that is not already covered before changing the implementation.

## Verify and report

- For settled behavior, run the focused tests and checks identified before implementation. For exploratory work, use the least costly appropriate validation without adding tests for unsettled behavior. Run applicable formatting, lint, type, or build checks when the project provides them.
- Review the final diff for accidental or out-of-scope changes. Report the meaningful change and checks run; state clearly if a check failed or could not be run.
