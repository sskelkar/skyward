# SKYWARD
## A Multi-Agent Coding Workshop Game

**Format:** Collaborative learning workshop
**Players:** 4-6 backend engineers
**Duration:** Half day (6 hours with lunch break, 10am-4pm)
**Core Goal:** Learn multi-agent orchestration by building an airline startup

📋 **For Facilitators:** See [GAMERUNNER.md](GAMERUNNER.md) for detailed facilitation guide, scoring rubrics, and randomness mechanics.

---

## GAME PREMISE

You are directors of engineering at **SkywardAI**, a new airline startup racing to launch in 1 year. Each director runs an independent department and builds systems using a team of Claude agents working together.

**The Learning Goal:** Master multi-agent orchestration - learning to coordinate multiple Claude agents, divide work effectively, and build working software faster than you could alone. Each director builds 2-3 microservices using specialized agent teams.

**The Challenge:** Across 4 quarters, demonstrate working software running locally on your laptop. Start with research and vision (Q1), build for investors (Q2), navigate market chaos (Q3), and launch to the world (Q4).

**The Constraint:** Everything runs locally - no cloud deployment, no hosting, just your laptop and Claude agents.

---

## THE 8 DIRECTOR ROLES

Each role is designed for independent work with minimal dependencies on other departments. Players can choose from 8 distinct roles based on their interests and comfort level.

**For 4-6 players:** Select the roles that best fit your group. All roles work independently.

**Character sheets:** Detailed character sheets for each role are in the `characters/` directory.

---

### 1. Director of Customer Booking Portal
**Department:** Customer Experience - Frontend
**Your Mission:** Build the customer-facing flight booking application

**What You'll Build:**
- Flight search interface (date, origin, destination)
- Flight results display with pricing
- Seat selection interface
- Booking confirmation system
- User account management

**Multi-Agent Strategy:**
- Agent 1: Frontend developer (React/Vue/vanilla JS)
- Agent 2: API client & integration
- Agent 3: UI/UX refinement & testing

**Demo Each Quarter:** Show customers searching and booking flights

**Character Description:**
You're the face of the company - if customers can't book flights easily, nothing else matters. You care deeply about user experience and visual polish. Your agents should produce interfaces that actually look good and work smoothly.

---

### 2. Director of Flight Inventory & Scheduling
**Department:** Operations - Backend Systems
**Your Mission:** Build the flight schedule and seat inventory management system

**What You'll Build:**
- Flight schedule database (routes, times, aircraft)
- Seat inventory tracking (available vs. booked)
- Real-time availability API
- Overbooking logic & algorithms
- Schedule optimization tools

**Multi-Agent Strategy:**
- Agent 1: Database architect & schema design
- Agent 2: Business logic & APIs
- Agent 3: Admin dashboard & tools

**Demo Each Quarter:** Show flight schedules, seat tracking, availability updates

**Character Description:**
You're the operational backbone - every flight, seat, and schedule flows through your systems. You love data structures, algorithms, and systems that never lose a single seat. Your agents should build bulletproof inventory tracking.

---

### 3. Director of Pricing & Revenue Optimization
**Department:** Finance - Analytics & ML
**Your Mission:** Build dynamic pricing and revenue optimization systems

**What You'll Build:**
- Dynamic pricing engine (demand-based)
- Competitor price monitoring
- Revenue analytics dashboard
- Discount & promotion system
- Price prediction models

**Multi-Agent Strategy:**
- Agent 1: Pricing algorithms & ML models
- Agent 2: Data analytics & visualization
- Agent 3: Testing & simulation

**Demo Each Quarter:** Show pricing changes, revenue projections, analytics dashboard

**Character Description:**
You're the money-maker - maximizing revenue per flight while staying competitive. You think in terms of yield management, price elasticity, and optimization. Your agents should build sophisticated pricing that actually makes business sense.

---

