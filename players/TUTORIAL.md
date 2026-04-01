# MULTI-AGENT ORCHESTRATION TUTORIAL
## A Practical Guide to Building with Multiple Claude Agents

**Purpose:** Learn how to coordinate multiple Claude agents to build software faster and more effectively than working with a single agent.

**Audience:** Software engineers new to multi-agent workflows

**Time to Read:** 15-20 minutes

---

## TABLE OF CONTENTS

1. [Why Multiple Agents?](#why-multiple-agents)
2. [Core Concepts](#core-concepts)
3. [How to Use Agents in Claude Code CLI](#how-to-use-agents-in-claude-code-cli)
4. [The Four Fundamental Patterns](#the-four-fundamental-patterns)
5. [Practical Examples](#practical-examples)
6. [Prompt Engineering](#prompt-engineering)
7. [Context Management](#context-management)
8. [Common Pitfalls & Solutions](#common-pitfalls--solutions)
9. [Debugging Agent Outputs](#debugging-agent-outputs)
10. [Advanced Techniques](#advanced-techniques)
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
- You describe tasks for each agent
- You review agent outputs
- You coordinate handoffs between agents
- You make final integration decisions

Think of yourself as a conductor, not a passive observer.

---

## HOW TO USE AGENTS IN CLAUDE CODE CLI

### The Key Insight

**In Claude Code CLI, you don't write code or JSON. You just talk to Claude naturally, and Claude creates subagents for you.**

**Example:**
```
You: "I need to build a flight booking app. Create two subagents in parallel:
      one for the Flask API and one for the React UI."

Claude: "I'll create two subagents to work on this in parallel."
        [Claude creates subagents internally using the Agent tool]
        [Agents work and complete]
        "Both agents have completed. Here's what they built..."
```

**You're just having a conversation.** No code, no tool calls, no JSON.

---

### Three Ways to Work with Multiple Agents

#### Option 1: Multiple Conversations (Tabs/Windows)

**How it works:** Open multiple Claude Code CLI sessions in different terminals.

```
Terminal 1: "Build a Flask API for flight search on port 5001"
Terminal 2: "Build a React UI for flight search on port 3000"
Terminal 3: "Integrate the API from terminal 1 with the UI from terminal 2"
```

**Pros:** Simple, full control, easy to see each agent's history
**Cons:** Manual context switching, manual copy-paste, hard to manage 3+ agents

**When to use:** You're new to multi-agent, only 2-3 agents, want full visibility

---

#### Option 2: Sub-Agents (Recommended)

**How it works:** Within a single Claude Code conversation, ask Claude to spawn sub-agents.

**Example:**
```
You: "Build a flight booking app with Flask backend and React frontend.
      Create two subagents in parallel for this."

Claude: "I'll create two subagents to work on this in parallel:
         - Agent 1: Backend API developer
         - Agent 2: Frontend developer

         [Both agents working...]

         Agent 1 completed: Flask API on port 5001
         Agent 2 completed: React UI on port 3000

         Both services are ready. Would you like me to test integration?"
```

**Pros:** Everything in one conversation, programmatic coordination, Claude handles the details
**Cons:** Sub-agent conversations not directly visible (you see results only)

**When to use:** Most scenarios (recommended default), 2-5 agents, want simplicity

---

#### Option 3: Agent Teams (Advanced)

**How it works:** Create a persistent team of specialist agents that collaborate across multiple turns.

**Example:**
```
You: "Create a team with Backend, Frontend, and QA specialists"

Claude: "I've created a team with three specialists:
         - Backend Agent
         - Frontend Agent
         - QA Agent

         What should the team work on?"

You: "Team: Build a flight booking system"

[Agents collaborate, can message each other, build on previous work]

You: "Team: Add payment processing"

[Same agents continue, building incrementally]
```

**Pros:** Agents retain context, communicate with each other, persistent specialists
**Cons:** More complex setup, can be overkill for simple tasks

**When to use:** Multi-quarter projects, want persistent memory, agents need to communicate

---

### How to Ask Claude to Create Agents

**For parallel work:**
```
You: "Spawn two agents in parallel:
      - Agent 1: Build Flask API on port 5001
      - Agent 2: Build React UI on port 3000"
```

**For sequential work:**
```
You: "Spawn agents sequentially:
      - First agent: Design database schema
      - Second agent: Build API using that schema"
```

**For background tasks:**
```
You: "Generate test data with 1000 flights. Run this in the background
      while I work on the frontend."
```

**To create a team:**
```
You: "Create a team with Backend, Frontend, and QA specialists."
```

**That's it!** Claude handles all the Agent tool calls internally. You just describe what you want.

---

## THE FOUR FUNDAMENTAL PATTERNS

### Pattern 1: Parallel Execution

**When to use:** Tasks are independent and can happen simultaneously

**How it works:** Start multiple agents at once, each with a separate task

**CLI Example:**
```
You: "Build a flight search feature with Flask backend and React frontend.
      Create two subagents in parallel."

Claude: [Creates Agent 1: Backend]
        [Creates Agent 2: Frontend]
        [Both work simultaneously]

        "Both completed:
         - Agent 1: Flask API on port 5001
         - Agent 2: React UI on port 3000"
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

**CLI Example:**
```
You: "Build a booking system in stages:
      1. First agent: Design database schema
      2. Second agent: Build API using that schema
      Run sequentially."

Claude: [Agent 1: Designs schema]
        "Agent 1 created schema with flights, bookings, payments tables.
         Here's the schema: [shows SQL]

         Now spawning Agent 2..."

        [Agent 2: Builds API using schema]
        "Agent 2 built Flask API with CRUD endpoints using Agent 1's schema."
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

**CLI Example:**
```
You: "Create a team with Backend, Frontend, and Testing specialists.
      This team will work across multiple quarters."

[Quarter 1]
You: "Team: Build flight search feature"

Backend Agent: [Builds search API]
Frontend Agent: [Builds search UI]
Testing Agent: [Writes search tests]

[Quarter 2 - same team continues]
You: "Team: Add booking functionality"

Backend Agent: [Adds booking endpoints to existing API]
Frontend Agent: [Adds booking flow to existing UI]
Testing Agent: [Extends tests for bookings]
```

**Advantages:**
- 🧠 Context retention - agents remember their previous work
- 🎯 Domain expertise - agents get better at their specialty
- 🏗️ Architectural consistency - each agent maintains their domain

**Disadvantages:**
- 🔒 Less flexible - can't easily reassign work
- 💼 More coordination - need to keep agents aligned

**Best for:** Multi-quarter projects, established architecture, clear boundaries

---

### Pattern 4: Iterative Refinement

**When to use:** Need quality, polish, or fixing issues

**How it works:** Agent 1 builds → Agent 2 reviews/improves → Agent 1 or 3 refines

**CLI Example:**
```
You: "Build a flight booking UI, then have another agent review and improve it."

Claude: [Agent 1: Builds UI]
        "Agent 1 built the UI. Now creating Agent 2 to review..."

        [Agent 2: Reviews]
        "Agent 2 found 3 UX improvements and 2 bugs:
         - Add loading states
         - Better error messages
         - Fix date picker validation"

        "Should I spawn Agent 3 to implement these improvements?"

You: "Yes"

Claude: [Agent 3: Implements improvements]
        "Agent 3 implemented all improvements. UI is now polished."
```

**Advantages:**
- ✨ Higher quality - multiple perspectives
- 🐛 Catches bugs - fresh eyes find issues
- 📚 Learning opportunity - see different approaches

**Disadvantages:**
- ⏱️ More time - multiple passes
- 🔁 Potential loops - agents disagree

**Best for:** Polish phases, quality-critical features, final refinement

---

## PRACTICAL EXAMPLES

### Example 1: Building a Flight Search Page (Parallel)

**Scenario:** You have 30 minutes to build a working flight search with backend and frontend.

**Your CLI conversation:**

```
You: "I have 30 minutes to build a flight search feature.

      Create two subagents in parallel:

      Agent 1: Build a Flask API with GET /flights endpoint
      - Query params: origin, destination, date
      - Return JSON array of flights
      - SQLite database with 10 mock flights
      - CORS enabled
      - Port 5001

      Agent 2: Build a React UI for flight search
      - Search form (origin, destination, date inputs)
      - Display results in a table
      - Call the API at localhost:5001
      - Port 3000

      Start both agents now."

Claude: "I'll spawn both agents to work in parallel.

         [Agent 1: Backend API]
         Building Flask flight search API...

         [Agent 2: Frontend UI]
         Building React flight search interface...

         [Both working simultaneously...]

         ---

         Agent 1 (Backend) completed (15 min):
         ✓ Flask API with GET /flights?origin={}&dest={}&date={}
         ✓ SQLite database with 10 mock flights (SFO, LAX, NYC, etc.)
         ✓ CORS enabled for localhost:3000
         ✓ Running on port 5001

         Files: backend/app.py, backend/flights.db

         ---

         Agent 2 (Frontend) completed (15 min):
         ✓ React app with search form
         ✓ Results table showing flights
         ✓ Calls http://localhost:5001/flights
         ✓ Loading states and error handling
         ✓ Running on port 3000

         Files: frontend/src/App.js, frontend/src/SearchForm.js

         ---

         Both agents completed in 15 minutes (would be 30 minutes sequentially!).

         To run:
         1. Terminal: cd backend && python app.py
         2. Terminal: cd frontend && npm start
         3. Open localhost:3000

         Ready to demo! Would you like me to test the integration?"

You: "Yes, test it"

Claude: [Spawns integration agent]
        "Integration test passed! Search flow works end-to-end."
```

**Timeline:**
- Minutes 0-2: Write request to Claude
- Minutes 2-17: Both agents work in parallel
- Minutes 17-20: Integration test
- Minutes 20-30: Demo and polish

**Result:** Working end-to-end feature in 20 minutes (vs 40+ minutes sequential).

---

### Example 2: Adding Booking Flow (Sequential Pipeline)

**Scenario:** You have the search page from Example 1. Now add booking capability.

**Your CLI conversation:**

```
You: "Now I need to add booking functionality. Run this sequentially:

      Agent 1: Extend the Flask API to add POST /bookings endpoint
      - Accept: flight_id, passenger_name, passenger_email
      - Return: booking_id, status, confirmation_code
      - Add bookings table to SQLite
      - Validate flight exists and has seats
      - Same port 5001

      Then Agent 2: Extend the React UI to add booking flow
      - When user clicks 'Book' show booking form
      - Submit to POST /bookings endpoint
      - Show confirmation page with booking details"

Claude: "I'll run these agents sequentially since Agent 2 needs Agent 1's endpoint.

         Starting Agent 1...

         [Agent 1: Booking API]
         Adding booking endpoint to existing Flask API...

         ---

         Agent 1 completed (12 min):
         ✓ Added POST /bookings endpoint
         ✓ Created bookings table in SQLite
         ✓ Validates flight_id exists and has available seats
         ✓ Decrements seats_available on successful booking
         ✓ Returns booking_id, status, confirmation_code

         Endpoint ready at http://localhost:5001/bookings

         ---

         Now creating Agent 2 to build the booking UI...

         [Agent 2: Booking UI]
         Adding booking flow to existing React app...

         ---

         Agent 2 completed (13 min):
         ✓ Added booking modal with passenger form
         ✓ Calls POST /bookings when user confirms
         ✓ Shows confirmation page with booking details
         ✓ Error handling for full flights

         ---

         Sequential pipeline completed in 25 minutes.

         Full flow now works: Search → View Results → Book → Confirmation!"

You: "Perfect! Demo ready."
```

**Result:** Complete search + booking flow in 25 minutes.

---

### Example 3: Quality Polish (Iterative Refinement)

**Scenario:** You have a working booking system but it feels rough. Polish it.

**Your CLI conversation:**

```
You: "The booking system works but needs polish.

      Spawn a UX review agent to identify improvements, then spawn
      another agent to implement the top improvements."

Claude: "I'll spawn a review agent first.

         [Agent 1: UX Review]
         Reviewing flight booking system for UX improvements...

         ---

         Agent 1 (Review) completed:

         Found 6 improvements:

         **UX Issues:**
         1. No loading states - users don't know when API is working
         2. Error messages are technical (500 error) not user-friendly
         3. No confirmation before booking (easy to click by mistake)

         **Missing Features:**
         4. Can't cancel bookings once made
         5. No search history / recently searched routes
         6. Date picker doesn't disable past dates

         **Priority order:** 1, 2, 3 (critical), 4, 5, 6 (nice-to-have)

         ---

         Should I spawn an agent to implement the top 3 critical improvements?"

You: "Yes, implement 1, 2, and 3"

Claude: [Agent 2: Implement improvements]
        Implementing loading states, better errors, and confirmation dialog...

        ---

        Agent 2 completed (10 min):
        ✓ Added loading spinner during API calls
        ✓ User-friendly error messages ("Sorry, this flight is full")
        ✓ Confirmation dialog before booking ("Book flight for $199?")

        ---

        System is now polished and ready for demo!"
```

**Result:** Professional-quality UI with iterative refinement.

---

### Example 4: Multi-Service Architecture (Specialist Roles)

**Scenario:** Build 3 microservices that work together across multiple quarters.

**Your CLI conversation:**

```
You: "I'm building a flight booking platform across 4 quarters.

      Create a team with three specialists:
      - Search Service Developer (owns search API)
      - Booking Service Developer (owns booking API)
      - Frontend Developer (owns web UI)

      This team will work together all 4 quarters."

Claude: "Team created with three specialists:
         - Search Agent (search API specialist)
         - Booking Agent (booking API specialist)
         - Frontend Agent (web UI specialist)

         Ready to start Q1!"

--- Quarter 1 ---

You: "Team: Build the initial version.

      Search Agent: Flask API on port 5001 with GET /flights
      Booking Agent: Flask API on port 5002 with POST /bookings
      Frontend Agent: React UI on port 3000 calling both APIs"

Search Agent: "Building flight search API on port 5001..."
              "Search API complete with /flights endpoint and SQLite database."

Booking Agent: "Building booking API on port 5002..."
               "Booking API complete with /bookings endpoint."

Frontend Agent: "Building UI that calls both microservices..."
                "UI complete. Calls search on 5001, bookings on 5002."

Claude: "Q1 complete! All three services working together."

--- Quarter 2 ---

You: "Team: Enhance your services.

      Search Agent: Add filtering by price and airline
      Booking Agent: Add GET /bookings/{id} to retrieve bookings
      Frontend Agent: Add booking lookup feature"

Search Agent: "Adding price and airline filters to my existing search API..."
              "Filters added: ?min_price=100&max_price=500&airline=UA"

Booking Agent: "Adding GET endpoint to my existing booking API..."
               "GET /bookings/{id} endpoint added."

Frontend Agent: "Adding booking lookup to my existing UI..."
                "Booking lookup feature added with search-by-ID."

Claude: "Q2 complete! All services enhanced."

--- Quarter 3 ---

You: "Team: Add payments.

      Booking Agent: Integrate with payment API (mock for now)
      Frontend Agent: Add payment form to booking flow"

Booking Agent: "Adding payment integration to booking flow..."
               "Payment step added before confirming bookings."

Frontend Agent: "Adding payment form with card details..."
                "Payment form integrated into booking flow."

Claude: "Q3 complete! Payment flow working."
```

**Result:** Each agent maintains their service across quarters, building incrementally with context retention.

---

## PROMPT ENGINEERING

### The Anatomy of a Good Request to Claude

When asking Claude to spawn agents, include:

1. **Task description** - What should be built?
2. **Tech requirements** - Framework, ports, dependencies
3. **Deliverables** - What outputs do you expect?
4. **Execution strategy** - Parallel or sequential?

### Example: Poor Request

```
You: "Build a booking system"
```

**Problems:**
- No scope definition
- No tech stack specified
- No clear deliverable
- Claude will make assumptions

### Example: Good Request

```
You: "Build a flight booking system with:

      Create two subagents in parallel:

      Agent 1 (Backend):
      - Flask REST API
      - Endpoints: GET /flights, POST /bookings
      - SQLite database
      - Port 5001

      Agent 2 (Frontend):
      - React app
      - Search form and booking form
      - Calls API at localhost:5001
      - Port 3000

      Deliverable: Both services running and integrated"
```

**Why it's better:**
- ✅ Clear scope (backend + frontend)
- ✅ Tech stack specified (Flask, React, SQLite)
- ✅ Specific endpoints and ports
- ✅ Execution strategy (parallel)
- ✅ Clear deliverable

### Template for Parallel Work

```
You: "Build [feature] with [N] agents in parallel:

      Agent 1: [Role] - Build [component]
      - [Requirement 1]
      - [Requirement 2]
      - Port/Location: [X]

      Agent 2: [Role] - Build [component]
      - [Requirement 1]
      - [Requirement 2]
      - Port/Location: [Y]

      Deliverable: [What should work end-to-end]"
```

### Template for Sequential Work

```
You: "Build [feature] with agents running sequentially:

      First agent: [Task 1]
      - [Requirements]

      Then second agent: [Task 2] using output from first agent
      - [Requirements]

      Deliverable: [Final output]"
```

### Anti-Patterns

❌ **Too vague:**
```
You: "Make it better"
You: "Build the backend"
```

❌ **Too many agents:**
```
You: "Spawn 7 agents to build..."
```
(Stick to 2-3 agents)

❌ **Missing tech stack:**
```
You: "Build a web app"
```
(Flask? Express? React? Vue?)

---

## CONTEXT MANAGEMENT

### The Context Handoff Challenge

When Agent 2 needs to build on Agent 1's work, what information should you provide?

### Option 1: Full Context

**When:** Agent 2 needs to modify/extend Agent 1's code

**Example:**
```
You: "Agent 1 built this API: [paste full code]

      Create Agent 2 to add three more endpoints to this code."
```

**Pros:** Complete context, informed decisions
**Cons:** Long messages, more tokens

---

### Option 2: Interface/Contract Only

**When:** Agent 2 just needs to call Agent 1's output

**Example:**
```
You: "There's an API running on localhost:5001 with these endpoints:

      GET /flights?origin={}&dest={}&date={}
      Returns: [{id, origin, dest, price, seats}, ...]

      POST /bookings {flight_id, passenger_name, email}
      Returns: {booking_id, status, confirmation_code}

      Spawn an agent to build a React UI that calls these endpoints."
```

**Pros:** Concise, focuses on interface
**Cons:** Agent can't fix issues in Agent 1's code if needed

---

### Option 3: Hybrid (Recommended)

**When:** Most scenarios

**Example:**
```
You: "Agent 1 built a Flask API with GET /flights endpoint on port 5001.

      Here's the endpoint signature:
      @app.route('/flights')
      def get_flights():
          origin = request.args.get('origin')
          dest = request.args.get('destination')
          # Returns JSON: [{id, origin, dest, price}, ...]

      Spawn an agent to build a frontend that calls this endpoint.
      If you find any issues with the API, flag them."
```

**Pros:** Balance of context and conciseness
**Cons:** Requires judgment on what to include

---

### Best Practices

1. **Start minimal, add as needed**
   - First try with just interface/contract
   - If agent struggles, provide more context

2. **Be explicit about what's done vs. what's next**
   ```
   You: "Agent 1 completed:
         ✅ Database schema
         ✅ Flight search endpoint

         Create Agent 2 to:
         ⬜ Add booking endpoint
         ⬜ Add payment processing"
   ```

3. **Reference locations clearly**
   ```
   You: "Agent 1 created backend/app.py on port 5001
         Create Agent 2 to create frontend/app.js on port 3000"
   ```

4. **Use structured summaries for complex systems**
   ```
   You: "Current system:

         Service 1 - Search API
         - Port: 5001
         - Endpoints: GET /flights

         Service 2 - Booking API
         - Port: 5002
         - Endpoints: POST /bookings

         Spawn a frontend agent to integrate both services."
   ```

---

## COMMON PITFALLS & SOLUTIONS

### Pitfall 1: Too Many Agents

**Symptom:**
- Managing 5+ agents simultaneously
- Spending more time coordinating than building
- Agents producing conflicting outputs

**Solution:**
```
Bad:  7 agents (API, DB, Frontend, Tests, Docs, Deploy, Monitoring)
Good: 3 agents (Backend with DB, Frontend, Integration & Tests)
```

**Rule of thumb:** 2-3 agents for a 30-minute task, 3-4 for a 60-minute task

---

### Pitfall 2: Agents Waiting Idle

**Symptom:**
- Purely sequential work with no parallelization
- No time savings vs. single agent

**Solution:**

**Before:**
```
Agent 1: Build API (20 min) → Wait →
Agent 2: Build frontend (20 min) → Wait →
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

**Solution:**

**Establish contracts first:**
```
You: "Before spawning agents, design the API contract:
      - Service 1 endpoints and response format
      - Service 2 endpoints and response format
      - Data models (Flight, Booking schemas)

      Then spawn agents to build to this contract."
```

**Or be explicit in request:**
```
You: "Spawn two agents:

      Agent 1: Build Flask API returning JSON in this format:
      {
        "flights": [
          {"id": "FL123", "price": 199.99, ...}
        ]
      }

      Agent 2: Build React UI calling API expecting this same JSON format"
```

---

### Pitfall 4: Context Loss

**Symptom:**
- Agent 2 doesn't know what Agent 1 built
- Agents make incompatible assumptions

**Solution:**

**Bad:**
```
You: "Build on what Agent 1 did"
```

**Good:**
```
You: "Agent 1 built a Flask API with GET /flights endpoint on port 5001.
      It returns: [{id, origin, dest, price, seats}]

      Here's the database schema: [paste schema]

      Create Agent 2 to build a frontend that calls this API..."
```

---

### Pitfall 5: No Integration Plan

**Symptom:**
- 3 agents finish successfully
- Outputs don't fit together
- Manual integration takes 15 minutes

**Solution:**

**Reserve an agent for integration:**
```
You: "Spawn 3 agents:
      Agent 1: Backend (20 min)
      Agent 2: Frontend (20 min)
      Agent 3: Integration - connect 1 & 2, fix issues (10 min)"
```

**Or test integration at the end:**
```
You: "Both agents completed. Now test the integration end-to-end.
      Fix any CORS issues, connection problems, or data format mismatches."
```

---

### Pitfall 6: Not Reviewing Outputs

**Symptom:**
- Agent produces code with bugs
- You immediately pass to next agent without review
- Bugs compound through the pipeline

**Solution:**

**Always review before handoff:**
```
You: "Build the API"
[Agent builds API]

You: "Does this code look right? Are there bugs?"
[Review output]

You: "Good! Now build the frontend that calls this API"
```

**Quick review checklist (2 minutes):**
- [ ] Does it run without errors?
- [ ] Does it match requirements?
- [ ] Are there obvious bugs?
- [ ] Ready for next agent?

---

## DEBUGGING AGENT OUTPUTS

### Why This Section Matters

Agents aren't perfect. They make mistakes, misunderstand requirements, and produce code that doesn't work. **This is normal.** The key is knowing how to debug efficiently and get back on track fast.

This section teaches you:
- How to diagnose what went wrong
- Strategies to fix issues quickly
- How to prevent common failures

---

### Common Types of Agent Failures

#### Type 1: Code That Won't Run

**Symptoms:**
- Syntax errors (SyntaxError, IndentationError)
- Import errors (ModuleNotFoundError, ImportError)
- Runtime crashes immediately on start

**Example:**
```
$ python app.py
ModuleNotFoundError: No module named 'flask_cors'
```

**Common causes:**
- Agent forgot to specify dependencies
- Agent used wrong package name
- Agent assumed library was installed

---

#### Type 2: Code That Runs But Produces Wrong Results

**Symptoms:**
- API returns empty array when should have data
- Frontend displays nothing even though API works
- Data saved to database but can't be retrieved

**Example:**
```
GET /flights?origin=SFO&dest=LAX
Returns: []  (expected flight results)
```

**Common causes:**
- Logic errors in filtering/queries
- Wrong database table or column names
- Mismatched data formats between services

---

#### Type 3: Code That Partially Works

**Symptoms:**
- Search works but booking fails
- Happy path works but error cases crash
- Works on first try, fails on second

**Example:**
```
First booking: Success!
Second booking: Error: Seat already taken (logic bug)
```

**Common causes:**
- Missing edge case handling
- State management bugs
- Incomplete implementation

---

#### Type 4: Integration Failures Between Services

**Symptoms:**
- Frontend can't call backend API
- CORS errors in browser console
- Services can't communicate (connection refused)

**Example:**
```
Console: Access to fetch at 'http://localhost:5001' blocked by CORS policy
```

**Common causes:**
- CORS not configured
- Wrong ports or URLs
- Services not running
- Firewall blocking connections

---

#### Type 5: Performance Issues

**Symptoms:**
- API takes 10+ seconds to respond
- UI freezes during operations
- Database queries timeout

**Example:**
```
GET /flights → 15 seconds (should be <1 second)
```

**Common causes:**
- Missing database indexes
- N+1 query problems
- Loading too much data at once

---

### Systematic Debugging Approach

#### Step 1: Read the Error Message Carefully

**Don't panic. Read the actual error.**

```
Bad:  "It's broken! Fix it!"
Good: "Getting error: ModuleNotFoundError: No module named 'flask_cors'
       in backend/app.py line 3"
```

**What to look for:**
- Error type (ImportError, TypeError, etc.)
- File and line number
- Actual vs expected behavior

---

#### Step 2: Isolate the Problem

**Which agent? Which file? Which function?**

**Questions to ask:**
- Is it frontend or backend?
- Does the backend API work when tested directly (curl/Postman)?
- Does the issue happen with all inputs or specific ones?
- When did it start working incorrectly?

**Example isolation:**
```
You: "Test the backend API directly with curl to see if it works
      without the frontend."

[Test reveals API works fine]

You: "OK, so the bug is in the frontend calling the API, not the API itself."
```

---

#### Step 3: Test Components Independently

**Don't test the whole system. Test one piece at a time.**

**Backend test:**
```bash
curl http://localhost:5001/flights?origin=SFO&dest=LAX
```

**Frontend test:**
```javascript
console.log("API response:", response.data)
```

**Database test:**
```bash
sqlite3 flights.db "SELECT * FROM flights WHERE origin='SFO'"
```

---

#### Step 4: Check Assumptions

**Common assumptions that break:**

❌ "The API is running" → Check with `ps aux | grep python`
❌ "Port 5001 is available" → Check with `lsof -i :5001`
❌ "Dependencies are installed" → Check with `pip list | grep flask`
❌ "File paths are correct" → Check with `ls backend/app.py`
❌ "Database has data" → Check with `sqlite3 db.db "SELECT COUNT(*) FROM flights"`

**Always verify, never assume.**

---

### Recovery Strategies

#### Strategy 1: Ask Same Agent to Fix (With Error Message)

**When to use:**
- Minor bugs (missing import, typo, small logic error)
- Agent has full context of what they built
- Fix is straightforward

**Example:**
```
You: "The code has this error:

     ModuleNotFoundError: No module named 'flask_cors'

     Fix this error."

Claude: [Same agent adds flask-cors to requirements.txt and installs it]
        "Fixed! Added flask-cors==4.0.0 to requirements.txt"
```

**Pros:** Fast, maintains context
**Cons:** If agent doesn't understand the bug, might fail again

✅ **Use when:** Simple bugs, clear error messages

---

#### Strategy 2: Spawn Debug Specialist Agent

**When to use:**
- Complex bugs requiring investigation
- Original agent tried to fix but failed
- Need fresh perspective

**Example:**
```
You: "Spawn a debugging specialist agent to investigate why
      GET /flights returns empty array.

      Context:
      - Backend API running on port 5001
      - Database has 10 flights in flights.db
      - Query params: ?origin=SFO&dest=LAX

      Here's the API code: [paste code]"

Claude: [Debug Agent investigates]
        "Found the issue! Line 47 uses 'destination' but the database
         column is 'dest'. Changing query to match DB schema."

        [Debug Agent fixes]
        "Fixed! Now returns correct results."
```

**Pros:** Fresh perspective, focused investigation
**Cons:** Takes longer, needs good context

✅ **Use when:** Complex bugs, original agent stuck, need investigation

---

#### Strategy 3: Start Over With Better Prompt

**When to use:**
- Fundamental misunderstanding of requirements
- Agent went in completely wrong direction
- Faster to rebuild than fix

**Example:**
```
Bad first attempt:
You: "Build an API"
Agent: [Builds REST API but you needed GraphQL]

Recovery:
You: "Actually, I need GraphQL not REST. Forget the REST API.

     Build a new GraphQL API with:
     - Schema for Flight type
     - Query for searching flights
     - Mutation for booking
     - Apollo Server on port 5001"

Claude: [New agent builds GraphQL API correctly]
```

**Pros:** Clean slate, correct from start
**Cons:** Loses previous work (if any was salvageable)

✅ **Use when:** Wrong architecture, fundamental mismatch, faster to restart

---

#### Decision Tree: Which Strategy?

```
Is it a simple error (import, typo, syntax)?
├─ Yes → Strategy 1: Ask same agent to fix
└─ No → Continue...

Did original agent try to fix but fail?
├─ Yes → Strategy 2: Spawn debug specialist
└─ No → Continue...

Is the agent's approach fundamentally wrong?
├─ Yes → Strategy 3: Start over with better prompt
└─ No → Strategy 2: Spawn debug specialist
```

---

### Practical Examples

#### Example 1: Import Error - Module Not Found

**The Problem:**
```
$ python backend/app.py
ModuleNotFoundError: No module named 'flask_cors'
```

**Your CLI Conversation:**
```
You: "Getting this error when running the backend:

     ModuleNotFoundError: No module named 'flask_cors'

     Fix it."

Claude: "The flask-cors package isn't installed. I'll add it to
         requirements.txt and install it.

         [Adds flask-cors==4.0.0 to requirements.txt]
         [Runs: pip install flask-cors]

         Fixed! Try running python backend/app.py again."

You: "Works now! Thanks."
```

**Time to fix:** 1 minute

**Key lesson:** Simple errors → ask same agent, provide exact error message

---

#### Example 2: CORS Error - Frontend Can't Call API

**The Problem:**
```
Browser Console:
Access to fetch at 'http://localhost:5001/flights' from origin
'http://localhost:3000' has been blocked by CORS policy
```

**Your CLI Conversation:**
```
You: "Frontend can't call the backend API. Getting CORS error:

     Access to fetch at 'http://localhost:5001/flights' from origin
     'http://localhost:3000' has been blocked by CORS policy

     The backend agent forgot to enable CORS. Fix this."

Claude: "I'll enable CORS in the Flask backend to allow requests from
         localhost:3000.

         [Updates backend/app.py]

         Added:
         from flask_cors import CORS
         CORS(app, origins=['http://localhost:3000'])

         Restart the backend and try again."

You: "Perfect! Frontend can now call the API."
```

**Time to fix:** 2 minutes

**Key lesson:** Integration bugs → be specific about which service needs fixing

---

#### Example 3: Code Runs But Returns Empty Results

**The Problem:**
```
GET /flights?origin=SFO&dest=LAX
Returns: []

Expected: Array of flight objects
```

**Your CLI Conversation:**
```
You: "The API returns empty array when it should return flights.

     Testing with: GET /flights?origin=SFO&dest=LAX
     Returns: []

     The database has 10 flights. Something is wrong with the query.

     Spawn a debug specialist to investigate."

Claude: [Spawns Debug Agent]

        "Debug Agent investigating...

         Found issue! The API code uses request.args.get('destination')
         but the database column is named 'dest'.

         Query fails because column name doesn't match.

         Should I fix this by:
         A) Change API to use 'dest' parameter, OR
         B) Rename database column to 'destination'?"

You: "Option A - change API to use 'dest' parameter"

Claude: [Debug Agent fixes]

        "Fixed! Changed line 23 from:
         dest = request.args.get('destination')
         to:
         dest = request.args.get('dest')

         Now returns correct results:
         GET /flights?origin=SFO&dest=LAX
         Returns: [{id: 1, origin: 'SFO', dest: 'LAX', price: 199}, ...]"
```

**Time to fix:** 5 minutes

**Key lesson:** Empty results → spawn debug specialist, provide context about what data exists

---

### Prevention Techniques

#### Prevention 1: Test As You Go

**Don't wait until everything is built to test.**

**Bad approach:**
```
Build backend → Build frontend → Build integration → Test everything
[Find 5 bugs across all layers]
```

**Good approach:**
```
Build backend → Test backend immediately
Build frontend → Test frontend immediately
Integrate → Test integration
```

**CLI Example:**
```
You: "Build the Flask API for flight search"
[Agent builds API]

You: "Before moving to frontend, test this API with curl to make
      sure it works"
[Agent tests, finds and fixes bug]

You: "Good! Now build the frontend"
```

✅ **Catch bugs early, when context is fresh**

---

#### Prevention 2: Be Specific About Dependencies

**Vague request:**
```
You: "Build a Flask API"
```
Agent might forget: CORS, database library, input validation library

**Specific request:**
```
You: "Build a Flask API with:
      - flask and flask-cors for web server
      - sqlite3 for database
      - Create requirements.txt with all dependencies
      - Test that all imports work"
```

✅ **Specify dependencies upfront**

---

#### Prevention 3: Include Error Handling in Initial Request

**Without error handling:**
```
You: "Build POST /bookings endpoint"
Agent builds happy path only → crashes on bad input
```

**With error handling:**
```
You: "Build POST /bookings endpoint with:
      - Validate passenger_name is not empty
      - Validate email format
      - Validate flight_id exists in database
      - Return 400 error with message for invalid inputs
      - Return 404 if flight not found
      - Return 409 if flight is full"
```

✅ **Request error handling from the start**

---

#### Prevention 4: Ask Agents to Explain Approach First

**Without explanation:**
```
You: "Build booking system"
Agent builds → wrong architecture → rebuild
```

**With explanation:**
```
You: "Before building, explain your approach:
      - What endpoints will you create?
      - What database schema?
      - What libraries will you use?"

Claude: "I'll create:
         - POST /bookings endpoint
         - bookings table with: id, flight_id, passenger_name, email
         - Use Flask, SQLite, flask-cors
         - Return booking_id and confirmation_code"

You: "Good! One change: also store booking timestamp. Now build it."

Claude: [Builds with correct approach]
```

✅ **Review approach before implementation**

---

### Quick Debugging Checklist

When something breaks, check:

**For Backend Issues:**
- [ ] Is the server running? (`ps aux | grep python`)
- [ ] Is it on the right port? (`lsof -i :5001`)
- [ ] Are dependencies installed? (`pip list`)
- [ ] Does the API respond to curl? (`curl localhost:5001/flights`)
- [ ] Does the database have data? (`sqlite3 db.db "SELECT * FROM flights"`)

**For Frontend Issues:**
- [ ] Is the dev server running? (`ps aux | grep node`)
- [ ] Are there errors in browser console? (Open DevTools)
- [ ] Is it calling the right API URL? (Check Network tab)
- [ ] Are environment variables set? (`echo $REACT_APP_API_URL`)

**For Integration Issues:**
- [ ] Is CORS enabled on backend?
- [ ] Are ports correct on both sides?
- [ ] Are both services running simultaneously?
- [ ] Are data formats compatible? (JSON structure matches?)

---

### Debugging Best Practices

1. **Always include the full error message**
   ```
   Bad:  "It's not working"
   Good: "Getting error: TypeError: Cannot read property 'map' of undefined
          in SearchResults.js line 42"
   ```

2. **Test one layer at a time**
   ```
   Database → Backend API → Frontend → Integration
   ```

3. **Keep error messages visible**
   ```
   Don't just say "fixed it" - show what was wrong and what changed
   ```

4. **Document what worked**
   ```
   When you fix a tricky bug, ask: "What was the root cause and how
   can I prevent this next time?"
   ```

5. **Use debug specialists for complex issues**
   ```
   If same agent fails twice to fix → spawn debug specialist
   ```

---

### When Debugging Takes Too Long

⚠️ **If you've spent 10+ minutes debugging and still stuck:**

**Option 1: Ask Claude for help**
```
You: "I've been debugging this CORS issue for 10 minutes.
      Can you spawn a specialist to investigate what I'm missing?"
```

**Option 2: Start fresh**
```
You: "This approach isn't working. Let's start over.
      Build a simpler version that just focuses on getting
      the API call working first."
```

**Option 3: Simplify scope**
```
You: "Remove the complex filtering logic for now.
      Just make it return all flights. We'll add filtering
      once basic retrieval works."
```

🚩 **Red flag:** If debugging takes longer than building would take → start over

---

## ADVANCED TECHNIQUES

### Technique 1: Background Agents

**Concept:** Run long tasks in the background while working on other things

**Example:**
```
You: "Generate a realistic flight database with 1000 flights.
      Run this in the background while I work on the frontend."

Claude: "Background agent started generating flights.db.
         You can continue working - I'll notify when complete.

         What should we work on now?"

You: "Build the React frontend"

[Frontend agent works while background agent generates data]

Claude: [Later] "Background agent completed! flights.db ready with 1000 flights."
```

**When to use:** Data generation, long builds, database migrations

---

### Technique 2: Adversarial Agents

**Concept:** One agent builds, another tries to break it

**Example:**
```
You: "Build a booking API endpoint, then spawn another agent to
      find security issues and edge cases."

Claude: [Agent 1: Builds API]
        "API built with POST /bookings endpoint."

        [Agent 2: Breaks API]
        "Found 5 issues:
         - No input validation on email
         - SQL injection vulnerability in flight_id
         - No rate limiting
         - Missing authentication
         - Race condition with seat availability"

        "Should I spawn Agent 3 to fix these issues?"

You: "Yes, fix the critical ones"

Claude: [Agent 3: Fixes issues]
        "Fixed SQL injection, added input validation, fixed race condition."
```

**When to use:** Security-critical features, production code, edge case discovery

---

### Technique 3: Specialist Review Agents

**Concept:** Different agents review different aspects

**Example:**
```
You: "Review this code with three specialist agents:
      - Security Reviewer
      - Performance Reviewer
      - UX Reviewer"

Claude: [Security Agent: Found SQL injection, hardcoded secrets]
        [Performance Agent: Found N+1 queries, missing indexes]
        [UX Agent: Found missing loading states, poor error messages]

        "Combined findings: 8 issues across security, performance, UX.
         Should I spawn an agent to fix the critical ones?"
```

**When to use:** Quality polish phase, pre-demo refinement, production readiness

---

### Technique 4: Creating Reusable Skills (Optional)

**What are skills?** Custom slash commands you create for common workflows.

**Example:** Instead of repeatedly asking for the same workflow, create a `/new-service` skill:

```
You: /new-service booking 5002

[Skill automatically spawns agent to create boilerplate microservice]
```

**When to create skills:**
- You have a workflow you'll repeat 3+ times
- Multi-quarter projects where patterns emerge
- You want to save time on repeated setups

**When to skip skills:**
- First time playing this game
- One-off tasks
- Still learning multi-agent patterns

**Note:** Skills are **optional** and **advanced**. Most directors succeed without them.

See https://code.claude.com/docs/en/skills for details.

---

## QUICK REFERENCE

### How to Spawn Agents (Quick Cheat Sheet)

**Parallel:**
```
You: "Spawn N agents in parallel:
      - Agent 1: [task]
      - Agent 2: [task]"
```

**Sequential:**
```
You: "Spawn agents sequentially:
      - First: [task]
      - Then: [task] using output from first"
```

**Background:**
```
You: "Run [task] in background while I work on [other thing]"
```

**Team:**
```
You: "Create a team with [roles]"
You: "Team: [task]"
```

---

### Common Agent Roles

- **Backend API Developer** - Builds REST APIs, databases
- **Frontend Developer** - Builds UIs, user interactions
- **Integration Engineer** - Connects services, fixes compatibility
- **Test Engineer** - Writes tests, finds edge cases
- **Code Reviewer** - Reviews quality, suggests improvements
- **Security Auditor** - Finds vulnerabilities
- **UX Designer** - Improves user experience

---

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

---

### Decision Tree

```
Are you new to multi-agent?
├─ Yes → Start with 2 agents, parallel, Multiple Tabs
└─ No → Continue...

Need agents to persist across quarters?
├─ Yes → Use Agent Teams
└─ No → Continue...

Have 2-5 agents for single task?
├─ Yes → Use Sub-Agents (ask Claude to spawn) ← RECOMMENDED
└─ No → Use Multiple Tabs
```

---

### Red Flags (Stop and Reconsider)

🚩 Spawning 6+ agents → Too many, simplify
🚩 Agent waiting 10+ min for another → Bad parallelization
🚩 Manual integration taking 15+ min → Poor contracts
🚩 Agents producing incompatible code → Missing alignment
🚩 Same work done twice → Context loss
🚩 Can't explain why using multiple agents → Use one

---

## CONCLUSION

### Start Simple

**First time:** 2 agents, parallel pattern, 30 minutes
**Second time:** 3 agents, try sequential
**Third time:** Experiment with specialist roles or teams
**Fourth time:** Try advanced techniques

### Key Principles

1. **Use natural language** - No code, just describe what you want
2. **Clear descriptions** - Specific tasks, tech stack, deliverables
3. **Explicit context** - Pass information between agents
4. **Reserve integration time** - Don't assume it "just works"
5. **Review outputs** - Agents aren't perfect
6. **Parallelize when possible** - Maximum speed
7. **Don't overcomplicate** - 2-3 agents often optimal

### You're the Orchestrator

In Claude Code CLI, you:
- Decide which pattern (parallel, sequential, specialist)
- Describe what you want in natural language
- Review outputs and provide feedback
- Make final integration decisions

You're just talking to Claude. No code, no JSON, no API calls.

### It's Easier Than You Think

**The entire workflow:**
```
You: "Build a flight booking app. Spawn two agents in parallel:
      one for Flask API (port 5001), one for React UI (port 3000)."

Claude: [Spawns agents, they build in parallel]
        "Both completed. Here's what they built..."

You: "Good! Test the integration."

Claude: [Tests] "Integration works! Ready to demo."
```

**That's it.** Just a conversation.

### Trust Yourself

- If a pattern isn't working, switch
- If an agent produces poor output, ask Claude to try again with clearer instructions
- Adapt, experiment, learn

---

**Good luck building! 🚀**

*Remember: The best way to learn multi-agent orchestration is to orchestrate multiple agents building something real.*
