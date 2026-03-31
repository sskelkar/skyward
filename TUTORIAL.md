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

### How Claude Code CLI Works

**Important context:** When you use Claude Code CLI, you're already talking to Claude in a conversation. You don't need to write code or API calls to spawn agents - you just **ask Claude to spawn agents** using natural language, and Claude will use the Agent tool internally.

**Example:**
```
You (in CLI): "I need to build a flight booking app. Spawn two agents in parallel:
               one for the Flask API and one for the React UI."

Claude: "I'll spawn two agents to work on this in parallel."
        [Claude uses Agent tool internally]
        [Agent 1 works on Flask API]
        [Agent 2 works on React UI]
        "Both agents have completed. Here are the results..."
```

**Key insight:** You don't invoke the Agent tool yourself - **you ask Claude to coordinate agents**, and Claude handles the tool calls.

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

### How to Actually Spawn Agents in Claude Code CLI

**Method 1: Just Ask Claude to Spawn Agents**

The simplest approach - describe what you want and let Claude coordinate.

**Example conversation:**
```
You: "Build a flight booking system with separate backend and frontend services.
      Use two agents working in parallel."

Claude: "I'll spawn two agents to work on this in parallel:
         - Agent 1: Backend API developer (Flask, port 5001)
         - Agent 2: Frontend developer (React, port 3000)

         Let me start both agents now."

         [Claude internally calls Agent tool twice]

         [After agents complete]

Claude: "Both agents have completed their work. Here's what they built:

         **Agent 1 (Backend):** Created a Flask API with flight search endpoint...
         **Agent 2 (Frontend):** Created a React app with search form...

         Would you like me to test the integration?"
```

**What's happening behind the scenes:**
- Claude receives your request
- Claude decides to use the Agent tool
- Claude formulates prompts for each agent
- Claude spawns agents (parallel or sequential)
- Claude reviews outputs and reports back to you

---

**Method 2: Give Claude Explicit Instructions**

For more control, tell Claude exactly how to structure the agents.

**Example conversation:**
```
You: "Spawn three agents sequentially:

      Agent 1: Design a database schema for flight bookings with flights,
               bookings, and payments tables.

      Agent 2: Using Agent 1's schema, build a Flask API on port 5001
               with CRUD endpoints.

      Agent 3: Build a React admin dashboard that calls Agent 2's API."

Claude: "I'll execute this as a sequential pipeline. Starting with Agent 1..."

         [Spawns Agent 1]

Claude: "Agent 1 has completed the schema. Here's what they designed:
         [shows schema]

         Now spawning Agent 2 to build the API using this schema..."

         [Spawns Agent 2 with schema context]

Claude: "Agent 2 has built the API. Now spawning Agent 3 for the dashboard..."

         [Spawns Agent 3 with API context]

Claude: "All three agents completed. Here's the integrated result..."
```

**Benefits of explicit instructions:**
- You control the sequence (parallel vs sequential)
- You specify what context to pass between agents
- You can request specific technologies or approaches

---

**Method 3: Ask Claude to Plan First, Then Execute**

For complex projects, have Claude plan the agent strategy before spawning.

**Example conversation:**
```
You: "I need to build a flight booking system with search, booking, and
      payment features. What's the best multi-agent strategy?"

Claude: "Here's my recommended approach:

         **Phase 1 - Parallel (20 min):**
         - Agent 1: Build Search API (port 5001)
         - Agent 2: Build Booking API (port 5002)

         **Phase 2 - Sequential (15 min):**
         - Agent 3: Build unified frontend calling both APIs (port 3000)
         - Agent 4: Write integration tests

         This maximizes parallelism while ensuring clean integration.
         Should I proceed with this plan?"

You: "Yes, proceed."

Claude: "Starting Phase 1 with Agent 1 and Agent 2 in parallel..."
         [Executes the plan]
```

---

**Method 4: Spawn Background Agents for Long Tasks**

