---
name: using-git-worktrees
description: Use when starting feature work that needs isolation from the current workspace
---

# Using Git Worktrees

## Overview

Git worktrees isolate feature work while sharing repository objects.

**Core principle:** Worktrees always live outside repositories under the global
Superpowers worktree directory. Never offer or create a project-local worktree.

**Announce at start:** "I'm using the using-git-worktrees skill to set up an isolated workspace."

## Location

Always use:

```text
~/.cache/superpowers/worktrees/<project-name>/<branch-name>
```

Do not inspect, offer, or create `.worktrees/` or `worktrees/` inside a project.
Do not ask the user to choose a location. Create the global parent automatically.
No `.gitignore` check is needed because the worktree is outside the repository.

## Creation

```bash
project=$(basename "$(git rev-parse --show-toplevel)")
branch=feature/example
path="$HOME/.cache/superpowers/worktrees/$project/$branch"
mkdir -p "$(dirname "$path")"
git worktree add "$path" -b "$branch"
cd "$path"
```

Choose a short descriptive branch name. If the branch or path already exists,
inspect existing worktrees and reuse the matching worktree only when it clearly
belongs to the same task; otherwise choose a distinct branch name.

## Setup and Baseline

Auto-detect only relevant project setup:

```bash
test ! -f package.json || npm install
test ! -f Cargo.toml || cargo build
```

Use the project's documented package manager; never substitute `pip` when a
project uses `uv`.

Run the project's baseline tests before editing. If they fail, report exact
failures and ask whether to investigate or proceed. If they pass, report:

```text
Worktree ready at <absolute-path>
Baseline: <tests>, 0 failures
```

## Quick Reference

| Situation | Action |
|---|---|
| Any repository | Use the global Superpowers path |
| Global parent absent | Create it automatically |
| Matching worktree exists | Verify and reuse it |
| Baseline fails | Report and ask before editing |

## Red Flags

Never:

- offer or create a project-local worktree;
- ask where to place a worktree;
- edit before baseline verification;
- proceed after a failing baseline without approval.

## Integration

After implementation, **REQUIRED SUB-SKILL:** Use
`superpowers:finishing-a-development-branch`.
