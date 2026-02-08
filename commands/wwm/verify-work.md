---
name: wwm:verify-work
description: Let's test what we built together through conversation
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
Let's validate what we built through conversational testing with persistent state.

Purpose: Confirm our work actually delivers what you need. One test at a time, plain text responses, natural conversation - no interrogation. When we find issues, I'll help diagnose them, and we can plan fixes together.

Output: {phase}-UAT.md tracking all our test results. If issues found: diagnosed gaps, fix plans ready for us to work on together
</objective>

<execution_context>
@~/.claude/work-with-me/workflows/verify-work.md
@~/.claude/work-with-me/templates/UAT.md
</execution_context>

<context>
Phase: $ARGUMENTS (optional)
- If provided: Test specific phase (e.g., "4")
- If not provided: I'll check for active sessions or ask which phase

@.planning/STATE.md
@.planning/ROADMAP.md
</context>

<process>
Execute the verify-work workflow from @~/.claude/work-with-me/workflows/verify-work.md end-to-end.
Preserve all workflow gates (session management, test presentation, diagnosis, fix planning, routing).
</process>