For tasks that take several minutes, ask Claude to run them in the background.

**Example conversation:**
```
You: "Generate a realistic flight database with 1000 flights. Run this in
      the background while I work on the frontend."

Claude: "I'll spawn an agent to generate the database in the background.
         You can continue working, and I'll notify you when it's complete."

         [Spawns background agent]

Claude: "Background agent started. What would you like to work on in the meantime?"

You: "Build the React frontend for flight search."

Claude: "I'll spawn a frontend agent now..."

         [Later, background agent completes]

Claude: "The database generation agent has finished. The flights.db file
         is ready with 1000 flights across 50 airports."
```

---

### Using Agent Teams in Claude Code CLI

**Agent Teams are created and managed through natural conversation.**

#### Creating a Team

**Example conversation:**
```
You: "Create an agent team for building a flight booking system.
      The team should have:
      - Backend specialist (Flask, databases)
      - Frontend specialist (React, UI/UX)
      - QA specialist (testing, quality)

      Make this a persistent team for the whole project."

Claude: "I've created a team called 'flight-booking-team' with three specialists:
         - Backend Agent (backend-dev)
         - Frontend Agent (frontend-dev)
         - QA Agent (qa-specialist)

         This team will persist across our conversation and coordinate with each other.
         What should the team work on first?"
```

#### Working with the Team

**Example conversation:**
```
You: "Team: Build a flight search feature with backend API and frontend."

Backend Agent: "I'll create a Flask API with GET /flights endpoint on port 5001..."
               [builds API]

Frontend Agent: "I see the backend is creating the API. I'll build a React UI
                 that calls localhost:5001/flights..."
                [builds UI]

QA Agent: "I'll review both implementations for bugs and integration issues..."
          [reviews]

Claude: "The team has completed the flight search feature. Here's a summary:
         - Backend: Flask API on port 5001 ✓
         - Frontend: React app on port 3000 ✓
         - QA: 2 minor issues found and fixed ✓"

You: "Team: Now add booking functionality."

[Team continues, building on their previous work]
```

#### Team Benefits

**Why use teams:**
- Agents remember their previous work (persistent context)
- Agents can ask each other questions
- Simulates real organizational structure
- Great for multi-quarter projects (Q1-Q6)

**When NOT to use teams:**
- One-off tasks (sub-agents are simpler)
- You're new to multi-agent (start with sub-agents first)
- Simple 2-agent parallel work

#### Team Commands

**Create team:**
```
You: "Create a team with [list roles]"
```

**Address the team:**
```
You: "Team: [task description]"
```

**Address specific team member:**
```
You: "Backend Agent: Add a new endpoint for flight details"
```

**Check team status:**
```
You: "What has the team built so far?"
```

**Disband team (optional):**
```
You: "Disband the flight-booking-team"
```

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

### Practical CLI Examples: What It Actually Looks Like

#### Example 1: Parallel Execution

**Scenario:** Build backend and frontend simultaneously.

**Your message in Claude Code CLI:**
```
Build a flight booking app with:
- Flask API on port 5001 with GET /flights endpoint
- React UI on port 3000 that calls the API

Spawn two agents in parallel for this.
```

**Claude's response:**
```
I'll spawn two agents to work on this in parallel.

[Agent 1: Build search API]
Building Flask API with flight search endpoint on port 5001...

[Agent 2: Build search UI]
Building React UI with search form on port 3000...

[Both agents working simultaneously...]

---

Agent 1 (Backend) completed:
✓ Created Flask API with GET /flights endpoint
✓ SQLite database with 10 mock flights
✓ CORS enabled for localhost:3000
✓ Running on port 5001

Files created:
- backend/app.py
- backend/flights.db

---

Agent 2 (Frontend) completed:
✓ Created React app with search form
✓ Displays flight results in a table
✓ Calls http://localhost:5001/flights
✓ Includes loading states and error handling
✓ Running on port 3000

Files created:
- frontend/index.html
- frontend/app.js
- frontend/styles.css

---

Both agents completed successfully. To run:
1. Terminal 1: cd backend && python app.py
2. Terminal 2: cd frontend && python -m http.server 3000
3. Open http://localhost:3000

Would you like me to test the integration?
```

