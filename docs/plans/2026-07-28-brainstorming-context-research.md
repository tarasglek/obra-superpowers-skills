# Brainstorming Context Research Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Make substantive brainstorming inspect prior local, session, forge, and external work before design.
**Architecture:** Add one conditional context-research item to the existing brainstorming workflow; no new skill.
**Tech Stack:** Markdown Agent Skill, Git, Pi sessions, `gh`/`glab`, Brave Search

---

- [ ] Capture RED baseline
  - Evidence: `/tmp/brainstorming-research-baseline.out`
  - Result: current skill checks files/docs/recent Git only; omits Pi sessions, forge, and external prior art.

- [ ] Add minimal research requirement
  - File: `skills/brainstorming/SKILL.md`
  - Change checklist and context guidance for substantive/unfamiliar work.
  - Require concise findings synthesis; missing tools/auth do not block.

- [ ] Verify GREEN
  - Run same pressure prompt with revised skill.
  - Expect Git history, Pi sessions, forge issues/PRs or MRs, Brave prior art, then clarification/design.
  - Run `git show --check HEAD` and finalize WIP only after pass.
