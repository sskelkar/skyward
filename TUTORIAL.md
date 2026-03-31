# MULTI-AGENT ORCHESTRATION TUTORIAL
## A Practical Guide to Building with Multiple Claude Agents

**Purpose:** Learn how to coordinate multiple Claude agents to build software faster and more effectively than working with a single agent.

**Audience:** Software engineers new to multi-agent workflows

**Time to Read:** 20-30 minutes

---

## TABLE OF CONTENTS

1. [Why Multiple Agents?](#why-multiple-agents)
2. [Core Concepts](#core-concepts)
3. [Claude Code Mechanics: How to Actually Spawn Agents](#claude-code-mechanics-how-to-actually-spawn-agents)
4. [The Four Fundamental Patterns](#the-four-fundamental-patterns)
5. [Prompt Engineering for Agents](#prompt-engineering-for-agents)
6. [Context Management](#context-management)
7. [Practical Examples](#practical-examples)
8. [Common Pitfalls & Solutions](#common-pitfalls--solutions)
9. [Advanced Techniques](#advanced-techniques)
10. [Decision Framework](#decision-framework)
11. [Quick Reference](#quick-reference)

---

## WHY MULTIPLE AGENTS?

### The Single-Agent Limitation

When you work with one Claude agent for a complex task:
- **Sequential work only** - Agent does one thing at a time
- **Context overload** - Long conversation contexts get unwieldy
- **No specialization** - Same agent handles frontend, backend, testing, docs
- **Revision friction** - Hard to backtrack without losing progress

### The Multi-Agent Advantage

With multiple agents working together:
- ✅ **Parallel execution** - Multiple tasks progress simultaneously
- ✅ **Specialized focus** - Each agent excels in its domain
- ✅ **Clean contexts** - Each agent has focused, manageable conversation
- ✅ **Modular output** - Easy to replace or revise specific components
- ✅ **Faster iteration** - 3 agents working 20 minutes = 60 agent-minutes of work

### Real-World Example

**Task:** Build a flight booking web app

**Single Agent Approach (60 minutes):**
```
You: "Build a flight booking web app with backend API and frontend"
→ Agent builds backend (20 min)
→ Agent builds frontend (20 min)
→ Agent integrates (10 min)
→ Agent writes tests (10 min)
Total: 60 minutes, sequential
```

**Multi-Agent Approach (25 minutes):**
```
Agent 1: "Build Flask API for flight search and booking" (20 min)
Agent 2: "Build React frontend for flight booking" (20 min) [parallel!]
Agent 3: "Integrate Agent 1's API with Agent 2's frontend" (5 min)
Total: 25 minutes, mostly parallel
```

**Result:** Same output, 60% faster.

---

## CORE CONCEPTS

### What is an Agent?

An **agent** is a single Claude conversation session with:
- A specific task or domain
- Its own conversation context
- Ability to produce code, analysis, or other outputs

**Example:** "Agent 1: Backend API Developer" vs. "Agent 2: Frontend Developer"

### Agent Coordination Patterns

There are four fundamental ways to coordinate agents:

1. **Parallel** - Agents work simultaneously on independent tasks
2. **Sequential** - Agents work in a pipeline, each using prior output
3. **Specialist** - Agents have permanent roles across multiple tasks
4. **Iterative** - Agents refine each other's work in cycles

### The Human-in-the-Loop

You are the **orchestrator**:
- You decide which pattern to use
- You write prompts for each agent
- You review agent outputs
- You coordinate handoffs between agents
- You make final integration decisions

Think of yourself as a conductor, not a passive observer.

---

## CLAUDE CODE MECHANICS: HOW TO ACTUALLY SPAWN AGENTS

Now that you understand **why** multiple agents are useful and **what** they are, let's cover **how** to actually spawn and coordinate them in Claude Code.

### Three Ways to Work with Multiple Agents

Claude Code supports three approaches to multi-agent workflows:

#### Option 1: Multiple Conversations (Manual Tabs)

**How it works:** Open multiple Claude Code tabs/windows, each with a different conversation.

**Example:**
```
Tab 1: "Build a Flask API for flight search on port 5001"
Tab 2: "Build a React UI for flight search on port 3000"
Tab 3: "Integrate the API from tab 1 with the UI from tab 2"
```

**Pros:**
- ✅ Simple, no special tools needed
- ✅ Full control over each conversation
- ✅ Easy to reference each agent's full history

**Cons:**
- ❌ Manual context switching (switching tabs)
- ❌ Manual copy-paste between agents
- ❌ Hard to manage more than 3 agents
- ❌ No programmatic coordination

**When to use:**
- You're new to multi-agent workflows
- Only 2-3 agents needed
- You want full visibility into each conversation
- You're experimenting/learning

---

#### Option 2: Sub-Agents via Agent Tool (Recommended)

**How it works:** Within a single Claude Code conversation, use the `Agent` tool to spawn sub-agents programmatically.

**Key concept:** You remain the **orchestrator** in the main conversation. You spawn sub-agents, review their output, and coordinate handoffs.

**Example - Spawning a parallel agent:**

```
Main conversation:
You: "I need to build a flight booking app with backend and frontend"

Claude (orchestrator): "I'll spawn two agents in parallel:
  - Agent 1: Build Flask API
  - Agent 2: Build React UI"

[Claude calls Agent tool twice]

Agent tool call 1:
{
  "description": "Build Flask API",
  "prompt": "You are a backend developer. Build a Flask API for flight
             search with endpoint GET /flights?origin={}&dest={}&date={}.
             Use SQLite. Run on port 5001. Include 10 mock flights."
}

Agent tool call 2:
{
  "description": "Build React UI",
  "prompt": "You are a frontend developer. Build a React app for flight
             search. Call API at http://localhost:5001/flights.
             Run on port 3000."
}

[Both agents run simultaneously]

Agent 1 completes → returns Flask code
Agent 2 completes → returns React code

Claude (orchestrator): "Both agents completed. Here's what they built:
  Agent 1: Flask API [summary]
  Agent 2: React UI [summary]

  Now testing integration..."
```

**How to invoke the Agent tool:**

The Agent tool accepts these key parameters:

1. **`description`** (required): Short 3-5 word summary (e.g., "Build Flask API")
2. **`prompt`** (required): Full task description for the agent
3. **`subagent_type`** (optional): Specialized agent type
   - `"general-purpose"` (default) - Most tasks
   - `"Explore"` - Codebase exploration, file searches
   - `"Plan"` - Implementation planning
4. **`run_in_background`** (optional): Set to `true` for long-running tasks
5. **`isolation`** (optional): Set to `"worktree"` for isolated git environment

**Example - Sequential agents with handoff:**

```
Agent 1 (Backend):
{
  "description": "Build booking API",
  "prompt": "Build a Flask API for bookings on port 5002 with POST /bookings
             endpoint. Schema: {flight_id, passenger_name, email}. Use SQLite."
}

[Wait for Agent 1 to complete]

Agent 2 (Frontend integration):
{
  "description": "Integrate booking UI",
  "prompt": "The backend has a booking API at http://localhost:5002/bookings.
             Here's the endpoint contract: POST /bookings, expects
             {flight_id, passenger_name, email}, returns {booking_id, status}.

             Extend the existing React flight search to add booking capability."
}
```

**Pros:**
- ✅ Programmatic coordination within one conversation
- ✅ Orchestrator can spawn agents in parallel or sequence
- ✅ Easy to review and integrate sub-agent outputs
- ✅ Can spawn agents with `run_in_background: true` for long tasks
- ✅ All work visible in single conversation

**Cons:**
- ❌ Sub-agent conversations not directly visible (you see results only)
- ❌ Limited control over sub-agent mid-execution

**When to use:**
- Most multi-agent scenarios (recommended default)
- 2-5 agents needed
- You want programmatic coordination
- You want everything in one conversation

**Best practices:**
- Write clear, specific prompts for each agent
- Use descriptive `description` fields (helps track progress)
- Review each agent's output before spawning the next (sequential)
- For parallel work, spawn all agents in one message
- Use `run_in_background: true` for tasks > 2 minutes

---

#### Option 3: Agent Teams (Advanced)

**How it works:** Create a persistent team of agents that collaborate across multiple user messages.

**Key concept:** Instead of spawning one-off agents, you create a **team** of specialist agents that persist and communicate with each other.

**Example:**

```
You: "Create a team with Backend, Frontend, and QA specialists"

[Team created with 3 persistent agents]

You: "Team: Build a flight booking system"

Backend Agent: [Builds API]
Frontend Agent: [Builds UI, can ask Backend about endpoints]
QA Agent: [Reviews both, suggests improvements]

[Agents collaborate, message each other]

You: "Team: Add payment processing"

[Same agents continue, building on their previous work]
Backend Agent: [Adds payment endpoint to existing API]
Frontend Agent: [Adds payment form to existing UI]
QA Agent: [Tests new flow]
```

**Pros:**
- ✅ Agents retain context across multiple turns
- ✅ Agents can communicate with each other
- ✅ Persistent specialists (like real org structure)
- ✅ Great for multi-quarter projects

**Cons:**
- ❌ More complex to set up and manage
- ❌ Requires learning Agent Teams API
- ❌ Can be overkill for simple tasks

**When to use:**
- Multi-quarter projects (in this game, Q2-Q6)
- Want persistent agent memory
- Simulating real organizational structure
- Agents need to communicate with each other

**Note:** For this workshop, **Agent Teams are optional** and **advanced**. Most directors will use Sub-Agents (Option 2) successfully.

---

### Decision Tree: Which Approach to Use?

```
Are you new to multi-agent workflows?
├─ Yes → Start with Multiple Tabs (Option 1)
└─ No → Continue...

Do you need agents to persist across multiple tasks/quarters?
├─ Yes → Use Agent Teams (Option 3)
└─ No → Continue...

Do you have 2-5 agents working on a single task?
├─ Yes → Use Sub-Agents via Agent Tool (Option 2) ← RECOMMENDED
└─ No (just 1-2 simple agents) → Use Multiple Tabs (Option 1)
```

### Practical Agent Tool Examples

#### Example 1: Parallel Execution

**Scenario:** Build backend and frontend simultaneously.

```
Main orchestrator spawns two agents in parallel:

Agent 1:
{
  "description": "Build search API",
  "prompt": "You are a backend developer. Build a Flask API for flight search.

             Endpoint: GET /flights?origin={code}&dest={code}&date={date}
             Response: [{id, origin, dest, departure, arrival, price, seats}]

             Requirements:
             - SQLite database with flights table
             - 10 mock flights (SFO, LAX, NYC, ORD, SEA)
             - CORS enabled for localhost:3000
             - Run on port 5001

             Deliverable: Complete app.py that runs with 'python app.py'"
}

Agent 2:
{
  "description": "Build search UI",
  "prompt": "You are a frontend developer. Build a flight search interface.

             Features:
             - Search form (origin, destination, date inputs)
             - Results table showing flights
             - Clean, professional styling
             - Call API at http://localhost:5001/flights

             Requirements:
             - Vanilla HTML/CSS/JS (no build step)
             - Loading states while fetching
             - Error handling
             - Run on port 3000

             Deliverable: Complete index.html that opens in browser"
}

[Both agents run simultaneously - massive time savings!]
```

#### Example 2: Sequential Pipeline

**Scenario:** Agent 2 needs Agent 1's output.

```
Main orchestrator spawns agents sequentially:

Step 1 - Spawn Agent 1:
{
  "description": "Design database schema",
  "prompt": "Design a database schema for a flight booking system.

             Tables needed:
             - flights (id, origin, dest, departure, arrival, price, seats)
             - bookings (id, flight_id, passenger_name, email, status, created)
             - payments (id, booking_id, amount, payment_method, status)

             Output: SQL CREATE TABLE statements with appropriate types,
             constraints, and indexes."
}

[Wait for Agent 1 to complete]

Step 2 - Review Agent 1's schema, then spawn Agent 2:
{
  "description": "Implement booking API",
  "prompt": "Build a Flask API for flight bookings using this database schema:

             [Paste Agent 1's schema here]

             Endpoints:
             - POST /bookings (create booking)
             - GET /bookings/{id} (get booking details)
             - DELETE /bookings/{id} (cancel booking)

             Use the exact schema from above. Include validation and error handling."
}
```

#### Example 3: Background Agents for Long Tasks

**Scenario:** Agent needs > 2 minutes, don't want to block.

```
Spawn long-running agent in background:

{
  "description": "Generate test data",
  "prompt": "Generate a realistic SQLite database with:
             - 1000 flights across 50 US airports
             - Random departure times over next 30 days
             - Realistic prices ($50-$800)
             - Varying seat availability

             Output: flights.db file",
  "run_in_background": true
}

[Agent runs in background, orchestrator continues with other work]

[Later, when background agent completes, orchestrator is notified]
```

#### Example 4: Specialized Explore Agent

**Scenario:** Need to understand existing codebase structure.

```
Use specialized Explore agent for codebase research:

{
  "description": "Find authentication code",
  "prompt": "Find and analyze all authentication-related code in this codebase.

             Look for:
             - Login/logout endpoints
             - Session management
             - Authentication middleware
             - Token generation/validation

             Provide: File locations, key functions, and how auth flow works",
  "subagent_type": "Explore"
}

[Explore agent is optimized for code searching and analysis]
```

### Common Mistakes with Agent Tool

❌ **Vague prompts**
```
{
  "description": "Build backend",
  "prompt": "Build the backend"
}
```
→ Agent doesn't know tech stack, ports, endpoints, etc.

✅ **Specific prompts**
```
{
  "description": "Build Flask booking API",
  "prompt": "Build a Flask API on port 5002 with POST /bookings endpoint.
             Body: {flight_id, passenger_name, email}.
             Returns: {booking_id, status, confirmation_code}.
             Use SQLite for storage."
}
```

---

❌ **Too many parallel agents**
```
[Spawns 7 agents simultaneously]
```
→ Hard to review outputs, integration nightmare

✅ **2-3 parallel agents max**
```
[Spawns 2-3 agents with clear boundaries]
```

---

❌ **Not reviewing agent output before next step**
```
Agent 1 builds API → immediately spawn Agent 2 without checking Agent 1's work
```
→ Bugs compound through pipeline

✅ **Review between steps**
```
Agent 1 builds API → Review: Does it work? Fix bugs → Then spawn Agent 2
```

---

❌ **Forgetting to pass context**
```
Agent 2: "Integrate with the API"
```
→ Agent 2 doesn't know what API, where it is, what endpoints exist

✅ **Explicit context handoff**
```
Agent 2: "The API is running on localhost:5001 with endpoint GET /flights
          that returns [{id, origin, dest, price}]. Build a UI that calls
          this endpoint..."
```

### Agent Tool Summary

**Key takeaway:** The Agent tool lets you programmatically spawn sub-agents within your main conversation. You remain the orchestrator, deciding when to spawn agents, what prompts to give them, and how to integrate their outputs.

**For this workshop:**
- **Start with 2-3 sub-agents** via Agent tool (Option 2)
- **Write clear, specific prompts** (see Prompt Engineering section)
- **Review each agent's output** before proceeding
- **Pass explicit context** when agents need to work together

**Next:** Now that you know HOW to spawn agents, let's explore the PATTERNS for coordinating them effectively.

---

## THE FOUR FUNDAMENTAL PATTERNS

### Pattern 1: Parallel Execution

**When to use:** Tasks are independent and can happen simultaneously

**How it works:** Start multiple agents at once, each with a separate task

**Example:**
```
Agent 1: "Build a Flask API with endpoints for flight search and booking"
Agent 2: "Build a React UI with search form and results display"
Agent 3: "Write integration tests for the flight booking API"

[All start at the same time, no dependencies]
```

**Advantages:**
- ⚡ Maximum speed - no waiting
- 🎯 Focused agents - each has one clear task
- 🔀 Easy to manage - no coordination needed

**Disadvantages:**
- May produce incompatible outputs
- Requires integration step afterward
- No agent learns from others' work

**Best for:** Early building phases, independent services, time pressure

---

### Pattern 2: Sequential Pipeline

**When to use:** Output of one task feeds into the next

**How it works:** Agent 1 finishes → pass output to Agent 2 → Agent 2 finishes → pass to Agent 3

**Example:**
```
Agent 1: "Design a database schema for flight bookings with tables for
         flights, bookings, passengers, and payments"

[Wait for Agent 1's schema]

Agent 2: "Using this database schema: [paste schema]
         Build a Flask API with CRUD endpoints for all tables"

[Wait for Agent 2's API]

Agent 3: "Using this API: [paste API code]
         Build an admin dashboard to manage flights and view bookings"
```

**Advantages:**
- 🔗 Coherent outputs - each builds on previous
- 📐 Consistent architecture - shared understanding
- 🎓 Later agents learn from earlier ones

**Disadvantages:**
- ⏳ Slower - purely sequential
- 🚫 Blocking - one slow agent delays everyone
- 🔄 Hard to revise - changes ripple through pipeline

**Best for:** Complex systems, architectural consistency, when order matters

---

### Pattern 3: Specialist Roles

**When to use:** Working across multiple quarters/iterations, want agent expertise

**How it works:** Assign each agent a permanent domain (backend, frontend, testing)

**Example:**

**Quarter 1:**
```
Backend Agent: "Build the initial flight search API"
Frontend Agent: "Build the search interface"
Testing Agent: "Write tests for the search flow"
```

**Quarter 2:** (Same agents continue)
```
Backend Agent: "Add booking endpoints to your existing API"
Frontend Agent: "Add booking flow to your existing UI"
Testing Agent: "Extend your tests to cover bookings"
```

**Advantages:**
- 🧠 Context retention - agents remember their previous work
- 🎯 Domain expertise - agents get better at their specialty
- 🏗️ Architectural consistency - each agent maintains their domain
- 💬 Natural handoff points - "Backend Agent's API is at localhost:5001"

**Disadvantages:**
- 🔒 Less flexible - can't easily reassign work
- 🎭 Role confusion - what if frontend needs backend changes?
- 💼 More coordination - need to keep agents aligned

**Best for:** Multi-quarter projects, established architecture, clear boundaries

---

### Pattern 4: Iterative Refinement

**When to use:** Need quality, polish, or fixing issues

**How it works:** Agent 1 builds → Agent 2 reviews/improves → Agent 1 or 3 refines

**Example:**
```
Agent 1: "Build a flight booking UI with search and results"

[Review Agent 1's output]

Agent 2: "Review this code: [paste Agent 1's code]
         Identify 3 UX improvements and 3 code quality issues"

[Agent 2 suggests: add loading states, better error messages, extract components]

Agent 1: "Implement these improvements: [paste Agent 2's suggestions]"
```

**Adversarial Variant:**
```
Agent 1: "Build a booking API endpoint"
Agent 2: "Try to break this API by finding edge cases: [paste API code]"
Agent 1: "Fix these edge cases: [paste Agent 2's findings]"
```

**Advantages:**
- ✨ Higher quality - multiple perspectives
- 🐛 Catches bugs - fresh eyes find issues
- 📚 Learning opportunity - see different approaches

**Disadvantages:**
- ⏱️ More time - multiple passes
- 🔁 Potential loops - agents disagree
- 💬 More context management - longer conversations

**Best for:** Polish phases, quality-critical features, final refinement

---

## PROMPT ENGINEERING FOR AGENTS

### The Anatomy of a Good Agent Prompt

A clear agent prompt has:

1. **Role/Context** - Who is this agent and what's their domain?
2. **Task** - What specifically should they build?
3. **Constraints** - What limitations or requirements?
4. **Output Format** - What should they deliver?
5. **Success Criteria** - How to know if it's done right?

### Example: Poor Prompt

```
"Build a booking system"
```

**Problems:**
- No scope definition
- No tech stack specified
- No clear deliverable
- Agent will make assumptions

### Example: Good Prompt

```
You are a backend API developer building a flight booking system.

Task: Build a Flask REST API with these endpoints:
- GET /flights?origin={code}&dest={code}&date={date}
  Returns: List of available flights with pricing
- POST /bookings
  Body: {flight_id, passenger_name, passenger_email}
  Returns: Booking confirmation with booking_id

Requirements:
- Use SQLite for data storage
- Include 5 mock flights in the database
- Run on port 5001
- Include basic error handling

Deliverable: Complete Python code that I can run with `python app.py`

Success criteria: I can curl these endpoints and get valid JSON responses
```

**Why it's better:**
- ✅ Clear role (backend API developer)
- ✅ Specific endpoints defined
- ✅ Tech stack specified (Flask, SQLite)
- ✅ Port number given
- ✅ Clear deliverable
- ✅ Testable success criteria

### Prompt Templates

#### For Building Something New

```
You are a [role] building [system/feature].

Task: Build [specific component] with these capabilities:
- [Capability 1]
- [Capability 2]
- [Capability 3]

Technical requirements:
- [Tech stack, framework, language]
- [Ports, databases, dependencies]
- [Performance or quality requirements]

Deliverable: [Exactly what they should produce]

Success criteria: [How to verify it works]
```

#### For Integration

```
You are integrating [Component A] with [Component B].

Context:
- Component A (from Agent 1): [Brief description + key details]
- Component B (from Agent 2): [Brief description + key details]

Task: [Specific integration work needed]

Here is the code from Component A:
[Paste relevant code]

Here is the code from Component B:
[Paste relevant code]

Deliverable: [Integrated code or glue code]

Success criteria: [End-to-end flow that should work]
```

#### For Review/Improvement

```
You are a code reviewer specializing in [domain].

Task: Review this code and identify:
- [Number] potential bugs or edge cases
- [Number] code quality improvements
- [Number] UX/functionality enhancements

Code to review:
[Paste code]

Deliverable: List of specific, actionable suggestions with explanations
```

### Prompt Anti-Patterns

❌ **Too Vague**
```
"Make it better"
"Add some features"
"Fix the bugs"
```

❌ **Too Prescriptive**
```
"On line 47, change the variable name to flightSearchResults
and add a comment explaining that this stores the results"
```
(Just do it yourself at this point!)

❌ **Multiple Unrelated Tasks**
```
"Build the API, write tests, create documentation,
and also design a logo"
```
(Split into separate agents!)

❌ **Missing Tech Stack**
```
"Build a web app for booking flights"
```
(Agent will guess - might pick React when you wanted Vue)

---

## CONTEXT MANAGEMENT

### The Context Handoff Challenge

When Agent 2 needs to build on Agent 1's work, what information should you pass?

### Option 1: Full Code Transfer

**When:** Agent 2 needs to modify/extend Agent 1's code

```
Agent 2: "Here is the API built by Agent 1:

[Paste entire API code - could be 100+ lines]

Task: Add these three new endpoints to this API:
- GET /bookings/{id}
- PUT /bookings/{id}
- DELETE /bookings/{id}
```

**Pros:** Complete context, agent can make informed decisions
**Cons:** Long prompts, token usage, harder to read

### Option 2: Interface/Contract Only

**When:** Agent 2 just needs to call Agent 1's output

```
Agent 2: "There is an API running on localhost:5001 with these endpoints:

- GET /flights?origin={}&dest={}&date={}
  Returns: [{id, origin, dest, departure_time, price}, ...]

- POST /bookings
  Body: {flight_id, passenger_name, passenger_email}
  Returns: {booking_id, status, confirmation_code}

Task: Build a React UI that calls these endpoints to:
1. Search for flights
2. Display results
3. Book a selected flight
4. Show confirmation
```

**Pros:** Concise, focuses on interface, easier to read
**Cons:** Agent can't fix issues in Agent 1's code if needed

### Option 3: Hybrid Approach

**When:** Agent 2 needs to integrate, might need to modify

```
Agent 2: "You're integrating a frontend with an existing API.

API Interface:
- Endpoint: GET /flights?origin={}&dest={}&date={}
- Returns: List of flight objects
- Running on: localhost:5001

Current API code structure:
[Paste just the relevant Flask route definitions, ~20 lines]

Task: Build a frontend that calls this API and displays results.
If you find any issues with the API code, suggest fixes.
```

**Pros:** Best of both - interface + ability to debug
**Cons:** Requires judgment on what to include

### Context Management Best Practices

1. **Start minimal, add as needed**
   - First try with just interface/contract
   - If agent struggles, add more code context

2. **Use comments to highlight key points**
   ```
   # Agent 1 built this schema with these tables:
   # - flights (id, origin, dest, departure, price)
   # - bookings (id, flight_id, passenger, email, status)
   ```

3. **Explicitly state what's finished vs. what's next**
   ```
   Agent 1 completed:
   ✅ Database schema
   ✅ Flight search endpoint
   ✅ Basic error handling

   Your task (Agent 2):
   ⬜ Add booking endpoint
   ⬜ Add payment processing
   ```

4. **Reference files/locations when possible**
   ```
   Agent 1 created: ./backend/app.py (running on port 5001)
   Agent 2 should create: ./frontend/app.js (running on port 3000)
   Agent 3 will integrate both
   ```

5. **Use structured summaries for complex systems**
   ```
   System built so far:

   Service 1 - Search API (Agent 1)
   - Tech: Flask
   - Port: 5001
   - Endpoints: GET /flights
   - Database: SQLite at ./flights.db

   Service 2 - Booking API (Agent 2)
   - Tech: Flask
   - Port: 5002
   - Endpoints: POST /bookings, GET /bookings/{id}
   - Calls: Service 1 for flight validation
   ```

---

## PRACTICAL EXAMPLES

### Example 1: Building a Flight Search Page (Parallel)

**Scenario:** You have 30 minutes to build a working flight search with backend and frontend.

**Strategy:** Parallel execution - both agents start together

**Agent 1 Prompt (Backend):**
```
You are a backend developer building a flight search API.

Build a Flask API with this endpoint:
- GET /api/flights?origin={code}&dest={code}&date={YYYY-MM-DD}

Response format:
[
  {
    "id": "FL123",
    "origin": "SFO",
    "destination": "LAX",
    "departure": "2024-01-15T10:00:00",
    "arrival": "2024-01-15T11:30:00",
    "price": 199.99,
    "seats_available": 42
  }
]

Requirements:
- Use SQLite with a flights table
- Include 10 mock flights between various cities
- Enable CORS for frontend access
- Run on port 5001

Deliverable: app.py file I can run with `python app.py`
```

**Agent 2 Prompt (Frontend):**
```
You are a frontend developer building a flight search interface.

Build a single-page app with:

1. Search form with fields:
   - Origin airport (text input)
   - Destination airport (text input)
   - Travel date (date picker)
   - Search button

2. Results display showing:
   - Flight number
   - Origin → Destination
   - Departure and arrival times
   - Price
   - "Book" button (just alert for now)

3. Basic styling (clean, readable, professional)

Technical requirements:
- Vanilla HTML/CSS/JavaScript (no build step)
- Call API at http://localhost:5001/api/flights
- Show loading state while fetching
- Handle errors gracefully
- Serve on port 3000

Deliverable: index.html file I can open in a browser
```

**Timeline:**
- Minutes 0-2: Write both prompts
- Minutes 2-15: Both agents work in parallel
- Minutes 15-20: Test each independently
- Minutes 20-25: Integration (open frontend, ensure it calls backend)
- Minutes 25-30: Demo

**Result:** Working end-to-end feature in 30 minutes.

---

### Example 2: Adding Booking Flow (Sequential Pipeline)

**Scenario:** You have the search page from Example 1. Now add booking capability.

**Strategy:** Sequential pipeline - booking backend must exist before frontend can use it

**Agent 1 Prompt (Booking API):**
```
You are extending an existing Flask API to add booking functionality.

Current API (already running):
- GET /api/flights (returns flight list)

Add this new endpoint:
- POST /api/bookings
  Body: {
    "flight_id": "FL123",
    "passenger_name": "John Doe",
    "passenger_email": "john@example.com"
  }
  Response: {
    "booking_id": "BK456",
    "status": "confirmed",
    "confirmation_code": "ABC123",
    "flight": {<flight details>}
  }

Requirements:
- Add a bookings table to the existing SQLite database
- Validate that flight_id exists and has available seats
- Decrement seats_available when booking succeeds
- Run on the same port 5001

Deliverable: Updated app.py with the new endpoint
```

[Wait for Agent 1 to complete]

**Agent 2 Prompt (Booking UI):**
```
You are extending an existing flight search UI to add booking capability.

Current UI (already exists):
- Search form
- Results display with "Book" buttons

The backend now has a new endpoint:
- POST http://localhost:5001/api/bookings
  Body: {flight_id, passenger_name, passenger_email}
  Returns: {booking_id, status, confirmation_code, flight}

Extend the UI to:

1. When "Book" button clicked, show a modal/form with:
   - Passenger name (input)
   - Email (input)
   - Selected flight details (read-only)
   - "Confirm Booking" button

2. When confirmed, call the booking API

3. On success, show confirmation page with:
   - Booking ID
   - Confirmation code
   - Flight details
   - "Book Another Flight" button

4. Handle errors (flight full, invalid data, etc.)

Deliverable: Updated index.html with booking flow
```

**Timeline:**
- Minutes 0-15: Agent 1 builds booking API
- Minutes 15-25: Agent 2 builds booking UI
- Minutes 25-30: Test and demo

**Result:** Complete search + booking flow

---

### Example 3: Quality Polish (Iterative Refinement)

**Scenario:** You have a working booking system but it feels rough. Polish it.

**Strategy:** Iterative refinement - review then improve

**Agent 1 Prompt (Initial Review):**
```
You are a UX reviewer analyzing a flight booking application.

Here is the current frontend code:
[Paste index.html]

Here is the backend API code:
[Paste app.py]

Identify exactly 3 improvements in each category:

1. User Experience Issues
   (e.g., unclear states, poor error messages, missing feedback)

2. Code Quality Issues
   (e.g., hardcoded values, no validation, poor structure)

3. Missing Features
   (e.g., loading states, input validation, edge case handling)

Format: For each issue, provide:
- What's wrong
- Why it matters
- Specific suggestion for fixing
```

[Wait for Agent 1's review]

**Agent 2 Prompt (Implement Improvements):**
```
You are improving an existing flight booking app based on code review.

Here is the code review feedback:
[Paste Agent 1's review]

Here is the current code:
[Paste the code]

Task: Implement the top 5 most important improvements from the review.

Focus on:
- Quick wins that improve UX
- Critical bugs or edge cases
- Most visible quality improvements

Deliverable: Updated code with comments explaining each improvement
```

**Result:** Polished application with professional feel

---

### Example 4: Multi-Service Architecture (Specialist Roles)

**Scenario:** Build 3 microservices that work together

**Strategy:** Specialist roles - each agent owns a service permanently

**Service Architecture:**
- Service 1: Flight Search API (port 5001)
- Service 2: Booking API (port 5002)
- Service 3: Frontend UI (port 3000)

**Agent 1 - Search Service (Specialist):**

*Quarter 1:*
```
You are the Search Service developer. You own the flight search API.

Build a Flask API on port 5001 with:
- GET /flights?origin={}&dest={}&date={}
- SQLite database with mock flights
- CORS enabled

This service will be called by Service 3 (Frontend) later.
```

*Quarter 2:*
```
You are continuing as the Search Service developer.

Your existing service: [brief reminder of what it does]

Enhance it with:
- GET /flights/{id} - get single flight details
- Add filtering by price range: &min_price={}&max_price={}
- Add sorting: &sort=price|departure

Keep the same port and database.
```

**Agent 2 - Booking Service (Specialist):**

*Quarter 1:*
```
You are the Booking Service developer. You own the booking API.

Build a Flask API on port 5002 with:
- POST /bookings
- GET /bookings/{id}
- SQLite database for bookings

When creating a booking, you'll need to validate the flight exists.
For now, use mock validation (assume flight exists).
Service 1 will provide real flight data later.
```

*Quarter 2:*
```
You are continuing as the Booking Service developer.

Your existing service: [brief reminder]

Enhance it with:
- DELETE /bookings/{id} - cancel booking
- GET /bookings?email={} - lookup by email
- Real validation: Call Service 1 at http://localhost:5001/flights/{id}
  to verify flight exists before booking
```

**Agent 3 - Frontend (Specialist):**

*Quarter 1:*
```
You are the Frontend developer. You own the user-facing web app.

Build a simple HTML/JS app on port 3000 with:
- Flight search form
- Results display
- Calls Service 1 at http://localhost:5001/flights

Service 2 (Booking) isn't ready yet, so "Book" buttons can just alert.
```

*Quarter 2:*
```
You are continuing as the Frontend developer.

Your existing app: [brief reminder]

Now Service 2 (Booking API) is ready at http://localhost:5002/bookings

Add:
- Booking form modal
- Call Service 2 to create bookings
- Confirmation page showing booking details
```

**Advantage:** Each agent builds incrementally on their own service, maintaining architectural consistency.

---

## COMMON PITFALLS & SOLUTIONS

### Pitfall 1: Too Many Agents

**Symptom:**
- Managing 5+ agents simultaneously
- Spending more time coordinating than building
- Agents producing conflicting outputs

**Why it happens:**
- Assumption that more agents = faster
- Trying to parallelize everything
- Not accounting for integration overhead

**Solution:**
```
Bad:  7 agents (API, DB, Frontend, Tests, Docs, Deploy, Monitoring)
Good: 3 agents (Backend with DB, Frontend, Integration & Tests)
```

**Rule of thumb:** 2-3 agents for a 30-minute task, 3-5 for a 60-minute task

---

### Pitfall 2: Agents Waiting Idle

**Symptom:**
- Purely sequential work (Agent 1 → Agent 2 → Agent 3 → ...)
- Agents finish quickly but others not ready
- No time savings vs. single agent

**Why it happens:**
- Choosing sequential pattern when parallel would work
- Over-specifying dependencies
- Not finding parallelizable work

**Solution:**

**Before:**
```
Agent 1: Build API (20 min)
→ Wait →
Agent 2: Build frontend (20 min)
→ Wait →
Agent 3: Write tests (20 min)
Total: 60 minutes
```

**After:**
```
Agent 1: Build API (20 min)      ⎤
Agent 2: Build frontend (20 min)  ⎬ Parallel!
Agent 3: Write tests (20 min)    ⎦
Total: 20 minutes
```

**Ask yourself:** "Does Agent 2 *really* need Agent 1's output, or can they work from a contract?"

---

### Pitfall 3: Conflicting Outputs

**Symptom:**
- Agent 1 uses Flask, Agent 2 assumes Express
- Agent 1 returns JSON format, Agent 2 expects different structure
- Integration takes longer than building

**Why it happens:**
- Not specifying technical contracts upfront
- Agents making different assumptions
- Lack of coordination in prompts

**Solution:**

**Establish contracts first:**
```
Agent 0 (Planning): "Design the API contract between services:
- Service 1 (Search) endpoints and response format
- Service 2 (Booking) endpoints and response format
- Data models (Flight, Booking schemas)

Output: API contract document"

[Review contract]

Now Agent 1 and Agent 2 build to the same contract.
```

**Or be explicit in prompts:**
```
Agent 1: "Build Flask API returning JSON in this exact format:
{
  "flights": [{
    "id": string,
    "price": number,
    ...
  }]
}"

Agent 2: "Build React UI that calls API expecting this JSON format:
{
  "flights": [{
    "id": string,
    "price": number,
    ...
  }]
}"
```

---

### Pitfall 4: Context Loss

**Symptom:**
- Agent 2 doesn't know what Agent 1 built
- Agent 3 redoes work Agent 1 already did
- Agents make incompatible assumptions

**Why it happens:**
- Not passing relevant context between agents
- Assuming agents can "see" each other's work
- Vague handoff prompts

**Solution:**

**Bad handoff:**
```
Agent 2: "Build on what Agent 1 did"
```

**Good handoff:**
```
Agent 2: "Agent 1 built a Flask API with these endpoints:
- GET /flights (running on port 5001)
- Returns: [{id, origin, dest, price, seats}]

Here is Agent 1's database schema:
[Paste schema]

Your task: Build a frontend that calls this API..."
```

**Use explicit summaries:**
```
Agent 1 completed:
✅ Flask API on port 5001
✅ SQLite database at ./data/flights.db
✅ Endpoints: GET /flights, POST /bookings
✅ CORS enabled for localhost:3000

Agent 2 should build:
⬜ React frontend on port 3000
⬜ Calls Agent 1's API
⬜ Shows search results and booking form
```

---

### Pitfall 5: Over-Specification

**Symptom:**
- Writing 500-word prompts
- Spending 10 minutes crafting perfect prompt
- Agents produce exactly what you described (no creativity)

**Why it happens:**
- Fear of agent misunderstanding
- Trying to control every detail
- Not trusting agent capabilities

**Solution:**

**Too specific (micromanaging):**
```
"Create a function called searchFlights that takes three parameters:
origin (string), destination (string), and date (Date object).
On line 1, declare a constant called API_URL. On line 2, use fetch()
with method GET. On line 3, await the response. On line 4..."
```

**Just right (clear goals):**
```
"Build a searchFlights function that calls GET /api/flights with
origin, destination, and date parameters. Return the parsed JSON.
Handle errors with try/catch."
```

**Trust the agent for details, specify the outcomes:**
- ✅ What endpoints to create
- ✅ What data format to return
- ✅ What the success criteria is
- ❌ Exact variable names
- ❌ Exact line-by-line code
- ❌ Low-level implementation

---

### Pitfall 6: No Integration Plan

**Symptom:**
- 3 agents finish successfully
- Outputs don't fit together
- Spend 15 minutes manually integrating

**Why it happens:**
- Focusing on building, not integration
- Assuming "it'll just work"
- No dedicated integration agent or step

**Solution:**

**Reserve an agent for integration:**
```
Agent 1: Build backend (20 min)
Agent 2: Build frontend (20 min)
Agent 3: Integrate 1 & 2, fix issues (10 min) ← The Integration Agent
```

**Or plan integration in final agent's prompt:**
```
Agent 3: "You are integrating the backend from Agent 1 with
the frontend from Agent 2.

Agent 1 built: [summary + code]
Agent 2 built: [summary + code]

Your tasks:
1. Ensure frontend calls correct backend URLs
2. Fix any CORS issues
3. Handle errors on frontend
4. Add loading states
5. Test end-to-end flow and fix bugs

Deliverable: Fully integrated, working system"
```

---

### Pitfall 7: Ignoring Agent Output Quality

**Symptom:**
- Agent produces code with bugs
- You paste it into next agent without review
- Bugs compound through the pipeline

**Why it happens:**
- Treating agents as infallible
- Time pressure (no review time)
- Trust in automation

**Solution:**

**Always review agent outputs before handoff:**

```
Agent 1: [Builds API]

You: [Review Agent 1's code]
- Does it run?
- Does it meet requirements?
- Are there obvious bugs?
- Is it ready for Agent 2?

If issues found:
  Agent 1: "Fix these issues: [list]"
  [Review again]

If good:
  Agent 2: [Build next component]
```

**Quick review checklist (2 minutes):**
- [ ] Does it run without errors?
- [ ] Does it match the prompt requirements?
- [ ] Are there obvious bugs or missing pieces?
- [ ] Is it ready for the next agent to use?

**Don't blindly chain agents!**

---

## ADVANCED TECHNIQUES

### Technique 1: Meta-Agent (Orchestrator Agent)

**Concept:** Use one agent to plan and coordinate other agents

**When to use:** Complex projects where you want AI help with coordination

**Example:**

**Meta-Agent Prompt:**
```
You are a technical architect planning a multi-agent build.

Project: Flight booking web application with search and booking

Create a plan that divides this work between 3 agents optimally.
For each agent, specify:
- Agent role/specialty
- Specific task
- Inputs needed (from other agents or standalone)
- Outputs produced
- Estimated time
- Dependencies on other agents

Goal: Maximize parallel work while ensuring outputs integrate cleanly.
```

**Meta-Agent Output:**
```
Agent 1 (Backend - Search Service):
- Task: Build Flask API for flight search
- Inputs: None (standalone)
- Outputs: Running API on port 5001
- Time: 20 minutes
- Dependencies: None
- Parallel with: Agent 2

Agent 2 (Backend - Booking Service):
- Task: Build Flask API for bookings
- Inputs: None initially (will integrate later)
- Outputs: Running API on port 5002
- Time: 20 minutes
- Dependencies: None
- Parallel with: Agent 1

Agent 3 (Frontend):
- Task: Build UI calling both APIs
- Inputs: Agent 1's API contract, Agent 2's API contract
- Outputs: Frontend on port 3000
- Time: 25 minutes
- Dependencies: Needs API contracts (not full implementation)
- Can start after: 5 minutes (once contracts defined)
```

**Then execute the plan:**
Follow meta-agent's architecture, write prompts for Agent 1, 2, 3.

---

### Technique 2: Adversarial Agents

**Concept:** One agent builds, another tries to break it

**When to use:** Quality-critical features, security, edge case discovery

**Example:**

**Agent 1 (Builder):**
```
Build a flight booking API endpoint:
POST /bookings
Body: {flight_id, passenger_name, passenger_email}

Include basic validation and error handling.
```

**Agent 2 (Breaker):**
```
Here is a booking API endpoint:
[Paste Agent 1's code]

Try to break it. Find:
- 5 invalid inputs that should be rejected but aren't
- 3 edge cases that cause errors
- 2 security issues
- 1 race condition or concurrency problem

For each issue, provide:
- The problematic input/scenario
- What goes wrong
- Severity (critical/major/minor)
```

**Agent 1 (Fixer):**
```
Here are issues found in your code:
[Paste Agent 2's findings]

Fix all critical and major issues.
Add tests to prevent regression.
```

**Result:** More robust code than single-pass building

---

### Technique 3: Test-Driven Multi-Agent

**Concept:** One agent writes tests, another implements to pass them

**When to use:** When you want strong test coverage, TDD approach

**Example:**

**Agent 1 (Test Writer):**
```
Write comprehensive pytest tests for a flight booking API with:

POST /bookings endpoint:
- Should create booking with valid data
- Should reject if flight_id doesn't exist
- Should reject if no seats available
- Should reject invalid email format
- Should reject missing required fields
- Should return correct booking object structure

Use pytest and mock database.
Don't implement the API, just write tests.
```

**Agent 2 (Implementer):**
```
Here are tests for a booking API:
[Paste Agent 1's tests]

Implement the Flask API that makes all these tests pass.

Requirements:
- All tests must pass
- No extra features beyond what tests require
- Clean, readable code
```

**Result:** 100% test coverage, clear requirements, validated implementation

---

### Technique 4: Specialized Review Agents

**Concept:** Different agents review different aspects

**When to use:** Quality polish phase, pre-demo refinement

**Example:**

**Agent 1 (Security Reviewer):**
```
Review this code for security issues:
[Paste code]

Check for:
- SQL injection vulnerabilities
- XSS risks
- Hardcoded secrets
- Insufficient input validation
- CORS misconfigurations
```

**Agent 2 (Performance Reviewer):**
```
Review this code for performance issues:
[Paste code]

Check for:
- N+1 queries
- Missing indexes
- Inefficient algorithms
- Memory leaks
- Blocking operations
```

**Agent 3 (UX Reviewer):**
```
Review this code for UX issues:
[Paste code]

Check for:
- Missing loading states
- Poor error messages
- Unclear user feedback
- Accessibility problems
- Mobile responsiveness
```

**Then prioritize and fix:**
Combine all feedback, pick top issues, implement fixes.

---

### Technique 5: Layered Refinement

**Concept:** Multiple passes, each improving a different aspect

**When to use:** Transforming rough code into polished product

**Example:**

**Pass 1 - Agent 1 (Make it work):**
```
Build a basic flight search UI.
Focus on functionality, don't worry about styling.
```

**Pass 2 - Agent 2 (Make it pretty):**
```
Here is a working flight search UI:
[Paste Agent 1's code]

Keep all functionality, improve visual design:
- Professional color scheme
- Better layout and spacing
- Smooth transitions
- Loading states
- Error styling
```

**Pass 3 - Agent 3 (Make it fast):**
```
Here is a flight search UI:
[Paste Agent 2's code]

Keep all functionality and design, optimize performance:
- Debounce search input
- Cache search results
- Lazy load images
- Minimize reflows
- Add service worker for offline
```

**Result:** Production-quality interface

---

### Technique 6: Domain-Specific Agent Teams

**Concept:** Pre-defined agent teams for common scenarios

**Example Teams:**

**Full-Stack Web App Team:**
- Agent 1: Backend API (Flask/Express specialist)
- Agent 2: Frontend UI (React/Vue specialist)
- Agent 3: Database & Data (Schema design, migrations)
- Agent 4: Integration & Testing

**Data Pipeline Team:**
- Agent 1: Data Extraction (APIs, scraping)
- Agent 2: Data Transformation (cleaning, normalization)
- Agent 3: Data Loading (database, storage)
- Agent 4: Validation & Quality

**DevOps/Tooling Team:**
- Agent 1: Docker/containerization
- Agent 2: Scripts & automation
- Agent 3: Configuration & infrastructure
- Agent 4: Documentation

**Reuse these teams across projects for consistency.**

---

### Technique 7: Creating Reusable Skills (Optional - Advanced)

**Concept:** Package common agent workflows into reusable slash commands (skills)

**When to use:** Repeated workflows across quarters or projects

**What are skills?**

Skills are custom slash commands you create for Claude Code. They're like macros or shortcuts for common multi-agent workflows.

**Example:** Instead of writing the same "create new service" prompt every quarter, create a `/new-service` skill.

**Syntax:**
```
User: /new-service booking
[Skill expands into a full agent workflow]
```

#### Should You Create Skills for This Workshop?

**Short answer: Optional and advanced.** Most directors succeed using agents directly.

**When skills are useful:**
- You have a workflow you'll repeat 3+ times
- Multi-quarter projects where patterns emerge
- You want to save time on repeated setups
- You're comfortable with YAML/JSON skill definitions

**When to skip skills:**
- First time playing this game
- One-off tasks
- Still learning multi-agent patterns
- Time pressure (creating skills takes time)

#### Example Skills Directors Might Create

**Skill 1: `/new-service` - Create a new microservice**

```yaml
name: new-service
description: Create a new microservice with boilerplate
prompt: |
  You are creating a new microservice called {{service_name}}.

  Spawn an agent to build:
  - Flask app with basic structure
  - SQLite database setup
  - CORS enabled
  - Running on port {{port}}
  - Health check endpoint GET /health

  Agent prompt:
  "Build a Flask microservice called {{service_name}} running on port {{port}}.
   Include basic structure, database setup, CORS, and health check endpoint."
```

**Usage:**
```
Director: /new-service booking 5002
[Skill spawns agent to create booking service on port 5002]
```

---

**Skill 2: `/qa-check` - Quality assurance review**

```yaml
name: qa-check
description: Run QA review on code
prompt: |
  Spawn a QA agent to review the current codebase.

  Agent prompt:
  "You are a QA specialist. Review all code in the current directory.

   Check for:
   - 3 potential bugs or edge cases
   - 3 code quality issues
   - 3 UX improvements

   Format: Specific, actionable suggestions with severity (critical/major/minor)"
```

**Usage:**
```
Director: /qa-check
[Skill spawns QA review agent]
```

---

**Skill 3: `/integrate-services` - Service integration**

```yaml
name: integrate-services
description: Integrate two microservices
prompt: |
  Spawn an integration agent to connect services.

  Agent prompt:
  "You are integrating {{service_a}} with {{service_b}}.

   Tasks:
   1. Ensure {{service_b}} can call {{service_a}}'s endpoints
   2. Fix any CORS issues
   3. Add error handling for failed requests
   4. Test end-to-end flow

   Service A is on port {{port_a}}, Service B is on port {{port_b}}."
```

**Usage:**
```
Director: /integrate-services search booking 5001 5002
[Skill spawns integration agent]
```

---

**Skill 4: `/api-contract` - Define API contract**

```yaml
name: api-contract
description: Design API contract before building
prompt: |
  Spawn a planning agent to design an API contract.

  Agent prompt:
  "Design an API contract for {{service_name}}.

   Define:
   - Endpoints (method, path, purpose)
   - Request formats (body, query params)
   - Response formats (success, errors)
   - Status codes
   - Data models

   Output: API contract document in markdown",
  "subagent_type": "Plan"
```

**Usage:**
```
Director: /api-contract booking-service
[Skill spawns planning agent to design contract]
```

#### How Skills Relate to Multi-Agent Workflows

Skills **automate agent spawning**. Instead of manually writing agent prompts, skills provide templates.

**Without skill:**
```
Main conversation:
Director: "I need a QA review"
Claude: [Spawns agent with QA prompt]
```

**With skill:**
```
Main conversation:
Director: /qa-check
[Skill automatically spawns agent with predefined QA prompt]
```

**Key difference:** Skills save time on repeated patterns, but you still get agents doing the work.

#### Creating a Simple Skill

Skills are defined in YAML or JSON and stored in your Claude Code configuration.

**Basic structure:**
```yaml
name: skill-name
description: What this skill does
prompt: |
  The prompt that will be executed when skill is invoked.
  Can include {{parameters}} for customization.
```

**Example - Simple skill:**
```yaml
name: hello-world
description: Test skill
prompt: |
  Say "Hello, {{name}}! This is a skill."
```

**Usage:**
```
User: /hello-world Alice
Claude: "Hello, Alice! This is a skill."
```

**Example - Skill that spawns agent:**
```yaml
name: build-api
description: Build a REST API
prompt: |
  Spawn an agent to build a {{framework}} API for {{domain}}.

  Agent prompt:
  "You are a backend developer. Build a {{framework}} REST API for {{domain}}.
   Include basic CRUD endpoints, database setup, and error handling.
   Run on port {{port}}."
```

**Usage:**
```
User: /build-api Flask flights 5001
[Skill spawns agent to build Flask flights API on port 5001]
```

#### Learning More About Skills

Skills are documented at: https://code.claude.com/docs/en/skills

**For this workshop:**
- Skills are **optional**
- Focus on mastering multi-agent patterns first
- Consider skills for Q3+ if you find repeated patterns
- Don't create skills in Q1 (not enough time)

**If you do create skills:**
- Keep them simple
- Test them before relying on them
- Document what each skill does
- Share useful skills with other directors

---

## DECISION FRAMEWORK

### When to Use Multiple Agents vs. Single Agent

**Use Single Agent when:**
- ✅ Task is small (< 15 minutes)
- ✅ Task is simple (one file, one function)
- ✅ No clear parallelization opportunity
- ✅ You're prototyping/exploring
- ✅ Context is important (agent needs full picture)

**Use Multiple Agents when:**
- ✅ Task is large (> 20 minutes)
- ✅ Clear subtasks exist (frontend + backend + tests)
- ✅ Subtasks are independent (can parallelize)
- ✅ Different expertise needed (React + Python + DevOps)
- ✅ You want faster completion
- ✅ You want modular outputs

### How Many Agents?

**2 Agents:**
- Simple decomposition (backend + frontend)
- Limited time (< 30 min)
- First time trying multi-agent

**3 Agents:**
- Sweet spot for most projects
- Standard pattern: Build + Build + Integrate
- Or: Build + Test + Refine
- 30-60 minute tasks

**4-5 Agents:**
- Complex projects (multiple services)
- 60+ minute tasks
- Specialist roles across quarters
- Full-stack applications

**6+ Agents:**
- Usually too many
- Coordination overhead high
- Consider if really needed

### Which Pattern to Choose?

**Choose Parallel when:**
- Subtasks are independent
- Speed is priority
- You have clear interfaces/contracts

**Choose Sequential when:**
- Output of A feeds into B
- Architectural consistency critical
- One agent needs to build on another

**Choose Specialist when:**
- Multi-quarter project
- Want context retention
- Clear domain boundaries

**Choose Iterative when:**
- Quality more important than speed
- Refinement/polish phase
- Initial output needs improvement

### Integration Strategy Decision

**Mock Integration (Recommended for Q1-Q3):**
```
✅ Faster development
✅ No coordination needed
✅ Each person works independently
❌ Not "real" end-to-end
```

**Real Integration (Optional for Q4):**
```
✅ Actual microservices working together
✅ Learn real integration challenges
❌ Slower, needs coordination
❌ Networking complexity
```

**Decision:** Start with mocks, attempt real integration only if time permits and value is clear.

---

## QUICK REFERENCE

### How to Spawn Agents (Quick Summary)

**Recommended: Use Agent Tool (Sub-Agents)**
```
Main conversation → Spawn sub-agents → Review outputs → Integrate

Example:
{
  "description": "Build Flask API",
  "prompt": "You are a backend developer. Build a Flask API with endpoint
             GET /flights. Use SQLite. Run on port 5001."
}
```

**Alternative: Multiple Tabs**
- Open 2-3 Claude Code tabs
- Each tab = one agent conversation
- Manually copy-paste between tabs

**Advanced: Agent Teams**
- Persistent specialist agents
- Multi-quarter projects
- Agents communicate with each other

**Decision:** Start with Agent Tool (Sub-Agents) for most scenarios.

---

### Prompt Template Cheat Sheet

**Building New Feature:**
```
You are a [role] building [feature].

Task: Build [specific thing] with [capabilities].

Tech requirements: [stack, ports, dependencies]

Deliverable: [what to produce]

Success: [how to verify]
```

**Integration:**
```
Integrate [A] with [B].

Context:
- A does: [summary]
- B does: [summary]

Here's A's code: [paste]
Here's B's code: [paste]

Task: [integration work]

Deliverable: [integrated output]
```

**Review:**
```
Review this [type] code:
[paste code]

Find [N] issues in:
- [Category 1]
- [Category 2]
- [Category 3]

Format: Specific, actionable suggestions
```

### Common Agent Roles

- **Backend API Developer** - Builds REST APIs, databases
- **Frontend Developer** - Builds UIs, user interactions
- **Integration Engineer** - Connects services, fixes compatibility
- **Test Engineer** - Writes tests, finds edge cases
- **DevOps Engineer** - Deployment, Docker, scripts
- **Code Reviewer** - Reviews quality, suggests improvements
- **Security Auditor** - Finds vulnerabilities
- **Performance Optimizer** - Improves speed, efficiency

### Timing Guidelines

**30-minute quarter:**
- 2-3 agents max
- 20 min building + 5 min integration + 5 min buffer

**60-minute quarter:**
- 3-4 agents
- 45 min building + 10 min integration + 5 min buffer

**Always reserve:**
- Integration time (5-10 min)
- Review time (2-5 min between agents)
- Buffer for unexpected issues (5 min)

### Context Handoff Checklist

When passing work from Agent 1 to Agent 2:

- [ ] What Agent 1 built (summary)
- [ ] Where it runs (port, location)
- [ ] Key interfaces (API endpoints, function signatures)
- [ ] Data formats (JSON structure, schemas)
- [ ] What worked / what didn't
- [ ] What Agent 2 should build
- [ ] How they'll integrate

### Red Flags (Stop and Reconsider)

🚩 Writing 500+ word prompts → Simplify or split task
🚩 Agent waiting 10+ min for another → Bad parallelization
🚩 Manual integration taking 15+ min → Poor contracts
🚩 Agents producing incompatible code → Missing alignment
🚩 Same work done twice → Context loss
🚩 Using 6+ agents → Overcomplicated
🚩 Can't explain why using multiple agents → Use one

---

## WORKSHOP TIPS

### Before You Start

1. **Understand how to spawn agents** (review Claude Code Mechanics section)
2. **Read one full example** (from Practical Examples section)
3. **Choose your pattern** (Parallel? Sequential? Specialist?)
4. **Decide: Multiple Tabs or Agent Tool?** (Agent Tool recommended for 3+ agents)
5. **Sketch your agent breakdown** (2-3 sentences per agent)
6. **Identify integration points** (where agents connect)
7. **Estimate timing** (X min per agent + integration buffer)

### During Building

1. **Write all prompts first** (before starting any agent)
2. **Start parallel agents together** (don't wait if independent)
3. **Review each agent output** (2-min sanity check)
4. **Pass explicit context** (don't assume agents know things)
5. **Reserve integration time** (last 5-10 minutes)

### When Stuck

**Agent produced broken code:**
- Review requirements - were they clear?
- Give agent the error message and ask to fix
- If stuck 2x, simplify the task

**Agents aren't integrating:**
- Check interfaces match (endpoints, data formats)
- Use integration agent to bridge gap
- Worst case: mock the integration for demo

**Running out of time:**
- Reduce scope (drop one feature)
- Drop from 3 agents to 2
- Show partial demo (what works)
- Next quarter, finish what's incomplete

### After Demo

**Reflect:**
- What agent pattern worked best?
- What would you do differently?
- What was harder than expected?
- What was easier than expected?
- How will you improve next quarter?

---

## CONCLUSION

**Multi-agent orchestration is a skill.** Like any skill, you'll improve with practice.

**Start simple:**
- First time: Use Agent Tool with 2 agents, parallel pattern, 30 minutes
- Second time: 3 agents via Agent Tool, try sequential
- Third time: Experiment with specialist roles
- Fourth time: Try advanced techniques (Agent Teams, skills)

**Key principles:**
1. **Clear prompts** - Specific role, task, deliverable
2. **Explicit context** - Pass information between agents
3. **Reserve integration time** - Don't assume it "just works"
4. **Review outputs** - Agents aren't perfect
5. **Parallelize when possible** - Maximum speed
6. **Don't overcomplicate** - 2-3 agents often optimal

**You're the orchestrator.** The agents are powerful tools, but you decide:
- Which pattern to use
- How to divide work
- What context to pass
- When to integrate
- What quality bar to hit

**Trust yourself.** If a pattern isn't working, switch. If an agent produces poor output, revise your prompt. Adapt, experiment, learn.

---

**Good luck building! 🚀**

*Remember: The best way to learn multi-agent orchestration is to orchestrate multiple agents building something real.*
