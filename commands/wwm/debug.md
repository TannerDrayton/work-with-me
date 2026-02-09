---
name: wwm:debug
description: Investigate issues using systematic debugging
argument-hint: [issue description]
allowed-tools:
  - Read
  - Bash
  - Task
  - AskUserQuestion
---

<objective>
Debug issues using scientific method with subagent isolation.

**Orchestrator role:** Gather symptoms, spawn specialized debugger agent, handle checkpoints, coordinate investigation.

**Why subagent:** Investigation burns context fast (reading files, forming hypotheses, testing). Fresh 200k context per investigation preserves main conversation context.
</objective>

<context>
Issue: $ARGUMENTS

Check for active sessions:
```bash
ls .planning/debug/*.md 2>/dev/null | grep -v resolved | head -5
```
</context>

<process>

## 0. Initialize Context

```bash
INIT=$(node ~/.claude/work-with-me/bin/wwm-tools.js state load)
```

Extract `commit_docs` from init JSON. Resolve debugger model:
```bash
DEBUGGER_MODEL=$(node ~/.claude/work-with-me/bin/wwm-tools.js resolve-model wwm-debugger --raw)
```

## 1. Check Active Sessions

If active sessions exist AND no $ARGUMENTS:
- List sessions with status, hypothesis, next action
- You pick a number to resume OR describe a new issue

If $ARGUMENTS provided OR you describe a new issue:
- Continue to symptom gathering

## 2. Gather Symptoms (if new issue)

Use AskUserQuestion for each:

1. **Expected behavior** - What should happen?
2. **Actual behavior** - What happens instead?
3. **Error messages** - Any errors? (paste or describe)
4. **Timeline** - When did this start? Ever worked?
5. **Reproduction** - How do you trigger it?

After gathering, confirm ready to investigate.

## 3. Spawn wwm-debugger Agent

Fill prompt and spawn:

```markdown
<objective>
Investigate issue: {slug}

**Summary:** {trigger}
</objective>

<symptoms>
expected: {expected}
actual: {actual}
errors: {errors}
reproduction: {reproduction}
timeline: {timeline}
</symptoms>

<mode>
symptoms_prefilled: true
goal: find_and_fix
</mode>

<debug_file>
Create: .planning/debug/{slug}.md
</debug_file>
```

```
Task(
  prompt=filled_prompt,
  subagent_type="wwm-debugger",
  model="{debugger_model}",
  description="Debug {slug}"
)
```

## 4. Handle Agent Return

**If `## ROOT CAUSE FOUND`:**
- Show the root cause and evidence summary
- Offer options:
  - "Fix now" — proceed to fix
  - "Plan fix" — route to /wwm:plan-phase --gaps
  - "Manual fix" — user handles it

**If `## CHECKPOINT REACHED`:**
- Present checkpoint details
- Get user response
- Spawn continuation agent (see step 5)

**If `## INVESTIGATION INCONCLUSIVE`:**
- Show what was checked and eliminated
- Offer options:
  - "Continue investigating" - spawn new agent with additional context
  - "Manual investigation" - you'll take it from here
  - "Add more context" - gather more symptoms, try again

## 5. Spawn Continuation Agent (After Checkpoint)

When you respond to a checkpoint, spawn fresh agent:

```markdown
<objective>
Continue debugging {slug}. Evidence is in the debug file.
</objective>

<prior_state>
Debug file: @.planning/debug/{slug}.md
</prior_state>

<checkpoint_response>
**Type:** {checkpoint_type}
**Response:** {user_response}
</checkpoint_response>

<mode>
goal: find_and_fix
</mode>
```

```
Task(
  prompt=continuation_prompt,
  subagent_type="wwm-debugger",
  model="{debugger_model}",
  description="Continue debug {slug}"
)
```

</process>

<success_criteria>
- [ ] Active sessions checked
- [ ] Symptoms gathered (if new)
- [ ] wwm-debugger spawned with context
- [ ] Checkpoints handled correctly
- [ ] Root cause confirmed before fixing
</success_criteria>