**What happened behind the scenes:**
Claude used the Agent tool twice in parallel with these prompts:

```
Agent 1 internal prompt:
"You are a backend developer. Build a Flask API for flight search.
 Endpoint: GET /flights?origin={code}&dest={code}&date={date}
 Use SQLite with 10 mock flights. CORS enabled. Port 5001."

Agent 2 internal prompt:
"You are a frontend developer. Build a flight search interface.
 Call API at http://localhost:5001/flights. Vanilla HTML/CSS/JS.
 Port 3000."
```

#### Example 2: Sequential Pipeline

**Scenario:** Agent 2 needs Agent 1's output.

**Your message in Claude Code CLI:**
```
Build a booking system in stages:

1. First agent: Design database schema with flights, bookings, payments tables
2. Second agent: Build Flask API using that schema with CRUD endpoints

Run these sequentially so the second agent can use the first agent's schema.
```

**Claude's response:**
```
I'll run these agents sequentially. Starting with the schema design...

[Agent 1: Design database schema]
Designing database schema for flight booking system...

---

Agent 1 (Schema Designer) completed:

Created schema with three tables:
- flights (id, origin, destination, departure, arrival, price, seats_available)
- bookings (id, flight_id, passenger_name, email, status, created_at)
- payments (id, booking_id, amount, payment_method, status, processed_at)

Here's the schema:
[Shows SQL CREATE TABLE statements]

---

Now spawning Agent 2 to build the API using this schema...

[Agent 2: Build booking API]
Building Flask API with the schema from Agent 1...

---

Agent 2 (API Developer) completed:

✓ Created Flask API with endpoints:
  - POST /bookings (create booking)
  - GET /bookings/{id} (get booking details)
  - DELETE /bookings/{id} (cancel booking)
✓ Uses the exact schema from Agent 1
✓ Includes validation and error handling
✓ Running on port 5002

Files created:
- booking-api/app.py
- booking-api/schema.sql

---

Sequential pipeline completed. The API is ready to use.
```

#### Example 3: Background Agents for Long Tasks

**Scenario:** Agent needs > 2 minutes, don't want to block.

**Your message in Claude Code CLI:**
```
Generate a realistic flight database with 1000 flights across 50 airports.
This will take a while, so run it in the background.

While that runs, I'll work on building the frontend UI.
```

**Claude's response:**
```
I'll spawn an agent to generate the database in the background. You can
continue working on other tasks and I'll notify you when it completes.

[Agent: Generate test data - BACKGROUND]
Generating 1000 flights across 50 US airports...
(Running in background...)

---

The database generation is running in the background.
What would you like me to work on now?
```

**You continue:**
```
Build the React frontend for flight search.
```

**Claude:**
```
[Agent: Build frontend]
Building React flight search UI...

---

Agent (Frontend) completed:
✓ Created React app with search form
✓ Flight results display
✓ Running on port 3000

Files created:
- frontend/src/App.js
- frontend/src/components/SearchForm.js
- frontend/src/components/FlightList.js

---

[Background agent notification]
The database generation agent has completed!

✓ Generated flights.db with 1000 flights
✓ 50 US airports (SFO, LAX, JFK, ORD, etc.)
✓ Departure times spread over next 30 days
✓ Prices ranging from $50-$800
✓ Varying seat availability

File created: backend/flights.db

All tasks completed!
```

#### Example 4: Specialized Explore Agent

**Scenario:** Need to understand existing codebase structure.

**Your message in Claude Code CLI:**
```
I need to understand how authentication works in this codebase.
Use an Explore agent to find all auth-related code and explain the flow.
```

