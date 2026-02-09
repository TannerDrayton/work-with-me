---
name: wwm:execute-phase
description: Execute phase with wave-based parallelization
argument-hint: "<phase-number> [--gaps-only]"
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
  - Bash
  - Task
  - TodoWrite
  - AskUserQuestion
---
<objective>
Execute phase using wave-based parallel execution.

Orchestrator discovers plans, analyzes dependencies, groups into waves, spawns subagents, collects results. Each subagent loads the full execute-plan context and handles its own plan.

Context budget: ~15% orchestrator, 100% fresh per subagent.
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/execute-phase.md
@~/.claude/work-with-me/references/ui-brand.md
</execution_context>

<context>
Phase: $ARGUMENTS

**Flags:**
- `--gaps-only` — Execute only gap closure plans (plans with `gap_closure: true` in frontmatter). Use after verify-work creates fix plans.

@.planning/ROADMAP.md
@.planning/STATE.md
</context>

<process>
Execute the execute-phase workflow from @~/.claude/work-with-me/workflows/execute-phase.md end-to-end.
Preserve all workflow gates (wave execution, checkpoint handling, verification, state updates, routing).
</process>
