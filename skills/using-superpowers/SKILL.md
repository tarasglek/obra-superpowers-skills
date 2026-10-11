---
name: using-superpowers
description: Use when starting a conversation or deciding which workflow skills apply
---

# Using Skills

Remove ceremony, not quality controls. Match process to uncertainty and risk; respect the user's authorized scope.

## Load What Applies

Check available skill descriptions before acting. Load requested and applicable skills using the platform's skill tool, or read their files when no skill tool exists. Use current instructions, not memory. Resolve consequential uncertainty about applicability by reading the skill; do not load every remotely related skill.

Use process guidance before domain implementation guidance. Required safety sub-skills still apply; a cross-reference alone does not require starting an unrelated workflow. Do not announce internal skill activation.

## Choose the Smallest Safe Workflow

- Clear, routine, authorized task: inspect relevant state, use focused tests and self-review, then report results. No separate design approval or plan document needed.
- Consequential unresolved requirements: use **superpowers:brainstorming** to resolve them before affected implementation.
- Multi-step work needing coordination: use **superpowers:writing-plans**; execute or resume with **superpowers:executing-plans**. A short inline checklist usually suffices.
- Complex work: make design decisions and trade-offs explicit. Complex, major, or high-risk changes require independent review, rollback/recovery planning, and broader verification proportionate to impact. Use **superpowers:requesting-code-review**; if review is unavailable, report readiness as blocked rather than treating self-review as equivalent.
- Plan-only or proposal-only requests: present the proposal and stop. A plan is not execution authorization.

In the core workflow, do not impose mandatory documents, task-tool entries, fixed batches, handoffs, or repeated approvals inside already authorized scope; use them only when requested or genuinely useful. A deliberately selected specialized workflow may retain its own tracking and review gates. Preserve explicit approval requirements for ambiguous scope, destructive actions, deployment, or other safety/authorization boundaries.

## Quality and Checkpoints

Preserve user work, including unrelated staged changes. Follow **superpowers:test-driven-development** for code changes, including refactoring, and **superpowers:systematic-debugging** for unexpected failures; brevity is not permission to skip either.

**REQUIRED:** Use **commit** and **superpowers:verification-before-completion**. Checkpoint known task changes as WIP before tests or verification, without routine confirmation. Amend later edits/fixes into WIP before rerunning checks; remove `WIP:` only after fresh successful verification. Exclude unrelated changes. Checkpoint permission does not authorize push, merge, deletion, or deployment.

## User Progress Contract

- Start substantive execution with a short scope and next-action update.
- During longer work, update at meaningful milestones, unexpected failures, blockers, or scope changes. After roughly 2 minutes of silence, give a brief heartbeat; before a call that will block longer than that, say so, and report when it returns.
- Use brief **Done / Left / Blocked**, or equivalent natural wording; omit empty fields. Distinguish verified results from merely implemented changes. Say when nothing new is verified.
- Final update: completed work, actual verification and its limits, remaining work/blockers.

Updates are required, not optional ceremony. Do not narrate every tool call, dump routine logs, or turn progress updates into approval waits. Continue within scope unless a real boundary requires a decision.
