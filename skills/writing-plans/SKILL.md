---
name: writing-plans
description: Use when asked for an implementation plan or when multi-step work needs sequencing and coordination
---

# Writing Plans

Smallest plan that makes safe execution clear. Default 3-5 checklist bullets, under 150 words; expand only for real complexity. Trivial authorized change: no plan.

Inspect code first; reuse existing solutions. Ask only what changes scope, correctness, safety, or authorization. Mark uninspected paths and commands as assumptions.

Each bullet: change + paths, ordering if it matters, verification command and expected result (RED/GREEN for code changes, including refactors). Add rollback, manual checks, or an independent-review gate only where risk warrants.

Plan-only: present and stop. Authorized: execute via **superpowers:executing-plans**. Save a file only if requested or resumable. Checkpoints, verification, and progress updates: per **superpowers:using-superpowers**.
