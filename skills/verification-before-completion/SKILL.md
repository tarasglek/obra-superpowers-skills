---
name: verification-before-completion
description: Use when task changes exist before running tests or checks, or when about to claim work is complete, fixed, or passing, finalize a commit, or create a PR
---

# Verification Before Completion

## Overview

Claiming work is complete without verification is dishonesty, not efficiency.

**Core principle:** Checkpoint changes first; evidence before claims and final commits, always.

**REQUIRED SUB-SKILL:** Use `commit` to create and maintain the WIP checkpoint.

**Violating the letter of this rule is violating the spirit of this rule.**

## The Iron Laws

```
NO VERIFICATION RUN WITH UNCOMMITTED TASK CHANGES
NO COMPLETION CLAIMS OR FINAL COMMITS WITHOUT FRESH VERIFICATION EVIDENCE
```

A commit whose subject starts with `WIP:` is a checkpoint, not a completion claim. It MUST exist before verification when task changes are present—even before lightweight checks such as `git diff --check`. Do not insert `git diff --cached --check` between staging and the WIP commit. Fixes MUST be amended into WIP before rerunning verification. Remove `WIP:` only after fresh verification passes.

If you haven't run the verification command in this message, you cannot claim it passes.

## The Gate Function

```
BEFORE running verification or claiming status:

1. INSPECT: Identify known task changes and unrelated/pre-existing changes.
2. REPORT: Describe unrelated/pre-existing changes before any necessary clarification.
3. CHECKPOINT: Immediately commit known task changes as WIP without confirmation; exclude unrelated or ambiguous changes.
4. IDENTIFY: What full command proves the intended claim?
5. RUN: Execute it fresh and completely.
6. READ: Check full output, exit code, and failure count.
7. IF FAILED: State evidence; amend each fix into WIP before rerunning.
8. IF PASSED: Amend the subject to remove WIP, then state the claim with evidence.

Skip any step = unverified work
```

## Common Failures

| Claim | Requires | Not Sufficient |
|-------|----------|----------------|
| Tests pass | Test command output: 0 failures | Previous run, "should pass" |
| Linter clean | Linter output: 0 errors | Partial check, extrapolation |
| Build succeeds | Build command: exit 0 | Linter passing, logs look good |
| Bug fixed | Test original symptom: passes | Code changed, assumed fixed |
| Regression test works | Red-green cycle verified | Test passes once |
| Agent completed | VCS diff shows changes | Agent reports "success" |
| Requirements met | Line-by-line checklist | Tests passing |

## Red Flags - STOP

- Using "should", "probably", "seems to"
- Expressing satisfaction before verification ("Great!", "Perfect!", "Done!", etc.)
- About to create a final commit/push/PR without verification
- Asking for routine commit-scope confirmation instead of checkpointing and proceeding
- Running `git diff --cached --check` or another check immediately before the WIP commit
- About to run verification while task changes are outside a WIP commit
- Treating a WIP checkpoint as a success claim
- Trusting agent success reports
- Relying on partial verification
- Thinking "just this once"
- Tired and wanting work over
- **ANY wording implying success without having run verification**

## Rationalization Prevention

| Excuse | Reality |
|--------|---------|
| "Should work now" | RUN the verification |
| "I'm confident" | Confidence ≠ evidence |
| "Just this once" | No exceptions |
| "Linter passed" | Linter ≠ compiler |
| "Agent said success" | Verify independently |
| "I'm tired" | Exhaustion ≠ excuse |
| "Partial check is enough" | Partial proves nothing |
| "Different words so rule doesn't apply" | Spirit over letter |

## Key Patterns

**Tests:**
```
✅ [Run test command] [See: 34/34 pass] "All tests pass"
❌ "Should pass now" / "Looks correct"
```

**Regression tests (TDD Red-Green):**
```
✅ Write → Run (pass) → Revert fix → Run (MUST FAIL) → Restore → Run (pass)
❌ "I've written a regression test" (without red-green verification)
```

**Build:**
```
✅ [Run build] [See: exit 0] "Build passes"
❌ "Linter passed" (linter doesn't check compilation)
```

**Requirements:**
```
✅ Re-read plan → Create checklist → Verify each → Report gaps or completion
❌ "Tests pass, phase complete"
```

**Agent delegation:**
```
✅ Agent reports success → Check VCS diff → Verify changes → Report actual state
❌ Trust agent report
```

## Why This Matters

From 24 failure memories:
- your human partner said "I don't believe you" - trust broken
- Undefined functions shipped - would crash
- Missing requirements shipped - incomplete features
- Time wasted on false completion → redirect → rework
- Violates: "Honesty is a core value. If you lie, you'll be replaced."

## When To Apply

**ALWAYS before:**
- Running tests, builds, linters, or other verification with task changes present
- ANY variation of success/completion claims
- ANY expression of satisfaction
- ANY positive statement about work state
- Finalizing a WIP commit, PR creation, task completion
- Moving to next task
- Delegating to agents

**Rule applies to:**
- Exact phrases
- Paraphrases and synonyms
- Implications of success
- ANY communication suggesting completion/correctness

## The Bottom Line

**No shortcuts for verification.**

Run the command. Read the output. THEN claim the result.

This is non-negotiable.
