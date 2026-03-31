# DIRECTOR'S GUIDE
## Managing Your Organization with Claude Agent Teams

**Purpose:** Learn to think and operate as a director managing multiple agent teams building microservices.

**Audience:** Engineers (junior to senior) learning to manage teams rather than code themselves

**Prerequisites:** Read TUTORIAL.md first for multi-agent mechanics. This guide focuses on the director mindset and strategy.

**Complements:** TUTORIAL.md (covers agent mechanics), this guide (covers director role)

---

## TABLE OF CONTENTS

1. [Thinking Like a Director](#thinking-like-a-director)
2. [Using Agents for Research & Planning](#using-agents-for-research--planning)
3. [Delegation Principles](#delegation-principles)
4. [Common Director Mistakes](#common-director-mistakes)
5. [Quick Reference](#quick-reference)

> **Note:** For detailed agent roles, prompt patterns, and multi-agent coordination techniques, see TUTORIAL.md

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

## DELEGATION PRINCIPLES

**For detailed agent roles and prompt templates, see TUTORIAL.md. This section focuses on director-level delegation strategy.**

### Core Principles

**1. Match Agents to Roles**
- Assign specialized roles (Backend, Frontend, QA) not generic tasks
- Specialization produces better results and clearer ownership
- See TUTORIAL.md for detailed role descriptions and prompt examples

**2. Start with Planning for Complex Features**
- Use PM or BA agents to define requirements before building
- 10 minutes of planning saves 30 minutes of rework
- Review planning output before delegating to dev agents

**3. Always End with QA Before Demos**
- Reserve last 5-10 minutes of every quarter for testing
- Find bugs yourself before the demo
- Fix critical issues, defer minor ones

**4. Trust Teams, But Verify**
- Let agents determine HOW to implement
- You define WHAT needs to be built and WHY
- Test outputs yourself (run code, test happy path + 2-3 edge cases)
- Verify integration between services

**5. Timebox Decisions**
- Architecture decisions: 2 minutes max
- Tech stack choices: 1 minute max
- Bug fix priority: 30 seconds max
- In a 30-minute quarter, every minute matters

**6. Focus on Outcomes, Not Process**
- Care about working software, not implementation details
- Ask "Does it work?" not "Did you code it my way?"
- Review results, not how agents got there

**7. Delegate Grunt Work**
- Bug finding → QA agent
- Test writing → QA agent
- Documentation → Technical Writer agent
- CSS polish → Frontend/UX agent
- Docker setup → DevOps agent

**You focus on:**
- Strategy (what to build)
- Review (does it meet requirements?)
- Architecture (how services integrate)
- Quality gates (ready to demo?)

---

## COMMON DIRECTOR MISTAKES

**Note:** For general multi-agent pitfalls (context loss, conflicting outputs, etc.), see TUTORIAL.md. This section focuses on mistakes specific to the director role.

### Mistake 1: Coding Instead of Directing

**Symptom:**
- You're writing code yourself
- Agents sitting idle while you debug
- Mixing director and engineer roles

**Why it happens:**
- Old habits from being an engineer
- "It's faster if I just do it myself"
- Not trusting agents with implementation

**Solution:**
- If you catch yourself coding, STOP
- Delegate the coding to an agent
- Your job: define requirements, review output, make decisions
- Only touch code for final integration or critical debugging

**Example:**
```
❌ Director behavior:
[Opens VS Code, writes API endpoint, debugs for 15 minutes]

✅ Director behavior:
"Agent 3, this endpoint is returning 500 errors. Here's the error log.
Fix it and test the endpoint."
```

---

### Mistake 2: Micromanaging Implementation

**Symptom:**
- Writing detailed line-by-line instructions
- Telling agents exactly how to code
- 500-word prompts with implementation details

**Why it happens:**
- Fear of agents doing it wrong
- Perfectionism
- Not trusting agent capabilities

**Solution:**
- Give objectives and requirements, not instructions
- Let agents figure out HOW
- Review output, not process

**Example:**
```
❌ Micromanaging:
"Import Flask on line 1. Create app variable on line 2.
Define search_flights function on line 5..."

✅ Directing:
"Build a Flask API with GET /flights endpoint.
Return JSON array of flights filtered by origin and destination."
```

---

### Mistake 3: Building Before Planning (Director Anti-Pattern)

**Symptom:**
- Jump straight to coding in Q1
- Halfway through quarter, realize wrong approach
- No clear architecture, services don't integrate

**Why it happens:**
- Time pressure feels urgent
- Want to see immediate results
- Undervalue planning phase

**Solution:**
- Q1 is for PLANNING, not building (usually)
- Spend 40-50 minutes on research, architecture, requirements
- Build simple MVP only if time permits
- Enter Q2 with clear vision and architecture

**Example:**
```
❌ Bad Q1:
0-60 min: Build services frantically, unclear requirements
[Enter Q2 confused about architecture]

✅ Good Q1:
0-20 min: Research agent analyzes domain
20-40 min: Architect agent designs 3-service architecture
40-55 min: PM agent defines Q2-Q4 roadmap
55-60 min: Polish vision document
[Enter Q2 with clear plan]
```

---

### Mistake 4: Not Adapting Strategy

**Symptom:**
- Agent stuck on same problem for 15 minutes
- Keep trying same broken approach
- Run out of time, demo fails

**Why it happens:**
- Stubbornness, sunk cost fallacy
- Not willing to pivot or simplify
- Attachment to original plan

**Solution:**
- Timebox attempts: 5 minutes max on any single issue
- If broken after 5 min → change strategy
- Simplify scope, defer to next quarter, or switch approach

**Decision tree:**
```
Agent output broken?
├─ Try to fix (5 min max)
├─ Still broken? → PIVOT
│   ├─ Simplify feature
│   ├─ Use mock data
│   ├─ Build simpler version
│   └─ Defer to next quarter
└─ Fixed? → Move on
```

---

### Mistake 5: Treating All 4 Quarters the Same

**Symptom:**
- Same approach in Q1 as Q4
- Not escalating scope across quarters
- Missing opportunity to build incrementally

**Why it happens:**
- Not understanding quarter progression
- Treating each quarter as independent
- No long-term vision

**Solution:**
- Q1: Research, planning, architecture (build vision)
- Q2: Build core MVP (investor demo ready)
- Q3-Q4: Add features, polish, scale
- Each quarter builds on previous quarters

**Example:**
```
✅ Good progression:
Q1: Vision doc, architecture, wireframes
Q2: Basic search + booking (demo to investors)
Q3: Add payments, seat selection
Q4: Polish UX, performance, launch prep

❌ Bad progression:
Q1: Build search
Q2: Rebuild search differently
Q3: Build booking from scratch
Q4: Scramble to integrate everything
```

---

## QUICK REFERENCE

### Director Mindset Cheat Sheet

| Engineer Thinks | Director Thinks |
|-----------------|-----------------|
| "I'll build the API" | "Agent Team A will build the API" |
| "How do I code this?" | "What outcome do I need?" |
| "Let me debug this" | "QA team, find bugs. Dev team, fix them" |
| "This needs to be perfect" | "This needs to ship, we can improve later" |
| "I need to understand every line" | "I need to understand the architecture" |

### Quarter Strategy Guide

**Q1 (Research & Planning):**
- Focus: Vision, architecture, requirements
- Agents: Researcher, PM, BA, Technical Architect, UX Designer
- Deliverable: Vision doc, wireframes, architecture design
- Success: Clear plan for Q2-Q4

**Q2 (Core MVP):**
- Focus: Build working demo for investors
- Agents: Backend, Frontend, QA
- Deliverable: Basic search + booking flow
- Success: End-to-end demo of core functionality

**Q3-Q4 (Enhancement & Polish):**
- Focus: Add features, improve UX, scale
- Agents: Backend, Frontend, UX, DevOps, QA
- Deliverable: Production-ready system
- Success: Polished, feature-complete product

### Director Decision Framework

**When planning:**
- What's the minimum viable demo?
- How many services? (2-3 recommended)
- Which agents? What roles?
- What can be deferred?

**When delegating:**
- Define WHAT and WHY, not HOW
- Match agents to specialized roles
- Can agents work in parallel?
- Reserve time for integration and testing

**When reviewing:**
- Does it run?
- Does it meet requirements?
- Ready to demo or needs revision?
- Integration issues?

**When adapting:**
- If stuck for 5 minutes → pivot
- Simplify scope, use mocks, or defer
- Decide fast, adapt as needed

### Director's Pre-Demo Checklist

- [ ] All services run (tested yourself)
- [ ] Happy path works end-to-end
- [ ] You've practiced the demo flow
- [ ] You can explain your multi-agent strategy
- [ ] Backup plan if something breaks
- [ ] Know which agents built which services

---

## FINAL WORDS

**Being a director is different from being an engineer.**

Engineers build. Directors orchestrate.

Your success is measured by:
- Working software your teams deliver
- Quality of demos you present
- Effectiveness of your delegation
- Speed of your decision-making
- Ability to adapt when things go wrong

**Trust your teams. Guide them. Review their work. But let them build.**

That's what directors do.

**Next Steps:**
1. Read TUTORIAL.md for multi-agent mechanics and patterns
2. Start with Q1 research and planning (don't rush to code)
3. Practice delegating instead of coding
4. Review this guide between quarters to stay in director mindset

Good luck!