### 4. Director of Personalization & Recommendations
**Department:** Product - ML & Data Science
**Your Mission:** Build recommendation and personalization systems

**What You'll Build:**
- Destination recommendation engine
- Personalized flight suggestions
- Upselling system (premium seats, bags, etc.)
- User behavior tracking & analysis
- Email & notification personalization

**Multi-Agent Strategy:**
- Agent 1: Recommendation algorithms
- Agent 2: User profiling & data pipeline
- Agent 3: Testing & metrics

**Demo Each Quarter:** Show personalized recommendations for different user types

**Character Description:**
You're the growth hacker - using data to increase bookings and revenue per customer. You love A/B tests, ML models, and seeing conversion rates climb. Your agents should build recommendation systems that actually work.

---

### 5. Director of Customer Service & Support
**Department:** Support - Automation & Tools
**Your Mission:** Build customer support systems and self-service tools

**What You'll Build:**
- Chatbot / AI support assistant
- Ticket management system
- Refund & cancellation workflows
- FAQ & knowledge base
- Support agent dashboard

**Multi-Agent Strategy:**
- Agent 1: Chatbot & NLP
- Agent 2: Ticketing system & workflows
- Agent 3: Analytics & quality monitoring

**Demo Each Quarter:** Show chatbot handling customer issues, support tools in action

**Character Description:**
You're the customer advocate - when things go wrong, your systems save the day. You care about resolution time, customer satisfaction, and automation. Your agents should build support tools that reduce manual work.

---

### 6. Director of Marketing & Growth
**Department:** Marketing - Analytics & Automation
**Your Mission:** Build marketing systems and growth analytics

**What You'll Build:**
- Marketing campaign management
- Landing page A/B testing system
- Email campaign automation
- Attribution & analytics tracking
- Social media integration & monitoring

**Multi-Agent Strategy:**
- Agent 1: Campaign tools & automation
- Agent 2: Analytics & tracking
- Agent 3: Content generation & testing

**Demo Each Quarter:** Show campaigns running, A/B tests, growth metrics

**Character Description:**
You're the growth engine - bringing customers to the platform and making them convert. You love experiments, viral loops, and watching user numbers grow. Your agents should build marketing systems that drive measurable growth.

---

### 7. Director of Check-in & Boarding
**Department:** Operations - Passenger Services
**Your Mission:** Build the check-in and boarding systems

**What You'll Build:**
- Online check-in flow
- Interactive seat selection (seat map)
- Boarding pass generation with QR codes
- Boarding group management
- Gate operations dashboard

**Multi-Agent Strategy:**
- Agent 1: Check-in backend & seat assignment
- Agent 2: Seat map UI & selection
- Agent 3: Boarding pass generator & QR codes

**Demo Each Quarter:** Show check-in flow, seat selection, boarding pass with QR code

**Character Description:**
You're the operations perfectionist - the gatekeeper who turns bookings into flights. You obsess over seat assignment algorithms, boarding efficiency, and making check-in seamless. Your agents should build systems that look like real airline software.

---

### 8. Director of Flight Status & Tracking
**Department:** Operations - Real-Time Systems
**Your Mission:** Build flight status and real-time tracking systems

**What You'll Build:**
- Flight status dashboard
- Live flight tracking map
- Departure/arrival boards (like at airport)
- Delay alerts and notifications
- Operations control center

**Multi-Agent Strategy:**
- Agent 1: Status backend & real-time updates
- Agent 2: Airport status board UI
- Agent 3: Flight map & tracking visualization

**Demo Each Quarter:** Show live status board, flight tracking map, delay notifications

**Character Description:**
You're the real-time information master - the single source of truth for flight status. You obsess over data freshness, accurate ETAs, and proactive passenger notifications. Your agents should build dashboards that feel like FlightRadar24.

---

## GAME STRUCTURE

### Half-Day Timeline (10am-4pm)

