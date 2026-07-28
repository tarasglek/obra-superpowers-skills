# WIP Before Verification Design

## Goal

Preserve every task-related change in a draft commit before running tests or other verification. Fold verification fixes into that draft and publish a clean final commit only after fresh verification succeeds.

## Workflow

1. Inspect `git status` and the relevant diff.
2. Describe unrelated or pre-existing changes before any necessary clarification.
3. Immediately commit known task changes with `WIP: <conventional subject>` without asking for confirmation.
4. Leave unrelated or ambiguous changes untouched and proceed with verification; clarify only if no safe known-task scope can be identified.
5. After a failing check, make the necessary fix and amend it into the WIP commit before rerunning the check.
6. After fresh verification passes, amend the subject to remove `WIP:` and retain a normal Conventional Commit.
7. If verification cannot pass, leave the commit marked `WIP:` and report the evidence.
8. Never include unrelated or pre-existing changes unless explicitly requested.

The workflow does not weaken TDD: failing and passing tests still run in their normal order. It changes the Git checkpoint around each run so the worktree's task changes are committed first.

## Skill Changes

- Make the central `commit` skill own scope confirmation, pre-existing-change reporting, WIP creation, amendments, and finalization.
- Make `verification-before-completion` distinguish a permitted WIP checkpoint from a forbidden final commit without verification.
- Update subagent implementation instructions so implementers checkpoint before each test run and finalize only after verification.
- Keep full-suite requirements in branch-finishing and parallel-integration skills; those checks happen after the WIP checkpoint.

## Failure Handling

A failed or interrupted verification leaves a clearly marked WIP commit. The agent reports the failed command and does not imply completion. Unrelated changes remain unstaged unless the user explicitly includes them.
