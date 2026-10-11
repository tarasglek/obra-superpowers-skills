---
name: brainstorming
description: Use when a request leaves consequential design choices, requirements, or trade-offs unresolved
---

# Resolve Design Uncertainty

Resolve what matters before implementation. Do not turn a clear authorized task into a design-approval ceremony.

1. Inspect relevant code, constraints, and existing solutions. Research history, prior work, or primary sources when needed to resolve consequential uncertainty; do not require a sweep of every source for every task.
2. Identify decisions that affect correctness, scope, safety, or authorization. If none remain and execution is authorized, proceed without a separate approval round.
3. Ask the smallest useful question set for material unknowns. Recommend a default where safe; compare alternatives only when their trade-offs matter. Do not guess retention rules, destructive intent, or deployment authority.
4. Summarize the chosen behavior, constraints, and verification briefly. For complex/high-risk work, make architecture, failure modes, recovery, and important trade-offs explicit; arrange independent review before declaring readiness.

## Proceed or Stop

- **Plan-only / proposal-only:** provide the proposal and stop. Do not implement, create repository artifacts, or commit a design merely because planning occurred.
- **Authorized execution:** proceed within the agreed scope. Use **superpowers:writing-plans** only when a multi-step checklist helps execution; no mandatory handoff.
- **Material ambiguity or new consequential scope:** pause the affected work for a decision. Continue independent, already authorized work when safe.

A design document is optional: save one when requested or useful for complex/resumable work, not by default. Any resulting task edits still follow the WIP/checkpoint and verification policies; optional documentation does not make checkpoints optional.

Follow the user progress contract in **superpowers:using-superpowers**. Avoid skill announcements, repeated section approvals, forced alternatives, and documenting decisions that are already clear. Keep tests, safety checks, and evidence-backed claims.