**Morning: Vision & Building**
- 10:00-10:30 | **Tutorial**: Multi-agent basics and Claude features
- 10:30-11:30 | **Q1 - Research & Vision** (60 min): Strategy, research, planning
- 11:30-12:30 | **Q2 - Investor Demo Build** (60 min): Build something impressive
- 12:30-13:00 | **Investor Demo**: Present to investors (gamerunner judges)

**Lunch Break**
- 13:00-14:00 | **LUNCH**

**Afternoon: Market Chaos & Launch**
- 14:00-14:45 | **Q3 - Chaos Quarter** (45 min): Dice-driven market challenge
- 14:45-15:30 | **Q4 - Launch Sprint** (45 min): Final polish, go live! 🎉
- 15:30-16:00 | **Performance Review**: VP promotion announcement

---

### Quarter-by-Quarter Breakdown

#### Q1: Research & Vision (60 min)
**Focus:** Strategy and planning, NOT working code yet

**What Directors Do:**
- Research best practices in their domain (use agents to analyze competitors)
- Define 2-3 service architecture for their department
- Create vision documents with wireframes/mockups
- Plan technical approach and agent team structure

**Deliverable Options:**
- Vision document with architecture diagrams
- Wireframes and user flows
- Simple MVP (if time permits)

**Agent Roles Commonly Used:**
- Business Analyst (research requirements)
- Product Manager (define vision)
- UX Designer (create wireframes)
- Technical Architect (design services)

**Demo:** Present your vision, explain your strategy for Q2-Q4

---

#### Q2: Investor Demo Build (60 min)
**Focus:** Build something impressive to show investors

**What Directors Do:**
- Build 1-2 working services based on Q1 vision
- Create demoable features (happy path works)
- Make it look professional and polished
- Focus on what investors want to see: value proposition

**Deliverable:**
- Working prototype with core flow
- Polished UI that looks production-ready
- Demo-ready system

**Agent Roles Commonly Used:**
- Backend Developer (build APIs)
- Frontend Developer (build UI)
- QA Engineer (test demo flow)

**Demo:** Live demo to "investors" (gamerunner + other directors)
**Scoring:** Gamerunner evaluates using investor demo rubric

---

#### Investor Demo & Lunch Break (30 min demo + 60 min lunch)
**What Happens:**
- Each director presents 3-5 minute demo
- Gamerunner (as investor) asks questions
- Investor demo scoring (see GAMERUNNER.md for rubric)
- Break for lunch

---

#### Q3: Chaos Quarter (45 min) - DICE DRIVEN
**Focus:** Rapid response to market chaos/opportunity

**What Happens:**
- Gamerunner rolls die to determine scenario (see table below)
- Directors must respond quickly under pressure
- Build new features, fix critical issues, or seize opportunities

**Possible Scenarios (roll 1d6):**
1. **Critical Bug** - Production issue causing failures, must fix immediately
2. **Competitor Attack** - Rival launched better feature, must differentiate
3. **Regulatory Audit** - Compliance issue to fix (accessibility, GDPR)
4. **Viral Traffic Spike** - Must handle 10x scale, optimize performance
5. **Budget Crisis** - Must reduce costs, optimize efficiency
6. **Partnership Opportunity** - Major partner wants integration, build API

**Deliverable:**
- Quick fix or feature responding to scenario
- Evidence of problem-solving under pressure
- Working response to crisis

**Demo:** Show how you handled the chaos (what you built, how it solves the problem)

---

#### Q4: Launch Sprint (45 min)
**Focus:** Final polish, production-ready, COMPANY LAUNCHES! 🎉

**What Directors Do:**
- Complete end-to-end customer/user flows
- Handle edge cases and error states
- Add loading states and user feedback
- Final UX polish and responsiveness
- Ensure demo-ready for launch presentation

**Deliverable:**
- Production-ready system
- Complete customer journey works end-to-end
- Professional appearance worthy of launch day

