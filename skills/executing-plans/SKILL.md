---
name: executing-plans
description: Use when executing or resuming an authorized implementation plan
---

# Executing Plans

Execute in dependency order, with evidence and recoverable checkpoints. Progress reports are not automatic approval gates.

## Start or Resume

Read the plan and inspect current code, Git/index state, and available verification evidence. Reconcile completed work, stale assumptions, partial implementation, and blockers; do not trust yesterday's completion labels over the current tree. Preserve unrelated work, including staged changes.

Confirm that execution is authorized. A plan-only or proposal-only request stops after the proposal. Existing authorization persists within scope: do not restart design approval when resuming. Ask only about consequential ambiguity, changed outcomes, unsafe actions, or missing authority.

Follow the **User Progress Contract in superpowers:using-superpowers**: start with scope/next action, report milestones and failures, give a heartbeat after roughly 2 minutes of silence, and finish with verified results and remaining work. Do not announce skill use or narrate every tool call.

## Execute and Verify

For each coherent task:
1. Inspect the relevant implementation and tests. Adapt incidental details to current evidence without silently changing agreed outcomes.
2. Follow **superpowers:test-driven-development** for code changes, including refactoring. Use appropriate checks for non-code work; do not claim those prove runtime behavior.
3. **Use commit:** checkpoint known task changes as WIP before tests or verification, without routine confirmation. Exclude unrelated changes and preserve their index state. Amend later edits and fixes into WIP before each rerun.
4. Follow **superpowers:verification-before-completion**: run the relevant checks, read full results, and compare implementation against requirements. Mark verified only what the evidence supports. Remove `WIP:` only after fresh successful verification; leave it if required checks cannot pass. Fixes after finalization, including review-driven fixes: if the finalized commit is HEAD and unpushed, re-mark it as WIP, amend, reverify, then re-finalize; otherwise follow **commit** for a follow-up WIP commit. Never rewrite pushed history without an explicit request.
5. Self-review the scoped diff. For complex, major, or high-risk changes, require independent review through **superpowers:requesting-code-review**, explicit recovery/rollback, and broader verification. Resolve critical/important findings and reverify fixes. If required review is unavailable, report readiness as blocked; self-review is not a substitute.

No fixed three-task batches, mandatory task tool, or routine feedback waits. Use checkpoints at meaningful boundaries and continue authorized work.

## Failure and Scope Changes

Unexpected test failures require **superpowers:systematic-debugging**, not automatic escalation of every failing test. Report the failure, investigate, and fix ordinary in-scope problems; checkpoint fixes before rechecking. Expected TDD RED is not a blocker.

Pause affected work for missing authority, unsafe actions, material scope changes, critical plan gaps, or persistent blockers. State the evidence and smallest decision/help needed. Continue safe independent work when possible. Never conceal failures to meet a deadline or call implemented work verified.

## Finish or Pause

Report changes, actual verification and limits, remaining work/blockers, and checkpoint/commit state. For resumable work retain only useful decisions, progress, blockers, and next checks; no mandatory document.

Use **superpowers:finishing-a-development-branch** only when integration or cleanup is requested or a branch decision is needed. Completion alone does not authorize push, merge, deletion, or deployment, and does not require an integration-options menu.
