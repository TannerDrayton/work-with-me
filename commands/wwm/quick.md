---
name: wwm:quick
description: Quick task execution (streamlined workflow)
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
Handle small, ad-hoc tasks with full guarantees (atomic commits, STATE.md tracking) while streamlining the workflow (skip research, plan-checking, formal verification).

Same system, shorter path:
- Plan (quick mode) → execute
- Skips wwm-phase-researcher, wwm-plan-checker, wwm-verifier (for speed)
- Quick tasks live in `.planning/quick/` separate from planned phases
- Updates STATE.md "Quick Tasks Completed" table (NOT ROADMAP.md)

Use when: Task is well-defined and small enough to skip formal research or verification.
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
