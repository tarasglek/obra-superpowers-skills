---
name: using-superpowers
description: Use when starting a conversation or deciding which workflow skills apply
---

# Using Skills

Remove ceremony, not quality controls. Match process to uncertainty and risk; respect the user's authorized scope.

Check available skill descriptions before acting; load requested and applicable ones, using current instructions rather than memory. Do not load every remotely related skill, and do not announce internal skill activation.

## Choose the Smallest Safe Workflow

- Clear, routine, authorized task: inspect relevant state, use focused tests and self-review, report results. No design approval or plan document.
- Unresolved consequential requirements: **superpowers:brainstorming** before affected implementation.
- Multi-step work needing coordination: **superpowers:writing-plans**, then **superpowers:executing-plans**. A short inline checklist usually suffices.
- Complex, major, or high-risk changes: make design decisions and trade-offs explicit; require independent review via **superpowers:requesting-code-review**, rollback planning, and broader verification. If review is unavailable, report readiness as blocked — self-review is not equivalent.
- Plan-only or proposal-only: present and stop. A plan is not execution authorization.

Do not impose mandatory documents, task-tool entries, fixed batches, handoffs, or repeated approvals inside authorized scope. Preserve explicit approval for ambiguous scope, destructive actions, deployment, and other safety boundaries.

## Quality and Checkpoints

Preserve user work, including unrelated staged changes. Use **superpowers:test-driven-development** for code changes, including refactoring, and **superpowers:systematic-debugging** for unexpected failures; brevity is not permission to skip either.

**REQUIRED:** Use **commit** and **superpowers:verification-before-completion**. Checkpoint known task changes as WIP before tests or verification, without routine confirmation. Amend later edits and fixes into WIP before rerunning checks; remove `WIP:` only after fresh successful verification. Exclude unrelated changes. Checkpointing does not authorize push, merge, deletion, or deployment.

## User Progress Contract

- Start substantive execution with a short scope and next-action update.
- Update at meaningful milestones, failures, blockers, or scope changes. Say up front when a call will block for a while; give a brief heartbeat after each long tool or agent run.
- Use brief **Done / Left / Blocked**, omitting empty fields. Distinguish verified results from merely implemented changes, and say when nothing new is verified.
- Finish with completed work, actual verification and its limits, and remaining work.

Updates are required, not optional ceremony. Do not narrate every tool call, dump routine logs, or turn updates into approval waits.
