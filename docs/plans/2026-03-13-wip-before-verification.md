# WIP Before Verification Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Immediately checkpoint known task changes as WIP without confirmation, leave unrelated changes untouched, then amend fixes and finalize only after fresh checks pass.
**Architecture:** Centralize Git behavior in the `commit` skill, add a WIP exception/finalization gate to verification, and align subagent instructions. Preserve TDD and full-suite integration checks.
**Tech Stack:** Markdown Agent Skills, Git, Pi subagent pressure tests

---

- [ ] Task 1: Baseline the current skill behavior
  - Files: `/tmp/wip-skill-baseline-prompt.md`, `/tmp/wip-skill-baseline-output.txt`
  - Test first: create a pressure scenario with pre-existing unrelated changes, a deadline, and a request to test current task changes.
  - Verify RED: run `pi -p --no-session --no-skills @/tmp/wip-skill-baseline-prompt.md`; capture that the agent does not reliably describe unrelated changes, confirm scope, and create a WIP commit before testing.

- [ ] Task 2: Update the central commit workflow
  - Files: `/home/taras/.pi/agent/skills/mitsuhiko-pi-agent-stuff/skills/commit/SKILL.md`
  - Change: require status/diff review, description of unrelated/pre-existing changes, immediate `WIP:` creation without confirmation, automatic exclusion of unrelated changes, amendment before reruns, final subject cleanup after fresh verification, and preservation of WIP on failure.
  - Verify: `git -C /home/taras/.pi/agent/skills/mitsuhiko-pi-agent-stuff diff --check`.

- [ ] Task 3: Align verification and subagent workflows
  - Files: `/home/taras/.pi/agent/skills/superpowers/skills/verification-before-completion/SKILL.md`, `/home/taras/.pi/agent/skills/superpowers/skills/subagent-driven-development/SKILL.md`, `/home/taras/.pi/agent/skills/superpowers/skills/subagent-driven-development/implementer-prompt.md`
  - Change: permit only explicitly marked WIP checkpoints before checks; prohibit final commits before fresh verification; make implementers checkpoint known task changes immediately without confirmation, leave unrelated files untouched, amend fixes, and finalize after passing checks.
  - Verify: `git -C /home/taras/.pi/agent/skills/superpowers diff --check`.

- [ ] Task 4: Pressure-test the revised behavior
  - Files: modified skill files and `/tmp/wip-skill-green-prompt.md`
  - Verify GREEN: run a Pi subagent with the revised skills and the same multi-pressure scenario; require it to describe unrelated changes, create `WIP:` without confirmation, leave unrelated files untouched, amend fixes before reruns, and remove `WIP:` only after fresh verification.
  - Refactor: close any loopholes exposed by the subagent and rerun until compliant.

- [ ] Task 5: Finalize both repositories
  - Verify: run `git diff --check` in both skill repositories and inspect all changed skill text.
  - Commit sequence: create/retain WIP commits before verification, amend any fixes into them, then rename to concise Conventional Commit subjects after verification succeeds.
  - Report exact changed files, verification evidence, commit IDs, and any remaining WIP state.
