# DIRECTOR'S GUIDE
## Managing Your Organization with Claude Agent Teams

**Purpose:** Learn how to think and operate as a director managing multiple agent teams building microservices.

**Audience:** Engineers (junior to senior) learning to manage teams rather than code themselves

**Read this before:** Starting your first quarter as a director

---

## TABLE OF CONTENTS

1. [Thinking Like a Director](#thinking-like-a-director)
2. [Using Agents for Research & Planning](#using-agents-for-research--planning)
3. [Roles in Your Organization](#roles-in-your-organization)
4. [Organizing Your Agent Teams](#organizing-your-agent-teams)
5. [Delegation Best Practices](#delegation-best-practices)
6. [Common Director Mistakes](#common-director-mistakes)
7. [Quick Reference](#quick-reference)

---

## THINKING LIKE A DIRECTOR

**You're not a junior engineer anymore.** Directors don't write code - they set strategy, delegate to teams, and review results.

### The Mindset Shift

As a director with Claude agents as your team, you need to shift how you think about building software:

**From:** "I need to implement this feature"
**To:** "Which team should build this feature?"

**From:** "How do I code this function?"
**To:** "What should this service achieve?"

**From:** "Let me debug this myself"
**To:** "Agent Team B, investigate and fix this issue"

### Director vs. Engineer Mindset

| Junior Engineer Thinks | Director Thinks |
|------------------------|-----------------|
| "I'll build the search API" | "Agent Team A will build the search API" |
| "How do I implement this function?" | "What should this service achieve?" |
| "Let me write this code myself" | "Which team is best suited for this?" |
| "This needs to be perfect" | "This needs to ship and we can improve it" |
| "I'll fix this bug" | "QA team, find bugs. Dev team, fix them" |
| "I need to understand every line" | "I need to understand the architecture" |
| "Let me optimize this algorithm" | "Is performance good enough for demo?" |
| "I should learn this new framework" | "Which framework lets my team ship fastest?" |

### The Five Director Responsibilities

#### 1. Set the Vision
**What it means:** Define what "success" looks like for each quarter

**Examples:**
- "Q1 goal: Working search + booking flow, polish comes later"
- "Q2 goal: Add seat selection and improve visual design"
- "This quarter we need to demo to investors, so focus on the happy path"

**How to do it:**
- Read the quarter scenario from gamerunner
- Decide: What's the minimum viable demo?
- Decide: What can we defer to next quarter?
- Communicate clear goals to your agent teams

#### 2. Delegate to Teams
**What it means:** Assign work to agent teams with clear objectives

**Examples:**
- "Agent 1 (Backend Dev): Build the flight search API with these endpoints..."
- "Agent 2 (Frontend Dev): Build the search UI that calls Agent 1's API..."
- "Agent 3 (QA): Test the complete search flow and find edge cases..."

**How to do it:**
- Break your vision into 2-3 services or components
- Assign each service to an agent team
- Give them objectives, not implementation details
- Let them figure out how to achieve it

**Good delegation:**
```
"You are a backend developer building a flight search API.

Build a service with:
- GET /flights endpoint (search by origin, destination, date)
- Return mock flight data
- Run on port 5001
- Include basic error handling

Deliverable: Working API I can test with curl"
```

**Bad delegation (micromanaging):**
```
"On line 1, import Flask. On line 2, create app = Flask(__name__).
On line 5, define a function called search_flights with parameters
origin, dest, date. Inside the function, on line 7..."
```

#### 3. Review & Decide
**What it means:** Review what your teams produce and decide next steps

**Your review checklist:**
- [ ] Does it run without errors?
- [ ] Does it meet the requirements I gave?
- [ ] Is it demo-ready, or does it need refinement?
- [ ] Can I integrate it with other services?

**Three possible decisions:**
1. **Ship it** - It's good enough, move to next task
2. **Revise it** - Close, but needs fixes (give agent specific feedback)
3. **Scrap it** - Wrong approach, start over with different strategy

**Example review:**
```
Agent produced: Flight search API

You test it:
- ✅ Runs on port 5001
- ✅ Returns flight data
- ❌ Missing error handling for invalid dates
- ❌ Returns 500 error instead of 404 for no results

Decision: Revise
Feedback to agent: "Fix these two issues: [paste issues]"
```

#### 4. Integrate & Coordinate
**What it means:** Ensure your services work together

**Why this matters:**
- Agent Team A builds Search API
- Agent Team B builds Booking API
- Agent Team C builds Frontend UI
- **Someone needs to make them talk to each other** → That's you (or an integration agent)

**How to do it:**
- Test each service independently first
- Use an integration agent to connect them
- Or manually verify they work together
- Fix integration issues before demo

**Example:**
```
"Agent 3 (Integration Engineer):

Here's the Search API from Agent 1: [running on port 5001]
Here's the Frontend from Agent 2: [running on port 3000]

Task: Make the frontend call the search API correctly.
Fix any CORS issues, data format mismatches, or connection problems.
Test the end-to-end flow."
```

#### 5. Adapt Strategy
**What it means:** When things don't work, change your approach

**Common adaptations:**
- "Agent Team A is struggling with complex search, let's simplify to basic search for Q1"
- "We're running out of time, let's build 2 services instead of 3"
- "The parallel approach isn't working, let's switch to sequential"
- "This feature is too complex for 30 minutes, defer to next quarter"

**Directors make fast decisions:**
- Don't spend 15 minutes trying to make a broken approach work
- Timebox attempts: "Try for 5 minutes, if still broken, pivot"
- It's okay to change strategy mid-quarter

---

## USING AGENTS FOR RESEARCH & PLANNING

**Quarter 1 is about strategy, not code.** You'll use agents differently in Q1 than in later quarters.

### Why Research First?

**Common mistake:** Jump straight to coding without understanding what to build.

**Better approach:** Use Q1 to:
- Research what makes great systems in your domain
- Define your architecture and service boundaries
- Create vision documents and wireframes
- Plan your technical approach

**Then in Q2+:** Execute on that vision with confidence.

### Q1 Agent Roles

In Quarter 1, you'll use different agent roles than coding quarters:

#### 1. Researcher Agent

**Purpose:** Analyze existing solutions, find best practices

**Example Prompt:**
```
"You are a product researcher analyzing flight booking portals.

Research 3 successful booking sites (Expedia, Kayak, Google Flights).

For each, document:
- Key features that make booking easy
- UX patterns they use
- What they do well
- What they do poorly
- Technical architecture (if visible)

Deliverable: Research summary with insights and recommendations"
```

**Output you'll get:**
- Competitive analysis
- Feature ideas
- Best practices to adopt
- Pitfalls to avoid

---

#### 2. Business Analyst (Strategic)

**Purpose:** Define requirements, user flows, business logic

**Example Prompt:**
```
"You are a business analyst for an airline booking system.

Define the complete customer booking journey:
- What are the steps from search to confirmation?
- What data is needed at each step?
- What are the business rules (cancellations, changes, refunds)?
- What are the edge cases (sold out flights, invalid dates)?
- What systems need to integrate?

Deliverable: Requirements document with user flows"
```

**Output you'll get:**
- Clear requirements
- User journey maps
- Business rules documented
- Integration points identified

---

#### 3. UX Designer (Planning)

**Purpose:** Create wireframes, design user flows, plan interface

**Example Prompt:**
```
"You are a UX designer for a flight booking portal.

Create wireframes for these screens:
1. Search page (origin, destination, date)
2. Results page (list of flights)
3. Booking form (passenger details, payment)
4. Confirmation page

For each wireframe:
- Describe the layout and components
- Explain the user flow between screens
- Identify key UX considerations
- Suggest best practices for conversion

Deliverable: Wireframe descriptions with ASCII mockups or detailed descriptions"
```

**Output you'll get:**
- Screen-by-screen wireframes
- User flow diagrams
- UX recommendations
- Visual structure

---

#### 4. Technical Architect

**Purpose:** Design system architecture, service boundaries, tech stack

**Example Prompt:**
```
"You are a technical architect designing a flight booking system.

Design a 2-3 microservice architecture:
- What services do we need? (e.g., Search API, Booking API, Frontend)
- What does each service do?
- How do they communicate?
- What databases/storage do we need?
- What's the recommended tech stack?
- What are the deployment considerations?

Deliverable: Architecture diagram (text/ASCII) with technical specifications"
```

**Output you'll get:**
- Service architecture
- Tech stack recommendations
- Database schemas
- API contracts

---

#### 5. Product Manager (Vision)

**Purpose:** Define product vision, prioritize features, create roadmap

**Example Prompt:**
```
"You are a product manager for a new airline booking portal.

Create a product vision and roadmap:
- What's our unique value proposition?
- What features are must-have for launch?
- What features can wait until post-launch?
- What's the MVP (minimum viable product)?
- How do we prioritize: Q1 research, Q2 investor demo, Q3-Q4 launch?

Deliverable: Product vision doc with prioritized feature roadmap"
```

**Output you'll get:**
- Product vision statement
- Feature prioritization
- MVP definition
- Roadmap for Q2-Q4

---

### Q1 Workflow Examples

#### Example 1: Research-Driven Approach

**Timeline for 60-minute Q1:**

```
Minutes 0-5: You decide on research questions

Minutes 5-25: Agent 1 (Researcher)
"Research best practices in flight booking UX"
[Agent researches, you review output]

Minutes 25-45: Agent 2 (UX Designer)
"Based on this research: [paste], create wireframes for our booking flow"
[Agent creates wireframes, you review]

Minutes 45-55: Agent 3 (Technical Architect)
"Based on these wireframes: [paste], design a 3-service architecture"
[Agent designs architecture]

Minutes 55-60: You compile vision doc, prepare demo
```

**Demo:** Present research insights, wireframes, and architecture plan.

---

#### Example 2: Vision-First Approach

**Timeline for 60-minute Q1:**

```
Minutes 0-5: You define high-level vision

Minutes 5-20: Agent 1 (Product Manager)
"Create product vision and feature roadmap for airline booking portal"

Minutes 20-35: Agent 2 (Business Analyst)
"Based on this vision: [paste], define detailed requirements and user flows"

Minutes 35-50: Agent 3 (UX Designer)
"Based on these requirements: [paste], create wireframes"

Minutes 50-60: Agent 4 (Technical Architect)
"Based on this UX: [paste], design service architecture"
```

**Demo:** Present complete vision doc with requirements, wireframes, and architecture.

---

#### Example 3: Quick MVP Approach

**Timeline for 60-minute Q1:**

```
Minutes 0-10: Agent 1 (Product Manager)
"Define MVP feature set for booking portal"

Minutes 10-30: Agent 2 (Backend Dev)
"Build simplest possible search API with mock data"

Minutes 30-50: Agent 3 (Frontend Dev)
"Build basic search UI calling the API"

Minutes 50-60: Polish and demo
```

**Demo:** Show working MVP + explain how you'll build on it in Q2.

---

### Q1 Deliverable Options

You have flexibility in what you deliver in Q1:

#### Option A: Vision Document
**Best for:** Complex domains, need clarity before building

**Contents:**
- Research insights
- Product vision
- User flows and wireframes
- Service architecture
- Tech stack decisions
- Roadmap for Q2-Q4

**Created by:** PM, BA, UX, Architect agents

---

#### Option B: Wireframes + Architecture
**Best for:** Visual thinkers, design-first approach

**Contents:**
- Detailed wireframes for all screens
- Architecture diagram
- API contracts between services
- Database schemas

**Created by:** UX Designer, Technical Architect agents

---

#### Option C: Simple MVP
**Best for:** "Show me, don't tell me" approach, time to spare

**Contents:**
- Very basic working prototype
- Core flow only (search → results)
- Proves technical feasibility

**Created by:** Backend + Frontend agents

---

#### Option D: Hybrid
**Best for:** Balanced approach

**Contents:**
- Short vision doc (1-2 pages)
- Key wireframes (3-4 screens)
- Simple MVP or proof-of-concept

**Created by:** Mix of PM, UX, and Dev agents

---

### Transitioning from Q1 to Q2

**At end of Q1, you should have:**
- Clear understanding of what to build
- Architecture designed (2-3 services defined)
- Plan for which agents will build which services
- Prioritized feature list

**In Q2, you execute:**
- Build services based on Q1 architecture
- Implement features based on Q1 prioritization
- Use Q1 wireframes as implementation guide

**Example transition:**
```
Q1 Output: "We'll build 3 services: Search API, Booking API, Frontend"

Q2 Plan:
- Agent Team A (Backend): Build Search API based on Q1 architecture
- Agent Team B (Backend): Build Booking API based on Q1 architecture
- Agent Team C (Frontend): Build UI based on Q1 wireframes
```

---

### Why This Matters

**Without Q1 planning:**
- Build the wrong thing, waste Q2-Q4 rebuilding
- Unclear architecture, services don't integrate
- No vision, demo lacks coherence

**With Q1 planning:**
- Confident execution in Q2-Q4
- Clear architecture, easy integration
- Compelling demos with clear narrative

**Q1 is an investment that pays off in Q2-Q4.**

---

## ROLES IN YOUR ORGANIZATION

In a real company, your department would have specialists. As a director with Claude agents, you can assign agents to these roles:

### 1. Product Manager (PM)

**What they do:** Define requirements, prioritize features, write specifications

**When to use:**
- Beginning of complex quarters
- When you're unsure what to build
- When requirements are ambiguous

**Agent prompt example:**
```
"You are a product manager for a flight booking portal.

Define requirements for a seat selection feature:
- User stories (as a customer, I want to...)
- Acceptance criteria (how do we know it's done?)
- Edge cases to handle
- Success metrics

Deliverable: Product requirements document"
```

**Output you'll get:**
- Clear feature definition
- Requirements you can hand to dev teams
- Edge cases to test

---

### 2. Backend Developer

**What they do:** Build APIs, databases, business logic, data processing

**When to use:**
- Building services, APIs, data models
- Most quarters - every service needs a backend

**Agent prompt example:**
```
"You are a backend developer.

Build a Flask API for flight search with:
- GET /flights?origin={}&dest={}&date={}
- SQLite database with flights table
- Include 10 mock flights
- Run on port 5001
- Add basic error handling

Deliverable: Python file I can run with 'python app.py'"
```

**Output you'll get:**
- Working API service
- Database schema
- Runnable code

---

### 3. Frontend Developer

**What they do:** Build UIs, user interactions, visual components

**When to use:**
- Building web pages, forms, dashboards
- Any customer-facing or admin interface

**Agent prompt example:**
```
"You are a frontend developer.

Build a flight search interface with:
- Search form (origin, destination, date inputs)
- Results display (grid of flight cards)
- Book button for each flight
- Modern, responsive design
- Calls API at http://localhost:5001/flights

Tech: React or vanilla JavaScript
Deliverable: HTML/JS I can open in a browser"
```

**Output you'll get:**
- Working UI
- Styled interface
- JavaScript to call APIs

---

### 4. QA Engineer

**What they do:** Test features, find bugs, validate quality, write test cases

**When to use:**
- After building features, before demos
- When you want to find issues before users do
- Last 5-10 minutes of a quarter

**Agent prompt example:**
```
"You are a QA engineer testing a flight booking API.

Test this code:
[paste your API code]

Find and report:
- 5 bugs or edge cases that break the API
- 3 missing input validations
- 2 error handling issues
- 1 performance problem

For each issue:
- Describe the problem
- Show how to reproduce it
- Suggest severity (critical/major/minor)"
```

**Output you'll get:**
- List of bugs you missed
- Test cases to verify
- Prioritized issues to fix

---

### 5. Business Analyst

**What they do:** Analyze requirements, define data flows, create specifications

**When to use:**
- Complex features with unclear requirements
- Need to understand business logic
- Before building, to clarify what to build

**Agent prompt example:**
```
"You are a business analyst for airline booking systems.

Define the complete booking flow:
- Step-by-step process from search to confirmation
- Data required at each step
- Business rules (cancellations, refunds, seat changes)
- Integration points with other systems (inventory, payment)
- Error scenarios and how to handle them

Deliverable: Business process document with flowchart"
```

**Output you'll get:**
- Detailed process flows
- Data requirements
- Business rules clarified

---

### 6. DevOps Engineer

**What they do:** Setup infrastructure, deployment, Docker, scripts, automation

**When to use:**
- Need to run multiple services together
- Want to automate startup/teardown
- Deploying or packaging services

**Agent prompt example:**
```
"You are a DevOps engineer.

Create a docker-compose.yml to run these services:
- Search API on port 5001
- Booking API on port 5002
- Frontend on port 3000

Make it so I can:
- Start all services with 'docker-compose up'
- Stop all with 'docker-compose down'
- See logs from all services

Deliverable: docker-compose.yml and README with instructions"
```

**Output you'll get:**
- Docker configuration
- Scripts to run everything
- Instructions

---

### 7. UX Designer

**What they do:** Design user flows, wireframes, improve user experience

**When to use:**
- Planning UI before building
- Improving existing interfaces
- Making things more user-friendly

**Agent prompt example:**
```
"You are a UX designer.

Review this flight booking interface:
[paste code or describe current UI]

Suggest improvements for:
- User flow (is it intuitive?)
- Visual design (modern and professional?)
- Accessibility (screen readers, keyboard navigation)
- Mobile responsiveness

Deliverable:
- 3 high-priority UX improvements with mockups
- Before/after comparison"
```

**Output you'll get:**
- UX recommendations
- Design suggestions
- Accessibility fixes

---

### 8. Technical Writer

**What they do:** Write documentation, API docs, user guides

**When to use:**
- Need to document APIs for integration
- Preparing for demos
- Other teams need to use your services

**Agent prompt example:**
```
"You are a technical writer.

Document this booking API:
[paste API code]

Create:
- API reference (all endpoints, parameters, responses)
- Quick start guide (how to run it)
- Example requests with curl
- Error codes and meanings

Deliverable: README.md with complete API documentation"
```

**Output you'll get:**
- Professional documentation
- Examples for integration
- User guides

---

## ORGANIZING YOUR AGENT TEAMS

### Scenario 1: Building a New Feature (Q1)

**Use case:** Starting from scratch

**Team structure:**
```
Agent 1 (Product Manager):
"Define requirements for flight search feature"
↓
Agent 2 (Backend Dev):
"Build search API based on these requirements: [paste PM output]"
↓
Agent 3 (Frontend Dev):
"Build search UI calling this API: [paste API details]"
↓
Agent 4 (QA):
"Test the complete search flow, find bugs"
```

**Timeline for 60-minute quarter:**
- 0-10 min: PM defines requirements (you review)
- 10-30 min: Backend and Frontend in parallel
- 30-50 min: QA tests, devs fix bugs
- 50-60 min: Final testing and demo prep

---

### Scenario 2: Improving Existing Feature (Q2-Q3)

**Use case:** Building on previous work

**Team structure:**
```
Agent 1 (Business Analyst):
"Analyze current booking flow, suggest improvements"
↓
Agent 2 (Frontend Dev):
"Implement these improvements: [paste BA suggestions]"
↓
Agent 3 (UX Designer):
"Review and polish the improved interface"
```

**Timeline for 60-minute quarter:**
- 0-15 min: BA analyzes and suggests
- 15-45 min: Frontend implements
- 45-60 min: UX reviews and polishes

---

### Scenario 3: Quick Iteration (30-minute quarter)

**Use case:** Fast turnaround, time pressure

**Team structure:**
```
Agent 1 (Backend Dev):    ⎫
"Build API..."            ⎬ Parallel!
Agent 2 (Frontend Dev):   ⎭
"Build UI..."

[You integrate manually]
```

**Timeline for 30-minute quarter:**
- 0-20 min: Both agents work in parallel
- 20-25 min: You integrate and test
- 25-30 min: Demo prep

---

### Scenario 4: Polish and Prepare for Demo

**Use case:** End of quarter, need quality

**Team structure:**
```
Agent 1 (QA):
"Test everything, create comprehensive bug list"
↓
Agent 2 (Backend + Frontend Dev):
"Fix all critical bugs: [paste bug list]"
↓
Agent 3 (Technical Writer):
"Document API for demo, create demo script"
```

**Timeline for 30-minute quarter:**
- 0-10 min: QA finds all issues
- 10-25 min: Devs fix issues
- 25-30 min: Final test and demo prep

---

### Choosing Team Size

**2 agents:**
- Simple features
- Time pressure (< 30 min)
- Pattern: Build + Test, or Backend + Frontend

**3 agents (most common):**
- Standard features
- 30-60 minute quarters
- Pattern: Backend + Frontend + Integration/QA

**4 agents:**
- Complex features
- 60+ minute quarters
- Pattern: PM + Backend + Frontend + QA

**5+ agents:**
- Rarely needed
- Risk of coordination overhead
- Only for very complex multi-service builds

---

## DELEGATION BEST PRACTICES

### 1. Match Agents to Roles, Not Just Tasks

**❌ Don't:**
```
Agent 1: "Build everything for the booking feature"
```

**✅ Do:**
```
Agent 1 (Backend Dev): "Build booking API"
Agent 2 (Frontend Dev): "Build booking UI"
Agent 3 (QA): "Test booking flow"
```

**Why:** Specialization produces better results, clearer ownership, easier to debug.

---

### 2. Start with a PM Agent for Complex Features

**When requirements are unclear:**

**Step 1 - PM Agent:**
```
"You are a product manager.
Define requirements for seat selection feature:
- User stories
- Acceptance criteria
- Data requirements"
```

**Step 2 - Review PM output:**
- Does this make sense?
- Is it achievable in this quarter?
- Any missing pieces?

**Step 3 - Hand requirements to dev agents:**
```
"Agent 2 (Backend): Build seat selection API based on these requirements:
[paste PM output]"
```

**Why:** Prevents building the wrong thing. 10 minutes of planning saves 30 minutes of rework.

---

### 3. Always End with a QA Agent Before Demos

**Never demo without testing.**

**Last 5-10 minutes of every quarter:**
```
"Agent (QA): Test this complete system:
[paste or describe what you built]

Find:
- Bugs that would embarrass us in demo
- Edge cases that crash the system
- Missing validations

Focus on critical issues only, we have 5 minutes."
```

**Then fix critical issues before demo.**

**Why:** Better to find bugs yourself than during demo. Shows professionalism.

---

### 4. Use Specialists, Not Generalists

**❌ Don't:**
```
"Agent 1, build the API and UI and tests and documentation"
```

**✅ Do:**
```
Agent 1 (Backend): "Build API"
Agent 2 (QA): "Write tests"
Agent 3 (Tech Writer): "Create documentation"
```

**Why:** Agents produce better output when given focused, specialized tasks.

---

### 5. Trust Your Teams, But Verify

**Trust:**
- Agents are generally capable
- Let them figure out implementation
- Don't micromanage every line of code

**But verify:**
- Always test agent output yourself
- Run the code, don't just read it
- Test edge cases
- Verify integration between services

**Process:**
1. Agent delivers code
2. You run it locally
3. You test the happy path
4. You test 2-3 edge cases
5. If it works → move on
6. If it breaks → give agent error, ask to fix

---

### 6. Timebox Your Decisions

**Directors decide quickly and adapt.**

**❌ Don't:**
- Spend 10 minutes debating Flask vs. FastAPI
- Spend 15 minutes choosing the perfect CSS framework
- Spend 20 minutes optimizing before anything works

**✅ Do:**
- Pick Flask (you know it) → move on
- Pick Bootstrap (it's fast) → move on
- Make it work first, optimize if time permits

**Timebox rule:**
- Architecture decisions: 2 minutes max
- Tech stack decisions: 1 minute max
- "Should I fix this bug?" decisions: 30 seconds max

**Why:** In a 30-minute quarter, every minute matters. Decide, move, adapt if needed.

---

### 7. Focus on Outcomes, Not Process

**You don't care HOW agents build it, you care THAT it works.**

**❌ Don't ask:**
- "Did you use the exact algorithm I described?"
- "Did you structure the code the way I would?"
- "Did you use the same variable names I prefer?"

**✅ Do ask:**
- "Does it return correct flight data?"
- "Can I demo this successfully?"
- "Does it integrate with the other service?"

**Let agents figure out implementation details.**

**Your job:** Define WHAT and WHY, let agents figure out HOW.

---

### 8. Delegate the Grunt Work

**Everything that doesn't require your judgment can be delegated:**

| Task | Who Does It |
|------|-------------|
| Debugging error messages | QA finds it, Backend fixes it |
| Writing tests | QA agent |
| Improving CSS styling | Frontend or UX agent |
| Writing documentation | Technical Writer agent |
| Setting up Docker | DevOps agent |
| Finding edge cases | QA agent |

**You focus on:**
- What to build (strategy)
- Does it meet requirements? (review)
- How do services integrate? (architecture)
- Are we ready to demo? (quality gate)

---

## COMMON DIRECTOR MISTAKES

### Mistake 1: Too Many Agents

**Symptom:**
- Managing 5+ agents simultaneously
- Spending more time coordinating than building
- Agents producing conflicting outputs

**Why it happens:**
- Thinking more agents = faster
- Not accounting for coordination overhead

**Solution:**
- Stick to 2-3 agents for 30-min quarters
- Stick to 3-4 agents for 60-min quarters
- More than 4 agents → you're over-complicating

**Example:**
```
❌ 6 agents: API, Database, Frontend, Tests, Docs, Integration
✅ 3 agents: Backend (API+DB), Frontend, QA (Tests+Docs)
```

---

### Mistake 2: Not Testing Before Demos

**Symptom:**
- Code looks good in agent output
- Demo fails because code doesn't actually run
- Embarrassing moment during presentation

**Why it happens:**
- Assuming agent output works
- Time pressure, skip testing
- Trust without verification

**Solution:**
- Always reserve last 5 minutes for testing
- Run the code yourself
- Test the demo flow
- Have a backup plan if something breaks

**Process:**
```
Minutes 0-25: Build
Minutes 25-28: Test everything yourself
Minutes 28-30: Fix critical issues or prepare backup
```

---

### Mistake 3: Micromanaging Agents

**Symptom:**
- Writing 500-word prompts with every implementation detail
- Telling agents exactly what code to write line-by-line
- Spending more time writing prompts than agents spend coding

**Why it happens:**
- Fear of agents doing it wrong
- Not trusting agent capabilities
- Trying to maintain control

**Solution:**
- Give objectives, not instructions
- Trust agents to figure out implementation
- Review output, not process

**Example:**
```
❌ Micromanaging:
"Create a variable called flightList on line 5. Loop through it
starting at index 0. For each element, check if the origin matches..."

✅ Delegating:
"Build a function that filters flights by origin and destination.
Return matching flights as JSON."
```

---

### Mistake 4: Building Before Planning

**Symptom:**
- Start coding immediately
- Halfway through, realize you're building the wrong thing
- Waste time backtracking

**Why it happens:**
- Time pressure → skip planning
- Eager to see results
- Misunderstand requirements

**Solution:**
- First 5 minutes: Plan (what services? what agents?)
- Next 5 minutes: Agent 1 (PM or BA) clarifies requirements
- Then: Start building

**Example:**
```
✅ Good flow:
0-5 min: You plan architecture (3 services, which agents)
5-10 min: PM agent defines requirements
10-15 min: Review requirements, adjust plan if needed
15-60 min: Build with confidence

❌ Bad flow:
0-30 min: Build frantically
30 min: Realize you built search but demo needs booking
30-60 min: Scramble to rebuild
```

---

### Mistake 5: Sequential When You Could Parallelize

**Symptom:**
- Agents waiting idle
- Backend finishes in 10 minutes, then frontend starts
- 60-minute quarter feels slow

**Why it happens:**
- Default to sequential thinking
- Not recognizing independent work
- Over-specifying dependencies

**Solution:**
- Ask: "Do these agents REALLY need to wait for each other?"
- Parallelize whenever possible
- Use API contracts instead of actual code

**Example:**
```
❌ Sequential (60 minutes):
Agent 1: Build API (20 min) → Wait →
Agent 2: Build UI (20 min) → Wait →
Agent 3: Test (20 min)

✅ Parallel (25 minutes):
Agent 1: Build API (20 min) ⎫
Agent 2: Build UI (20 min) ⎬ Parallel!
                            ⎭
Agent 3: Test both (5 min)
```

---

### Mistake 6: Ignoring Integration Until the End

**Symptom:**
- 3 services built separately
- Demo time: They don't talk to each other
- Scramble to make them work together

**Why it happens:**
- Focus on building, forget integration
- Assume "it'll just work"
- No integration agent assigned

**Solution:**
- Reserve time for integration (5-10 min minimum)
- Test services together before demo
- Use integration agent to connect them

**Process:**
```
Minutes 0-20: Build services
Minutes 20-25: Integration agent connects them
Minutes 25-28: Test end-to-end flow
Minutes 28-30: Demo prep
```

---

### Mistake 7: Not Adapting When Things Go Wrong

**Symptom:**
- Agent produces broken code
- Spend 15 minutes trying to fix the same issue
- Run out of time, demo fails

**Why it happens:**
- Stubbornness ("I can fix this")
- Sunk cost fallacy ("I already spent 10 minutes")
- Not willing to pivot

**Solution:**
- Timebox debugging: 5 minutes max
- If still broken → pivot strategy
- Simplify scope or switch approach

**Decision tree:**
```
Agent produces code → Test it

Works? → Great, move on
Broken? → Give error to agent, ask to fix

Fixed? → Great, move on
Still broken after 5 min? → PIVOT

Pivot options:
- Simplify the feature
- Use mock data instead
- Build simpler version
- Defer to next quarter
```

---

## QUICK REFERENCE

### Role Selection Cheat Sheet

**Need to define what to build?** → PM or Business Analyst
**Need to build an API?** → Backend Developer
**Need to build a UI?** → Frontend Developer
**Need to test and find bugs?** → QA Engineer
**Need to improve UX?** → UX Designer
**Need to run multiple services?** → DevOps Engineer
**Need documentation?** → Technical Writer

### Team Size Guidelines

| Quarter Length | Number of Agents | Typical Roles |
|----------------|------------------|---------------|
| 30 minutes | 2-3 agents | Backend + Frontend + Integration |
| 60 minutes | 3-4 agents | PM + Backend + Frontend + QA |
| Complex feature | 4 agents | PM + Backend + Frontend + QA |
| Simple iteration | 2 agents | Dev + QA |

### Time Allocation Guide

**30-minute quarter:**
- 0-2 min: Plan strategy
- 2-22 min: Agents build
- 22-25 min: Integration
- 25-28 min: Testing
- 28-30 min: Demo prep

**60-minute quarter:**
- 0-5 min: Plan strategy
- 5-15 min: PM/BA define requirements
- 15-50 min: Agents build (parallel when possible)
- 50-55 min: Integration
- 55-58 min: Testing
- 58-60 min: Demo prep

### Director's Pre-Quarter Checklist

Before starting a quarter, ask yourself:

- [ ] What does success look like for this quarter?
- [ ] What's the minimum viable demo?
- [ ] How many services will I build? (2-3 recommended)
- [ ] Which agents do I need? (List roles)
- [ ] Can any agents work in parallel?
- [ ] What's my integration strategy?
- [ ] What can I defer to next quarter?

### Director's Pre-Demo Checklist

Before demoing, verify:

- [ ] All services actually run (tested yourself)
- [ ] Happy path works end-to-end
- [ ] You've tested the exact flow you'll demo
- [ ] You can explain your multi-agent strategy
- [ ] You have a backup plan if something breaks
- [ ] You know which agents built which services

---

## FINAL WORDS

**Being a director is different from being an engineer.**

**Engineers build. Directors orchestrate.**

Your success isn't measured by lines of code you write - it's measured by:
- Working software your teams deliver
- Quality of demos you present
- Effectiveness of your delegation
- Speed of your decision-making
- Ability to adapt when things go wrong

**Trust your teams. Guide them. Review their work. But let them build.**

That's what directors do.

Good luck! 🚀
