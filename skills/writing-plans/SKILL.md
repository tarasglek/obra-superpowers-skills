---
name: writing-plans
description: Use when you have a spec or requirements for a multi-step task, before touching code
---

# Writing Plans

## Overview

Write **brief checklist-style implementation plans**. Plans should be easy to scan, easy to execute, and specific enough that another agent can follow them without guessing.

**Default style:** concise checklist, not long prose.

**Announce at start:** "I'm using the writing-plans skill to create the implementation plan."

**Save plans to:** `docs/plans/YYYY-MM-DD-<feature-name>.md`

## Plan Header

Every plan starts with:

```markdown
# [Feature Name] Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** [one sentence]
**Architecture:** [1-2 short sentences]
**Tech Stack:** [key crates/tools]

---
```

## Checklist Format

Prefer this format:

```markdown
- [ ] Task 1: [short task name]
  - Files: `src/foo.rs`, `tests/foo_test.rs`
  - Test first: add/modify `[specific test]`
  - Verify RED: `cargo test ...` should fail because `[reason]`
  - Implement: `[specific minimal change]`
  - Verify GREEN: `cargo test ...`

- [ ] Task 2: [short task name]
  - Files: `src/bar.rs`
  - Change: `[specific change]`
  - Verify: `cargo check ...`
```

## Required Detail

Keep plans short, but include:

- Exact file paths
- Exact commands for verification
- Expected failure/pass result for tests
- TDD steps for behavior changes
- Hardware/manual checks when needed
- Any important ordering constraints

## What to Avoid

- Long code blocks unless essential
- Teaching the whole codebase
- Repeating obvious mechanics
- Commit steps unless explicitly requested
- Over-specifying implementation details that are better discovered while coding

## Good Task Size

Each checklist item should be one coherent chunk, usually 5-20 minutes:

- Good: "Add CLI parser variants and host tests"
- Good: "Remove boot-time WiFi spawn"
- Bad: "Implement all WiFi management"
- Bad: "Change one line" repeated 20 times

## Handoff

After saving the plan, say where it was written and offer to execute it.
