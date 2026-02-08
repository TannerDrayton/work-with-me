<div align="center">

# WORK WITH ME

**A collaborative development system for working together with Claude Code - thoughtful planning, transparent execution, and true partnership.**

[![License](https://img.shields.io/badge/license-MIT-blue?style=for-the-badge)](LICENSE)
[![Install Method](https://img.shields.io/badge/install-GitHub-success?style=for-the-badge&logo=github)](https://github.com/TannerDrayton/work-with-me#getting-started)

</div>

```bash
npx github:TannerDrayton/work-with-me
```

---

## Why This Approach

I forked from [get-shit-done](https://github.com/glittercowboy/get-shit-done) because I wanted something different.

GSD is amazing for autonomous execution - describe what you want, let Claude build it. I want collaboration, not delegation. I want to understand what's being built, make decisions along the way, and learn from the process.

So I transformed it into **Work With Me**:

- **From** autonomous execution → **To** collaborative development
- **From** "Claude does it" → **To** "we do it together"
- **From** minimal checkpoints → **To** meaningful collaboration points
- **From** batch execution → **To** step-by-step partnership

The technical excellence remains - context engineering, subagent orchestration, state management. But the philosophy shifts: Claude is your pair programming partner, not your contractor.

---

## Who This Is For

People who want to:

- **Understand** what's being built, not just delegate and review
- **Collaborate** with AI through transparent processes
- **Learn** from working alongside Claude, not just from final code
- **Control** the direction at each step, not just approve/reject at the end
- **Build together** with thoughtful discussion, not just rapid autonomous execution

If you want Claude to build things for you completely autonomously, stick with GSD. If you want to work together with Claude as a partner, use Work With Me.

---

## Getting Started

```bash
npx github:TannerDrayton/work-with-me
```

The installer prompts you to choose:

1. **Runtime** — Claude Code, OpenCode, Gemini, or all
2. **Location** — Global (all projects) or local (current project only)

Verify with `/wwm:help` inside your chosen runtime.

### Staying Updated

Work With Me evolves as we refine the collaborative approach:

```bash
npx github:TannerDrayton/work-with-me
```

<details>
<summary><strong>Non-interactive Install (Docker, CI, Scripts)</strong></summary>

```bash
# Claude Code
npx github:TannerDrayton/work-with-me --claude --global   # Install to ~/.claude/
npx github:TannerDrayton/work-with-me --claude --local    # Install to ./.claude/

# OpenCode
npx github:TannerDrayton/work-with-me --opencode --global # Install to ~/.opencode/
npx github:TannerDrayton/work-with-me --opencode --local  # Install to ./.opencode/

# Gemini CLI
npx github:TannerDrayton/work-with-me --gemini --global   # Install to ~/.gemini/
npx github:TannerDrayton/work-with-me --gemini --local    # Install to ./.gemini/

# Install to all runtimes
npx github:TannerDrayton/work-with-me --all --global
npx github:TannerDrayton/work-with-me --all --local
```

</details>

---

## How It Works

### 1. We Start Projects Together

```bash
/wwm:new-project
```

I'll ask you questions to understand your vision, we'll optionally research the domain together, define clear requirements, and create a roadmap collaboratively.

**Output:**

- `PROJECT.md` — our shared context
- `REQUIREMENTS.md` — what we're building
- `ROADMAP.md` — how we'll build it together

### 2. We Discuss Before Planning

```bash
/wwm:discuss-phase 1
```

Before planning implementation, let's talk about the gray areas - UI decisions, UX flows, behavior choices. I'll ask questions, you share your vision, and we document decisions together.

**Output:**

- `CONTEXT.md` — our decisions guide the work ahead

### 3. We Plan Together

```bash
/wwm:plan-phase 1
```

We'll research the technical approach (if needed), create detailed plans together, and verify they'll achieve our goals before any code is written.

**Output:**

- `RESEARCH.md` — findings to inform our decisions
- `PLAN.md` — step-by-step implementation guide
- Plans checked for completeness and alignment

### 4. We Build Together

```bash
/wwm:execute-phase 1
```

I'll work through the plan with you, pausing at checkpoints for your input, showing you what's happening, and keeping you involved throughout execution.

**Collaboration points:**

- Checkpoint for decisions
- Verification checkpoints after automation
- Transparent progress updates
- Clear communication about what's next

### 5. We Verify Together

```bash
/wwm:verify-work 1
```

Let's test what we built through conversation. I'll guide you through verification, we'll find issues together, and plan fixes collaboratively.

**Output:**

- `UAT.md` — our testing session
- Issues diagnosed and planned for fixing

---

## Commands

### Project Setup

- `/wwm:new-project` — Let's set up a new project together
- `/wwm:map-codebase` — Let's understand existing code together

### Planning & Discussion

- `/wwm:discuss-phase` — Work together to clarify your vision
- `/wwm:research-phase` — Let's research implementation approaches
- `/wwm:plan-phase` — Let's create a plan together
- `/wwm:list-phase-assumptions` — I'll share my assumptions so you can correct them

### Execution & Verification

- `/wwm:execute-phase` — Let's work through this phase together
- `/wwm:verify-work` — Let's test what we built
- `/wwm:debug` — Let's investigate issues together

### Quick Tasks

- `/wwm:quick` — Let's knock out a quick task (streamlined workflow)

### Progress & Navigation

- `/wwm:progress` — Let's check where we are and decide what's next
- `/wwm:pause-work` — Let's save our progress
- `/wwm:resume-work` — Let's pick up where we left off

### Todos & Planning

- `/wwm:add-todo` — Let's capture an idea for later
- `/wwm:check-todos` — Let's review our pending todos

### Milestones

- `/wwm:new-milestone` — Let's start a new milestone
- `/wwm:audit-milestone` — Let's verify our milestone achieved its goals
- `/wwm:complete-milestone` — Let's archive this completed milestone

### Phase Management

- `/wwm:add-phase` — Add a new phase to our roadmap
- `/wwm:insert-phase` — Let's insert urgent work between phases
- `/wwm:remove-phase` — Let's remove a phase we decided not to do

### Configuration

- `/wwm:settings` — Configure our workflow preferences
- `/wwm:set-profile` — Switch model profile (quality/balanced/budget)
- `/wwm:help` — Show all commands
- `/wwm:update` — Update Work With Me

---

## Philosophy

### Collaboration Over Automation

**Work With Me** believes in:

- **Transparency** — You see what's happening at each step
- **Partnership** — We make decisions together, not just approve/reject
- **Understanding** — Context is shared, not hidden in subagent execution
- **Control** — You guide direction throughout, not just at checkpoints
- **Learning** — Working together helps you understand, not just delegate

### When to Use WWM vs GSD

**Use Work With Me when:**

- You want to understand and guide the development process
- You're learning and want to work alongside Claude
- The project requires frequent decision-making and iteration
- You value transparency and collaboration over pure speed
- You want meaningful checkpoints, not just final review

**Use Get Shit Done when:**

- You know exactly what you want and how it should be built
- Speed and autonomous execution are priorities
- You're comfortable with batch execution and end-review
- The requirements are clear and unlikely to change
- You trust Claude to handle most decisions independently

Both approaches use the same technical foundation (context engineering, subagent orchestration). The difference is philosophy and workflow.

---

## Technical Foundation

Behind the scenes, Work With Me uses:

- **Context Engineering** — Fresh subagent contexts prevent quality degradation
- **Meta-Prompting** — Specialized agents with role-specific instructions
- **State Management** — Persistent state across sessions via `.planning/STATE.md`
- **Goal-Backward Verification** — Verify outcomes, not just task completion
- **Checkpoint Protocol** — Meaningful collaboration points throughout execution
- **Atomic Commits** — Per-task commits with clear history

The system inherits GSD's technical excellence while transforming the collaboration model.

---

## Credits

**Work With Me** is a fork of [get-shit-done](https://github.com/glittercowboy/get-shit-done) by TÂCHES.

The original GSD system provides the technical foundation - context engineering, subagent architecture, and state management. Work With Me transforms the philosophy from autonomous execution to collaborative development.

Thank you to TÂCHES for building such a solid foundation to build upon.

---

## License

MIT License - See [LICENSE](LICENSE) for details.

Forked from get-shit-done by TÂCHES, also MIT licensed.

---

## Contributing

This is a personal fork exploring collaborative AI development. If you're interested in this approach:

1. Try it out and share feedback
2. Open issues for bugs or suggestions
3. Fork and experiment with your own variations

The goal is to learn what works for collaborative AI development, not to build the one true system.

---

<div align="center">

**Work With Me** · Collaborative Development with Claude

[Get Started](#getting-started) · [Commands](#commands) · [Philosophy](#philosophy)

</div>