**Demo:** Full end-to-end flow demonstration
**Milestone:** SkywardAI officially launches to the world! 🚀

---

#### Performance Review (30 min)
**What Happens:**
- Gamerunner calculates final scores
- Announces VP of Engineering promotion winner
- Team retrospective and celebration

**Scoring Based On:**
- Delivery scores (Q1-Q4 demos)
- Tech debt score (code quality assessment)
- API cost efficiency
- Collaboration bonus

See GAMERUNNER.md for detailed scoring rubrics.

---

---

## TURN STRUCTURE

### How Each Quarter Works

**Note:** Q1 (Research & Vision) works differently from Q2-Q4 (Building). See below for both.

---

### Q1 Turn Structure (Research & Vision)

**1. Introduction (5 min)**
- Gamerunner explains Q1 focus: research and planning, not coding
- Directors ask clarifying questions
- Understand deliverable options (vision doc, wireframes, or MVP)

**2. Research & Planning with Agents (45-50 min)**
**Use agents for strategic work:**
- Research competitors and best practices
- Define requirements and user flows
- Create wireframes and mockups
- Design service architecture
- Plan technical approach

**Agent Roles for Q1:**
- Business Analyst
- Product Manager
- UX Designer
- Technical Architect
- Researcher

**Example Q1 workflow:**
```
Minutes 0-20: Agent 1 (Researcher)
"Research best practices for [your domain]"

Minutes 20-40: Agent 2 (UX Designer)
"Based on research, create wireframes for key flows"

Minutes 40-50: Agent 3 (Architect)
"Design 2-3 service architecture for this system"

Minutes 50-55: Compile vision doc, prepare presentation
```

**3. Vision Presentation (5 min per director)**
- Present your vision document, wireframes, or MVP
- Explain your strategy for Q2-Q4
- No scoring in Q1, just feedback

---

### Q2-Q4 Turn Structure (Building)

**1. Scenario Introduction (3-5 min)**
The gamerunner announces the quarter's challenge and goals.

**2. Build with Agents (most of the time)**
**This is where building happens!** You orchestrate multiple Claude agents to build your systems.

**Multi-Agent Orchestration Strategies:**

**Parallel Work:**
```
Agent 1: "Build the flight search API..."
Agent 2: "Create a React frontend..."
Agent 3: "Write integration tests..."
(All work simultaneously)
```

**Sequential Pipeline:**
```
Agent 1: "Design the database schema..."
→ Wait for completion →
Agent 2: "Using that schema, build the API..."
→ Wait for completion →
Agent 3: "Build the UI using that API..."
```

**Specialist Teams:**
```
Agent 1 (Backend specialist): "You own all backend services..."
Agent 2 (Frontend specialist): "You own all UI..."
Agent 3 (Testing specialist): "You own quality..."
```

**Iterative Refinement:**
```
Agent 1: "Build basic version..."
→ Review output →
Agent 1: "Now improve by adding..."
→ Review again →
Agent 2: "Refactor Agent 1's code to..."
```

**Key Questions to Explore:**
- How many agents is optimal? (2? 3? 5?)
- Should agents specialize or generalize?
- How to handoff context between agents?
- When to use parallel vs. sequential?
- How to review and integrate agent output?

**3. Demo Time (last few minutes)**
Each director demonstrates their working software. Show what you built!

---

## SUCCESS CRITERIA

### What Makes a Good Demo?

**✅ Bronze: It Works**
- Code runs without errors
- Core functionality demonstrated
- Basic happy path works
- "I could show this to someone"
- **Typical score: 1 point**

**✅ Silver: It's Polished**
- Handles edge cases gracefully
- UI looks intentional (not broken HTML)
- Error messages make sense
- "I'd be comfortable showing this to a customer"
- **Typical score: 2 points**

**✅ Gold: It's Impressive**
- Sophisticated features working smoothly
- Great UX/UI polish
- Handles complex scenarios
- "Wow, you built that in this time?"
- **Typical score: 3 points**