**Claude's response:**
```
I'll spawn an Explore agent to search the codebase for authentication code.

[Agent: Explore - Find authentication code]
Searching codebase for authentication patterns...

---

Agent (Explore) completed:

Found authentication implementation across 5 files:

**1. backend/auth/middleware.py**
- authenticate_request() - Validates JWT tokens
- require_auth() - Decorator for protected endpoints

**2. backend/auth/tokens.py**
- generate_token() - Creates JWT tokens
- verify_token() - Validates and decodes tokens

**3. backend/routes/auth.py**
- POST /login - Login endpoint (generates token)
- POST /logout - Logout endpoint (invalidates token)

**4. frontend/src/utils/auth.js**
- storeToken() - Saves JWT to localStorage
- getToken() - Retrieves token for API calls

**5. backend/config.py**
- JWT_SECRET - Secret key for signing tokens
- TOKEN_EXPIRY - Set to 24 hours

**Authentication Flow:**
1. User posts credentials to POST /login
2. Backend validates, generates JWT token
3. Frontend stores token in localStorage
4. All API requests include "Authorization: Bearer <token>" header
5. authenticate_request() middleware validates token on each request

**Security concerns found:**
- JWT_SECRET is hardcoded (should use environment variable)
- No token refresh mechanism
- No rate limiting on login endpoint
```

### Key Insight: Natural Language, Not Code

**You don't write JSON or code in Claude Code CLI.** You just describe what you want in natural language.

**What you DON'T do:**
```
You: {
       "description": "Build API",
       "prompt": "Build a Flask API...",
       "subagent_type": "general-purpose"
     }
```
❌ This is wrong - you're not calling APIs directly

**What you DO do:**
```
You: "Build a Flask API for flight search. Use an agent for this."
```
✓ This is right - just describe what you want

**Claude handles all the tool calls internally.** Your job is to:
- Describe the task clearly
- Specify if you want parallel or sequential agents
- Provide context for agents to use
- Review outputs and give feedback

**Think of it like delegating to a project manager:**
- You don't tell the PM exactly what JSON to write
- You describe what you need and let them figure out the details
- You review results and provide direction

---

### Common Mistakes with Agent Spawning

❌ **Vague requests**
```
You: "Build the backend"
```
→ Claude doesn't know tech stack, ports, endpoints, etc.

✅ **Specific requests**
```
You: "Build a Flask API on port 5002 for flight bookings.
      Include POST /bookings endpoint that accepts flight_id, passenger_name,
      and email. Return booking_id, status, and confirmation_code.
      Use SQLite for storage."
```

---

❌ **Too many parallel agents**
```
You: "Spawn 7 agents to build all these features at once..."
```
→ Hard to review outputs, integration nightmare

✅ **2-3 parallel agents max**
```
You: "Spawn 2 agents in parallel: one for backend API, one for frontend UI"
```

---

❌ **Not reviewing agent output before next step**
```
You: "Build the API with Agent 1, then immediately have Agent 2 build the UI"
```
→ Bugs compound through pipeline

✅ **Review between steps**
```
You: "Build the API with Agent 1"
[Claude builds API]
You: [Reviews output, tests it]
You: "Good. Now spawn Agent 2 to build UI that calls this API"
```

---

❌ **Forgetting to pass context**
```
You: "Now spawn an agent to integrate with the API"
```
→ Agent doesn't know what API, where it is, what endpoints exist

✅ **Explicit context handoff**
```
You: "Spawn an agent to build a frontend. The backend API is running on
      localhost:5001 with GET /flights endpoint that returns an array of
      flight objects with id, origin, dest, and price fields."
```

### Complete End-to-End CLI Example

Here's a realistic conversation showing the full multi-agent workflow in Claude Code CLI:

