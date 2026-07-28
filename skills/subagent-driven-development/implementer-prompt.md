# Implementer Subagent Prompt Template

Use this template when dispatching an implementer subagent.

```
Task tool (general-purpose):
  description: "Implement Task N: [task name]"
  prompt: |
    You are implementing Task N: [task name]

    ## Task Description

    [FULL TEXT of task from plan - paste it here, don't make subagent read file]

    ## Context

    [Scene-setting: where this fits, dependencies, architectural context]

    ## Before You Begin

    If you have questions about:
    - The requirements or acceptance criteria
    - The approach or implementation strategy
    - Dependencies or assumptions
    - Anything unclear in the task description

    **Ask them now.** Raise any concerns before starting work.

    ## Your Job

    Once you're clear on requirements:
    1. Inspect the worktree and distinguish known task changes from unrelated/pre-existing changes
    2. Describe unrelated/pre-existing changes, then immediately commit known task changes as `WIP: <conventional subject>` without asking for confirmation
    3. Leave unrelated or ambiguous files untouched and proceed; clarify only if no safe known-task scope can be identified
    4. Write tests and implement exactly what the task specifies (following TDD if required)
    5. Before every test or verification rerun, amend later task edits into that WIP
    6. Verify implementation works
    7. After fresh verification passes, amend the commit message to remove `WIP:`
    8. Self-review (see below); amend and reverify any resulting changes before finalizing again
    9. Report back

    Never include unrelated/pre-existing changes unless explicitly requested. Do not request routine commit-scope confirmation. If verification cannot pass, leave the commit marked `WIP:` and report the failures.

    Work from: [directory]

    **While you work:** If you encounter something unexpected or unclear, **ask questions**.
    It's always OK to pause and clarify. Don't guess or make assumptions.

    ## Before Reporting Back: Self-Review

    Review your work with fresh eyes. Ask yourself:

    **Completeness:**
    - Did I fully implement everything in the spec?
    - Did I miss any requirements?
    - Are there edge cases I didn't handle?

    **Quality:**
    - Is this my best work?
    - Are names clear and accurate (match what things do, not how they work)?
    - Is the code clean and maintainable?

    **Discipline:**
    - Did I avoid overbuilding (YAGNI)?
    - Did I only build what was requested?
    - Did I follow existing patterns in the codebase?

    **Testing:**
    - Do tests actually verify behavior (not just mock behavior)?
    - Did I follow TDD if required?
    - Are tests comprehensive?

    If you find issues during self-review, fix them now before reporting.

    ## Report Format

    When done, report:
    - What you implemented
    - What you tested and test results
    - WIP and final commit IDs (or why the commit remains WIP)
    - Files changed and unrelated/pre-existing files left untouched
    - Self-review findings (if any)
    - Any issues or concerns
```