**Remember:** You're evaluated on delivery quality, tech debt, cost efficiency, and collaboration. The goal is learning, but there's friendly competition for the VP promotion!

---

## MULTI-AGENT LEARNING OBJECTIVES

By the end of 4 quarters, directors should be able to:

### Core Skills
1. **Divide & Conquer** - Break large tasks into agent-sized chunks
2. **Prompt Engineering** - Write clear, effective prompts for agents
3. **Context Management** - Handoff work between agents effectively
4. **Parallel Execution** - Run multiple agents simultaneously when appropriate
5. **Sequential Pipelines** - Chain agent outputs as inputs to next agent
6. **Integration** - Combine outputs from multiple agents into coherent system
7. **Review & Iterate** - Evaluate agent work and provide refinement instructions

### Advanced Techniques
8. **Specialist Roles** - Assign agents specific domains vs. generalist approach
9. **Error Recovery** - Handle when agents produce broken code
10. **Incremental Building** - Agent builds on previous agent's work
11. **Testing Strategy** - Use agents to write tests for other agents' code
12. **Refactoring** - Have agents improve each other's code
13. **Documentation** - Agents document their own and others' work

### Metacognition
14. **Know when to use multiple agents** vs. single agent
15. **Recognize agent strengths/weaknesses** - what agents are good/bad at
16. **Cost-benefit analysis** - coordination overhead vs. parallel speed
17. **Human-in-the-loop** - when to review vs. let agents run

---

## ARCHITECTURE: MULTIPLE SERVICES PER DIRECTOR

Each director builds **2-3 microservices** using different agent teams. This teaches service boundaries, agent specialization, and integration.

### Example: Director of Booking Portal

**Service 1 - Search API** (Agent Team A):
- Flight search endpoint
- Filtering and sorting logic
- Mock flight data

**Service 2 - Booking API** (Agent Team B):
- Booking creation
- Payment processing
- Confirmation generation

**Service 3 - Frontend UI** (Agent Team C):
- Search interface
- Booking flow
- Result display

Each service is built by a dedicated agent team (1-3 agents), runs on a different port locally, and can be demoed independently.

### Service Architecture Benefits

1. **Agent specialization:** Different agent teams focus on different services
2. **Parallel development:** Build multiple services simultaneously
3. **Realistic microservices:** Learn service boundaries
4. **Incremental demos:** Show progress service-by-service

### Local Development Setup

All services run on your laptop:
```
Service 1: http://localhost:5001
Service 2: http://localhost:5002
Service 3: http://localhost:3000
```

Use Docker Compose (optional) or just multiple terminal windows.

---

## INTEGRATION OPTIONS (OPTIONAL)

While departments work independently with mock data, optional integration is possible:

### Option 1: Mock Integration (Recommended)
**Best for:** Q1-Q3, keeps things simple

- Use mock/hardcoded data from other departments
- Focus on your own multi-service architecture
- Demo assumes other services exist

Example: Booking Portal calls mock Inventory API
```python
# Mock other department's API
def get_flight_availability(flight_id):
    return {"flight_id": flight_id, "seats_available": 42}
```

### Option 2: Local Network Integration (Advanced)
**Best for:** Q4 "Launch Day" if desired

#### 2a. ngrok/localtunnel (Different Locations)
```bash
# Director A runs booking service
ngrok http 5001
# Shares URL: https://abc123.ngrok.io

# Director B calls it
curl https://abc123.ngrok.io/api/flights
```

**Pros:** Real integration, works remotely
**Cons:** Requires ngrok setup, internet dependent

#### 2b. Shared WiFi (Same Location)
```bash
# Director A's laptop: 192.168.1.100
# Service runs on http://192.168.1.100:5001

# Director B calls it
curl http://192.168.1.100:5001/api/flights
```

**Pros:** True local integration
**Cons:** Same physical location needed

