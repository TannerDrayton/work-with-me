---
name: wwm:quick
description: Let's knock out a quick task together (streamlined workflow)
argument-hint: ""
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
  - Bash
  - Task
  - AskUserQuestion
---
<objective>
Let's handle small, ad-hoc tasks together with full guarantees (atomic commits, STATE.md tracking) while streamlining the workflow (skip research, plan-checking, formal verification).

Quick mode is our same collaborative system with a shorter path:
- We'll plan together (quick mode) then work together on execution
- Skips wwm-phase-researcher, wwm-plan-checker, wwm-verifier (for speed)
- Quick tasks live in `.planning/quick/` separate from planned phases
- Updates STATE.md "Quick Tasks Completed" table (NOT ROADMAP.md)

Use when: You know exactly what you want and the task is small enough to not need formal research or verification.
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/quick.md
</execution_context>

<context>
@.planning/STATE.md
</context>

<process>
Execute the quick workflow from @~/.claude/work-with-me/workflows/quick.md end-to-end.
Preserve all workflow gates (validation, task description, planning, execution, state updates, commits).
</process>
