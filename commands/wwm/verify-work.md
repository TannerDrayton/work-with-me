---
name: wwm:verify-work
description: Verify phase delivery through conversational testing
argument-hint: "[phase number, e.g., '4']"
allowed-tools:
  - Read
  - Bash
  - Glob
  - Grep
  - Edit
  - Write
  - Task
---
<objective>
Validate phase delivery through conversational testing with persistent state.

Purpose: Confirm delivered work meets requirements. One test at a time, plain text responses, natural conversation. When issues found: diagnose, plan fixes.

Output: {phase}-UAT.md tracking test results. If issues found: diagnosed gaps, fix plans ready for execution.
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/verify-work.md
@~/.claude/work-with-me/templates/UAT.md
</execution_context>

<context>
Phase: $ARGUMENTS (optional)
- If provided: Test specific phase (e.g., "4")
- If not provided: Check for active sessions or prompt for phase

@.planning/STATE.md
@.planning/ROADMAP.md
</context>

<process>
Execute the verify-work workflow from @~/.claude/work-with-me/workflows/verify-work.md end-to-end.
Preserve all workflow gates (session management, test presentation, diagnosis, fix planning, routing).
</process>