### Shared Data Contracts (Optional)

If integrating, agree on JSON schemas:

**Flight Data:**
```json
{
  "flight_id": "SK123",
  "origin": "SFO",
  "destination": "LAX",
  "departure": "2024-01-15T10:00:00Z",
  "price": 199.99,
  "seats_available": 42
}
```

**Booking Data:**
```json
{
  "booking_id": "B12345",
  "flight_id": "SK123",
  "passenger": {"name": "...", "email": "..."},
  "status": "confirmed"
}
```

### Integration Strategy by Quarter

- **Q1-Q2:** Work independently, mock all external services
- **Q3:** Agree on API contracts, continue with mocks
- **Q4:** Optional real integration for "Launch Day" demo

### Independence Principle

**Each director must be able to demo their services using:**
- Mock data they generate
- Simulated external dependencies
- Standalone operation

**Integration is optional enrichment, not a requirement.** The focus is multi-agent orchestration within your department's 2-3 services.

---

## TECHNOLOGY GUIDELINES

### Recommended Stack (Be Pragmatic)
- **Backend Services:** Python (Flask/FastAPI), Node.js (Express), or anything you know
- **Frontend:** React, Vue, vanilla HTML/CSS/JS, or anything that renders in a browser
- **Database:** SQLite (simple), Postgres, or even JSON files
- **Local Development:** Everything runs on `localhost` on different ports
- **No cloud/hosting:** No deployment, no cloud services, no Kubernetes

### Multi-Service Setup Examples

**Option A: Multiple Python Services**
```bash
# Terminal 1: Search Service
cd search-service && python app.py  # runs on :5001

# Terminal 2: Booking Service
cd booking-service && python app.py  # runs on :5002

# Terminal 3: Frontend
cd frontend && python -m http.server 3000
```

**Option B: Docker Compose (Optional)**
```yaml
services:
  search-api:
    build: ./search-service
    ports: ["5001:5000"]
  booking-api:
    build: ./booking-service
    ports: ["5002:5000"]
  frontend:
    build: ./frontend
    ports: ["3000:3000"]
```

**Option C: Monorepo with Multiple Ports**
All services in one directory, different ports

### What to Build
- **2-3 working services** per director
- **Visual demos** for each service
- **Quality over quantity** - one polished service > three broken ones
- **Local-only** - runs on your laptop

### What Not to Worry About
- ❌ Authentication (assume users are logged in)
- ❌ Deployment (local only, no cloud)
- ❌ Scale (assume 100 users, not 1M)
- ❌ Perfect code (focus on learning agent orchestration)
- ❌ Production infrastructure (no k8s, no load balancers)
- ❌ Cross-machine networking (use mocks or simple solutions)


## EXAMPLE: QUARTER 1 WALKTHROUGH

### Scenario: "Foundation - Build the Core"

**Director of Booking Portal:** "I need a flight search and booking page"

**Multi-Agent Approach:**
```
[Starts 3 Claude conversations]

Agent 1 - Backend:
"Build a simple Flask API with these endpoints:
- GET /flights?origin=X&dest=Y&date=Z (return mock flight data)
- POST /bookings (accept booking, return confirmation)
Use SQLite for storage. Include 5 mock flights in the database."

Agent 2 - Frontend:
"Build an HTML page with:
- Flight search form (origin, destination, date)
- Results display (shows flights with prices)
- Book button (sends POST request)
Use vanilla JavaScript, make it look decent with basic CSS."

Agent 3 - Integration:
"Connect the frontend from Agent 2 to the API from Agent 1.
Add error handling and loading states.
Test the full flow and fix any bugs."
```

**Minutes 3-10:** Agents 1 & 2 work in parallel
**Minutes 10-15:** Review outputs, give refinement prompts
**Minutes 15-20:** Agent 3 integrates and tests
**Minutes 20-25:** Final polish, test the full flow
**Minutes 25-30:** Demo showing working search → results → booking

