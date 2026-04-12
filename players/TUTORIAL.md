# MULTI-AGENT ORCHESTRATION TUTORIAL
## Quick Start Guide for Building with Multiple Claude Agents

**Purpose:** Learn how to coordinate multiple Claude agents to build software faster.

**Time to Read:** 5 minutes

---

## SETUP (BEFORE THE GAME)

### Prerequisites

**1. Enable agent teams** (experimental feature)

Add to `~/.claude/settings.json`:
```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

**2. Install and start tmux**

Install tmux (macOS):
```bash
brew install tmux
```

Start tmux in control mode (works best with iTerm2):
```bash
tmux -CC
```

This gives each agent team member its own pane, so you can see all agents working simultaneously.

**3. Start Claude with auto-permissions:**

```bash
claude --permission-mode auto
```

This allows agent teams to work freely without constant permission prompts, while still blocking destructive operations.

### When Spawning Agent Teams

Always specify model and mode for cost-efficiency:
```
Agent({
  model: "sonnet",      // Most cost-effective
  mode: "auto",         // Pre-approve safe operations
  description: "Backend developer for flight API",
  prompt: "Build the flight tracking service..."
})
```

---

## WHY MULTIPLE AGENTS?

**Single Agent:** Sequential work, context overload, no specialization
**Multiple Agents:** Parallel execution, specialized focus, faster iteration

**Example:**
- Single agent: 60 minutes (sequential)
- 3 agents in parallel: 25 minutes (same output)

---

## HOW TO USE AGENTS IN CLAUDE CODE CLI

**You just talk to Claude naturally. No code, no JSON.**

```
You: "Create a team with Backend, Frontend, and QA specialists.
     Use Sonnet for all agents."

Claude: "I've created a team with three specialists..."

You: "Team: Build a flight booking system"

[Agents work in parallel, each in their own pane]
```

**Three options:**
1. **Multiple terminal tabs** - Simple, manual coordination
2. **Sub-agents** - Spawn within one conversation, results only
3. **Agent Teams** - Persistent specialists, communicate with each other (recommended for this game)

---

## AGENT TEAMS BEST PRACTICES

### 1. Limit Team Size (2-3 agents)

**Good:** Backend + Frontend + QA (3 agents)
**Bad:** Backend + Frontend + DB + Testing + DevOps + Security + Docs (7 agents = chaos)

---

### 2. Avoid File Conflicts - Clear Ownership

**Good:**
```
Backend Agent: owns backend/
Frontend Agent: owns frontend/
QA Agent: owns tests/
```

**Bad:**
```
Agent 1: Build API in app.py
Agent 2: Add payment to app.py  ← CONFLICT!
```

---

### 3. Set Clear Deadlines

```
You: "Team: Build flight search. Use Sonnet.
     Backend: Flask API
     Frontend: React UI
     GO!"
```

---

### 4. Establish Interfaces Early

```
You: "Before building, agree on API contract:
     - GET /flights?origin={}&dest={} → Returns [{id, price}]
     - POST /bookings {flight_id, name} → Returns {booking_id}
     
     Now build to this contract."
```

---

### 5. Assign Clear Roles

```
Backend Agent: Owns .py files in backend/, does NOT touch frontend
Frontend Agent: Owns .jsx files in frontend/, calls backend APIs
QA Agent: Owns tests/, does NOT modify source code
```

---

### 6. Monitor Progress

Check in periodically to see what's working and redirect if needed.

---

### Quick Checklist

Before creating agent team:
- [ ] Team size: 2-3 agents max
- [ ] File ownership: No overlaps
- [ ] Interfaces: API contracts defined

---

## THE FOUR PATTERNS

### 1. Parallel Execution
Tasks are independent, run simultaneously.
```
You: "Spawn two agents in parallel, use Sonnet for both:
     - Agent 1: Build Flask API on port 5001
     - Agent 2: Build React UI on port 3000"
```

### 2. Sequential Pipeline
Output of one feeds into next.
```
You: "Run sequentially, use Sonnet:
     - First: Design database schema
     - Then: Build API using that schema"
```

### 3. Specialist Roles
Create a team where each agent keeps the same role.
```
You: "Create team with Sonnet: Backend, Frontend, QA"
```

### 4. Iterative Refinement
Build → Review → Improve
```
You: "Use Sonnet. Build booking API, then spawn reviewer to find issues,
     then spawn another to fix them."
```

---

## PROMPT ENGINEERING ESSENTIALS

### Good Request Structure

```
You: "Build [feature] with [N] agents. Use Sonnet for all agents.

     Agent 1: [Role] - Build [component]
     - [Requirement 1]
     - [Requirement 2]
     - Port: [X]

     Agent 2: [Role] - Build [component]
     - [Requirement 1]
     - [Requirement 2]
     - Port: [Y]

     Deliverable: [What should work end-to-end]"
```

### What to Include

1. **Task description** - What to build
2. **Tech requirements** - Framework, ports
3. **Deliverables** - Expected outputs
4. **Execution strategy** - Parallel or sequential

### Anti-Patterns

❌ Too vague: "Make it better"
❌ Too many agents: "Spawn 7 agents..."
❌ Missing tech stack: "Build a web app"

---

## DEBUGGING QUICK TIPS

### When Things Break

**Step 1:** Read the error carefully
```
Good: "Error: ModuleNotFoundError: flask_cors in app.py line 3"
Bad: "It's broken!"
```

**Step 2:** Isolate the problem
- Backend or frontend?
- Test API with curl directly
- Check one component at a time

**Step 3:** Recovery strategies
- **Simple bugs** → Ask same agent to fix
- **Complex bugs** → Spawn debug specialist
- **Wrong approach** → Start over with clearer prompt

### Prevention

- Test as you go (don't wait until end)
- Be specific about dependencies
- Include error handling in requests
- Ask agents to explain approach first

---

## QUICK REFERENCE

### Spawning Agents

**Parallel:**
```
You: "Spawn 2 agents in parallel using Sonnet: [task 1], [task 2]"
```

**Sequential:**
```
You: "Spawn sequentially using Sonnet: First [task 1], then [task 2]"
```

**Team:**
```
You: "Create team with Sonnet: [roles]"
You: "Team: [task]"
```

### Common Roles

- **Backend Developer** - APIs, databases
- **Frontend Developer** - UI, interactions
- **QA Engineer** - Tests, edge cases
- **Integration Engineer** - Connect services

### Red Flags

🚩 6+ agents → Too many
🚩 10+ min wait → Bad parallelization
🚩 15+ min integration → Poor contracts
🚩 Same file edited by 2 agents → Conflicts

---

## KEY PRINCIPLES

1. **Use natural language** - Just describe what you want
2. **Use Sonnet** - Keep costs down
3. **Clear descriptions** - Specific tasks, tech stack, ports
4. **Explicit context** - Pass info between agents
5. **Review outputs** - Test as you go
6. **Parallelize when possible** - Max speed
7. **Don't overcomplicate** - 2-3 agents optimal

---

**Good luck! 🚀**

*The best way to learn is to do. Start with 2 agents in parallel and build from there.*
