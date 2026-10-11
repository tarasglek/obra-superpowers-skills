---
name: brainstorming
description: Use when a request leaves consequential design choices, requirements, or trade-offs unresolved
---

# Resolve Design Uncertainty

Resolve what matters before implementation; do not turn a clear authorized task into a design-approval ceremony.

Inspect relevant code, constraints, and existing solutions; research further only to settle consequential uncertainty. Identify decisions affecting correctness, scope, safety, or authorization — if none remain and execution is authorized, proceed without an approval round. Ask the smallest useful question set, recommending a default where safe. Never guess retention rules, destructive intent, or deployment authority. For complex, major, or high-risk work, make architecture, failure modes, and recovery explicit, and arrange independent review before declaring readiness.

Plan-only: propose and stop. Authorized: proceed within scope, using **superpowers:writing-plans** only when a checklist helps. Material ambiguity or new consequential scope: pause that work and continue safe independent work. A design document is optional.