**Demo:** Opens browser, searches for flights, books one, shows confirmation

**Gamerunner:** "Great! I like how you used three agents in parallel and then integrated. For next quarter, think about seat selection..."


## ADVANCED MULTI-AGENT PATTERNS

As directors get comfortable, they can explore advanced techniques:

### Pattern 1: Agent Specialization
Assign permanent roles to agents across quarters:
- Agent A: Always handles database/backend
- Agent B: Always handles frontend/UI
- Agent C: Always handles testing/quality

**Benefit:** Agents build on prior context
**Cost:** Less flexibility to adapt

### Pattern 2: Meta-Agent
Use one agent to coordinate others:
- Agent 0: "Create a plan to build X, dividing work between 3 agents"
- Agent 0: "Review outputs from Agents 1-3 and identify integration issues"

### Pattern 3: Adversarial Agents
Agents challenge each other:
- Agent 1: Builds feature
- Agent 2: Tries to break it, finds edge cases
- Agent 1: Fixes issues found by Agent 2

### Pattern 4: Iterative Refinement
Build → Review → Improve loop:
- Agent 1: "Build basic version"
- Agent 2: "Review Agent 1's code and suggest 3 improvements"
- Agent 1: "Implement those improvements"

### Pattern 5: Test-Driven
Tests lead implementation:
- Agent 1: "Write comprehensive tests for feature X"
- Agent 2: "Implement feature X to pass those tests"

---

## COMMON PITFALLS & SOLUTIONS

### Pitfall 1: Too Many Agents
**Problem:** 5+ agents, coordination overhead exceeds benefit
**Solution:** Start with 2-3 agents max per quarter

### Pitfall 2: Agents Waiting Idle
**Problem:** Sequential dependencies create bottlenecks
**Solution:** Find more parallel work or reduce agent count

### Pitfall 3: Conflicting Outputs
**Problem:** Agents produce incompatible code
**Solution:** Establish contracts/interfaces upfront, or use meta-agent to coordinate

### Pitfall 4: Copy-Paste Hell
**Problem:** Manually integrating code from 3+ agents is tedious
**Solution:** Have final agent do the integration programmatically

### Pitfall 5: Context Loss
**Problem:** Later agents don't know what earlier agents did
**Solution:** Explicitly pass context: "Here's what Agent 1 built: [paste code]"

### Pitfall 6: Over-Specification
**Problem:** Spending 20 minutes writing perfect prompts
**Solution:** Start simple, iterate based on output


## GETTING STARTED

### Before Game Day
1. **Choose your role** - Review the 8 director roles and pick what excites you
2. **Read your character sheet** - In `characters/` directory
3. **Set up dev environment** - Ensure Claude access and local dev tools ready
4. **Review multi-agent strategies** - Understand the patterns you'll use

### On Game Day
1. **Tutorial (30 min)** - Learn multi-agent basics with live examples
2. **Build! (4 quarters)** - Orchestrate agents to build your department
3. **Demo each quarter** - Show your working software
4. **Compete for VP** - Best metrics get promoted at the end

### Key Mindset
- **Focus:** Multi-agent orchestration, not perfect code
- **Build:** 2-3 services using specialized agent teams
- **Demo:** Working software beats perfect planning
- **Learn:** By doing, experimenting, and sharing techniques
- **Collaborate:** Help the company succeed, compete respectfully

---

## ADDITIONAL RESOURCES

- **Character Sheets:** `characters/` directory - detailed role guides
- **Multi-Service Guide:** `MULTI-SERVICE-GUIDE.md` - architecture patterns
- **Facilitator Guide:** `GAMERUNNER.md` - for workshop organizers

---

*"The best way to learn multi-agent orchestration is to orchestrate multiple agents building something real."*

**Skyward** | Half-day workshop | 4-6 players | Learn multi-agent Claude workflows by building an airline startup
