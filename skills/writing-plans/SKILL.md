---
name: writing-plans
description: Use when asked for an implementation plan or when multi-step work needs sequencing and coordination
---

# Writing Plans

Write the smallest plan that makes safe execution clear. Prefer a short inline checklist; expand for real complexity, not a fixed template or word count. A trivial authorized change needs no separate plan.

## Plan Content

Inspect relevant state and reuse existing solutions. Ask only questions that materially affect scope, correctness, safety, or authorization. Do not invent exact paths or commands when the repository has not been inspected; label those as assumptions or discovery steps.

Each coherent task should identify:
- The intended change and affected paths.
- Dependencies or important ordering constraints.
- Verification commands and expected results, including test-first steps for code changes; for refactors, the tests that must stay green.

Include design decisions, failure handling, rollback/recovery, manual checks, and broader verification where risk warrants them. Complex, major, or high-risk changes need independent review; identify where it gates readiness. Routine changes need focused tests and self-review, not automatic reviewer dispatch.

Example:

```markdown
- [ ] Fix boundary handling in `src/limit.ts`; add regression in `tests/limit.test.ts`.
  - RED: `npm test -- tests/limit.test.ts` fails on the boundary case.
  - GREEN: minimal fix; rerun the focused suite, then relevant regression checks.
```

**Checkpoint policy applies throughout:** use **commit** to WIP-checkpoint each task edit before its next test or verification; amend fixes before reruns and finalize only after fresh successful verification. Do not repeat these mechanics under every task, but never omit them from execution. Use **superpowers:test-driven-development** and **superpowers:verification-before-completion** as applicable.

## Delivery

- **Plan-only / proposal-only:** present the plan and stop. Do not implement or add repository files unless requested.
- **Execution already authorized:** proceed within scope using **superpowers:executing-plans** when useful. Do not ask again merely because the plan is ready.
- Save a plan only when requested or useful for long/resumable work. No mandatory filename, header, design document, or separate session handoff.

Follow **superpowers:using-superpowers** for user updates and safety boundaries. Avoid skill announcements, long code blocks, repeating requirements, teaching the whole codebase, or prescribing details better discovered during implementation.
