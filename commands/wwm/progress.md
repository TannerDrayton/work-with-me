---
name: wwm:progress
description: Check project status and route to next action
allowed-tools:
  - Read
  - Bash
  - Grep
  - Glob
  - SlashCommand
---
<objective>
Check project progress, review recent work and what's ahead, then route to next action.

Provides situational awareness before continuing work.
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/progress.md
</execution_context>

<process>
Execute the progress workflow from @~/.claude/work-with-me/workflows/progress.md end-to-end.
Preserve all routing logic (Routes A through F) and edge case handling.
</process>
