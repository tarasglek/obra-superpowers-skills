---
name: executing-plans
description: Use when executing or resuming an authorized implementation plan
---

# Executing Plans

Read the plan, then inspect current code, Git/index state, and verification evidence. Do not trust stale completion labels over the current tree. Preserve unrelated and staged work. Plan-only stops after the proposal; existing authorization persists within scope.

Per task: inspect current code and tests; **superpowers:test-driven-development** for code changes, including refactors; WIP-checkpoint before each check, amend fixes, drop `WIP:` only after a fresh pass; verify against requirements and mark verified only what the evidence supports; self-review the diff. Complex, major, or high-risk: independent review via **superpowers:requesting-code-review**, plus rollback and broader verification — if required review is unavailable, report readiness as blocked; self-review is not a substitute. Fixing after finalization: if that commit is HEAD and unpushed, re-mark it WIP, amend, reverify, re-finalize; else add a follow-up WIP commit. Never rewrite pushed history unasked.

Unexpected failures need **superpowers:systematic-debugging**; expected TDD RED is not a blocker. Pause for missing authority, unsafe actions, material scope change, or persistent blockers — state the evidence and smallest decision needed, and continue safe independent work. Never conceal failures or call implemented work verified.

Finish with changes, actual verification and its limits, remaining work, and commit state. Completion alone does not authorize push, merge, deletion, or deployment. Progress updates per **superpowers:using-superpowers**.