**You:**
```
I'm building a flight booking system for Q1. I want to use a multi-agent
approach with:
1. One agent to build the search API
2. One agent to build the search UI
3. Run them in parallel to save time

Use Flask for backend (port 5001) and React for frontend (port 3000).
```

**Claude:**
```
I'll spawn two agents to work on this in parallel - a backend developer
for the search API and a frontend developer for the search UI.

[Spawning Agent 1: Backend Search API]
[Spawning Agent 2: Frontend Search UI]

Both agents are now working...
```

**Claude (after ~5 minutes):**
```
Agent 1 (Backend) completed:
✓ Flask API with GET /flights endpoint
✓ Query params: origin, destination, date
✓ Returns: Array of flight objects
✓ SQLite database with 10 mock flights
✓ CORS enabled for localhost:3000
✓ Running on port 5001

Files: backend/app.py, backend/flights.db

Agent 2 (Frontend) completed:
✓ React app with search form
✓ Input fields: origin, destination, date
✓ Displays results in a table
✓ Calls http://localhost:5001/flights
✓ Loading states and error handling
✓ Running on port 3000

Files: frontend/src/App.js, frontend/src/components/

Both agents completed successfully. To run:
  Terminal 1: cd backend && python app.py
  Terminal 2: cd frontend && npm start

Would you like me to test the integration?
```

**You:**
```
Yes, test the integration.
```

**Claude:**
```
[Spawning integration agent to test end-to-end flow]

Testing integration between backend and frontend...

✓ Backend API responding on port 5001
✓ Frontend making requests to backend
✓ CORS working correctly
✓ Data flowing from backend to frontend
✓ Search form submitting and showing results

Integration test passed! The search flow works end-to-end.

Demo ready. You can now present this to your table!
```

**You:**
```
Great! What should I demo?
```

**Claude:**
```
Here's your Q1 demo flow:

1. Show the search form (frontend on localhost:3000)
2. Enter a search: SFO → LAX, any date
3. Click "Search"
4. Results appear showing available flights
5. Explain: "We have two microservices:
   - Search API (Flask, port 5001)
   - Search UI (React, port 3000)"

Q1 deliverable achieved: Working flight search with multi-service architecture!

For Q2, you could add:
- Booking API (port 5002)
- Booking UI integration
- Payment processing

Need help with Q2 planning?
```

---

### Agent Tool Summary

**Key takeaway:** In Claude Code CLI, you don't write code or JSON - you just **describe what you want** in natural language, and Claude coordinates the agents for you.

**Your role:**
- Describe tasks clearly ("Build a Flask API on port 5001...")
- Specify parallel vs sequential ("Run these two agents in parallel...")
- Review agent outputs ("Does this look right? Test it before continuing...")
- Provide context for handoffs ("The API from Agent 1 is on localhost:5001...")

**Claude's role:**
- Spawn agents using the Agent tool internally
- Formulate detailed prompts for each agent
- Coordinate timing (parallel vs sequential)
- Report results back to you

**For this workshop:**
- **Just ask Claude naturally** - no code needed
- **Start with 2-3 agents** in parallel or sequence
- **Review each agent's output** before proceeding
- **Pass explicit context** when agents need to work together

**Next:** Now that you know HOW to spawn agents in the CLI, let's explore the PATTERNS for coordinating them effectively.

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

### How to Spawn Agents in Claude Code CLI (Quick Summary)

**You just ask Claude in natural language. Claude handles the Agent tool internally.**

**Parallel agents:**
```
You: "Build a flight booking app with Flask API and React UI.
      Spawn two agents to work on this in parallel."

Claude: [Spawns both agents simultaneously, reports when complete]
```

**Sequential agents:**
```
You: "First agent: Design database schema.
      Second agent: Build API using that schema.
      Run sequentially."

Claude: [Runs Agent 1, shows result, then runs Agent 2 with context]
```

**Background agent:**
```
You: "Generate test data with 1000 flights. Run this in background
      while I work on the frontend."

Claude: [Spawns background agent, notifies when complete]
```

**Agent Teams (advanced):**
```
You: "Create a team with Backend, Frontend, and QA specialists."
Claude: [Creates persistent team]

You: "Team: Build flight search feature."
[Team members collaborate and build]
```

**Key insight:** No code needed - just describe what you want!

---

### Claude Code CLI Quick Commands

**Ask Claude to spawn agents:**
- "Spawn two agents in parallel for..."
- "Use a sequential pipeline with three agents..."
- "Run this agent in the background..."
- "Create a team with [roles]..."

**Review and iterate:**
- "Show me what Agent 1 built"
- "That looks good, now spawn Agent 2..."
- "The integration isn't working, spawn a debug agent..."

**Get help:**
- "What's the best multi-agent strategy for this?"
- "How should I divide this work between agents?"
- "Should I use parallel or sequential agents here?"

---

### Alternative: Multiple Tabs (Manual)
- Open 2-3 Claude Code CLI sessions in different terminals
- Each session = one agent conversation
- Manually copy-paste context between sessions
- Use when you want full control over each agent's conversation

**Decision:** For most scenarios, just ask Claude to spawn agents (much easier!).

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

1. **Describe your agent strategy to Claude** (e.g., "Spawn two agents in parallel...")
2. **Let Claude spawn agents** (you don't write code/JSON, just describe)
3. **Review each agent output** (2-min sanity check)
4. **Provide context for next agents** ("The API from Agent 1 is on port 5001...")
5. **Reserve integration time** (last 5-10 minutes)

**Example conversation starter:**
```
You: "I need to build [feature] with a multi-agent approach.
      Spawn [N] agents:
      - Agent 1: [task]
      - Agent 2: [task]
      Run them [parallel/sequentially]."
```

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
1. **Use natural language** - No code needed, just describe what you want
2. **Clear descriptions** - Specific tasks, tech stack, deliverables
3. **Explicit context** - Pass information between agents
4. **Reserve integration time** - Don't assume it "just works"
5. **Review outputs** - Agents aren't perfect
6. **Parallelize when possible** - Maximum speed
7. **Don't overcomplicate** - 2-3 agents often optimal

**You're the orchestrator.** In Claude Code CLI, you decide:
- Which pattern to use (parallel, sequential, specialist)
- How to divide work between agents
- What context to pass between agents
- When to integrate outputs
- What quality bar to hit

**You're just talking to Claude.** No code, no JSON, no API calls. Just:
- Describe what you want to build
- Ask Claude to spawn agents
- Review outputs
- Provide feedback and direction

**Trust yourself.** If a pattern isn't working, switch. If an agent produces poor output, ask Claude to try again with more specific instructions. Adapt, experiment, learn.

---

**Good luck building! 🚀**

*Remember: The best way to learn multi-agent orchestration is to orchestrate multiple agents building something real.*

---

## FINAL NOTE: IT'S EASIER THAN YOU THINK

If this tutorial seems long and complex, here's the good news:

**In Claude Code CLI, multi-agent orchestration is just conversation.**

You don't need to:
- Write code or JSON
- Learn API syntax
- Memorize tool parameters
- Configure complex systems

You just need to:
- Describe what you want to build
- Ask Claude to spawn agents (parallel or sequential)
- Review what agents build
- Provide feedback

**Example - the entire workflow:**
```
You: "Build a flight booking app. Spawn two agents in parallel:
      one for Flask API (port 5001), one for React UI (port 3000)."

Claude: [Spawns agents, they build in parallel]

Claude: "Both agents completed. Here's what they built... [summary]"

You: "Good! Now spawn an agent to integrate them."

Claude: [Spawns integration agent]

Claude: "Integration complete. Ready to demo!"
```

**That's it.** You just had a conversation with Claude, and got a multi-service application built by multiple agents working in parallel.

**Start simple, build confidence, then try advanced techniques.**

You've got this!
