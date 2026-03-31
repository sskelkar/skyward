# SKYWARD
## A Multi-Agent Coding Workshop Game

**Format:** Collaborative learning workshop
**Participants:** 4-6 backend engineers (playing as directors)
**Duration:** Half day (6-6.5 hours with lunch break, 10am-4pm or 4:30pm)
**Core Goal:** Learn multi-agent orchestration by building an airline startup

---

## DOCUMENTATION GUIDE

- **This File (GAME.md):** Player handbook - game structure, rules, scoring
- **[TUTORIAL.md](TUTORIAL.md):** Multi-agent techniques and patterns
- **[DIRECTOR-GUIDE.md](DIRECTOR-GUIDE.md):** Strategy and tips for each quarter
- **[GAMERUNNER.md](GAMERUNNER.md):** Facilitation guide and scoring rubrics
- **[characters/](characters/):** Detailed role guides for each director

---

## GAME PREMISE

You are directors of engineering at **SkywardAI**, a new airline startup racing to launch in 1 year. Each director runs an independent department and builds systems using a team of Claude agents working together.

**The Learning Goal:** Master multi-agent orchestration - learning to coordinate multiple Claude agents, divide work effectively, and build working software faster than you could alone. Each director builds 2-3 microservices using specialized agent teams.

**The Challenge:** Across 4 quarters, demonstrate working software running locally on your laptop. Start with research and vision (Q1), build for investors (Q2), navigate market chaos (Q3), and launch to the world (Q4).

**The Constraint:** Everything runs locally - no cloud deployment, no hosting, just your laptop and Claude agents.

---

## THE 8 DIRECTOR ROLES

Each role is designed for independent work with minimal dependencies on other departments. Choose based on your interests and comfort level.

**For 4-6 players:** Select the roles that best fit your group. All roles work independently.

**Full character sheets with strategies and examples:** See the `characters/` directory.

---

### 1. Director of Customer Booking Portal
**Mission:** Build the customer-facing flight booking application (search, results, seat selection, confirmation)

### 2. Director of Flight Inventory & Scheduling
**Mission:** Build flight schedule and seat inventory management systems (routes, availability, overbooking logic)

### 3. Director of Pricing & Revenue Optimization
**Mission:** Build dynamic pricing and revenue optimization (demand-based pricing, analytics, competitor monitoring)

### 4. Director of Personalization & Recommendations
**Mission:** Build recommendation and personalization systems (destination suggestions, upselling, user behavior analysis)

### 5. Director of Customer Service & Support
**Mission:** Build customer support systems (chatbot, ticketing, refund workflows, self-service tools)

### 6. Director of Marketing & Growth
**Mission:** Build marketing systems and growth analytics (campaigns, A/B testing, attribution tracking)

### 7. Director of Check-in & Boarding
**Mission:** Build check-in and boarding systems (online check-in, seat maps, boarding passes with QR codes)

### 8. Director of Flight Status & Tracking
**Mission:** Build flight status and real-time tracking (status dashboard, live maps, delay alerts, departure boards)

**See [characters/](characters/) directory for detailed role guides with multi-agent strategies and demo ideas.**

---

## GAME STRUCTURE

### Half-Day Timeline (10am-4pm or 4:30pm)

**Morning: Vision & Building**
- 10:00-10:30 | **Tutorial**: Multi-agent basics and Claude features
- 10:30-11:30 | **Q1 - Research & Vision** (45-60 min): Strategy, research, planning
- 11:30-12:30 | **Q2 - Investor Demo Build** (45-60 min): Build something impressive
- 12:30-13:00 | **Investor Demo**: Present to investors (gamerunner judges)

**Lunch Break**
- 13:00-14:00 | **LUNCH**

**Afternoon: Chaos & Launch**
- 14:00-15:00 | **Q3 - Market Challenges** (45-60 min): Optional chaos event + building
- 15:00-16:00 | **Q4 - Launch Sprint** (45-60 min): Optional chaos event + final launch push
- 16:00-16:30 | **Performance Review**: VP promotion announcement

**Note:** Quarter lengths are flexible (45-60 min). Gamerunner adjusts based on group pace. Chaos events in Q3/Q4 are optional at gamerunner's discretion.

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

**Demo:** Present your vision, explain your strategy for Q2-Q4

**For multi-agent techniques, see [TUTORIAL.md](TUTORIAL.md)**

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

**Demo:** Live demo to "investors" (gamerunner + other directors)
**Scoring:** Gamerunner evaluates using investor demo rubric

**For multi-agent techniques, see [TUTORIAL.md](TUTORIAL.md)**

---

#### Investor Demo & Lunch Break (30 min demo + 60 min lunch)
**What Happens:**
- Each director presents 3-5 minute demo
- Gamerunner (as investor) asks questions
- Investor demo scoring (see GAMERUNNER.md for rubric)
- Break for lunch

---

#### Q3: Market Challenges (45-60 min)
**Focus:** Building under pressure + optional chaos event

**What Directors Do:**
- Continue building features from Q2 roadmap
- **Optional:** Gamerunner may introduce a crisis/opportunity (dice roll or chosen scenario)
- Adapt and respond while continuing to deliver

**If Chaos Event Occurs (Gamerunner's Choice):**
Possible scenarios - Critical Bug, Competitor Attack, Regulatory Audit, Influencer Meltdown, Acqui-hire Raid, Partnership Opportunity (see GAMERUNNER.md for full scenarios)

**Deliverable:**
- Continued progress on department roadmap
- If chaos occurred: evidence of handling the situation
- Working software ready for Q4 launch prep

**Demo:** Show progress + how you handled any challenges

---

#### Q4: Launch Sprint (45-60 min)
**Focus:** Final polish + launch prep + optional chaos event

**What Directors Do:**
- Complete end-to-end customer/user flows
- Handle edge cases and error states
- Add loading states and user feedback
- Final UX polish and responsiveness
- **Optional:** Gamerunner may introduce a last-minute crisis (adds realism!)

**If Chaos Event Occurs (Gamerunner's Choice):**
Last-minute pressure on launch day - could be anything from a critical bug discovered in production, to a competitor announcement, to a key customer demand. Handle it while still launching on time.

**Deliverable:**
- Production-ready system
- Complete customer journey works end-to-end
- Professional appearance worthy of launch day
- Evidence of handling any last-minute fires

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
Use agents to research, plan, design, and create vision documents. See [TUTORIAL.md](TUTORIAL.md) for multi-agent techniques.

**3. Vision Presentation (5 min per director)**
- Present your vision document, wireframes, or MVP
- Explain your strategy for Q2-Q4
- **Scoring (0-3 points):** Q1 is scored based on strategy quality, clarity of vision, and feasibility of plan (not code quality)

---

### Q2-Q4 Turn Structure (Building)

**1. Scenario Introduction (3-5 min)**
The gamerunner announces the quarter's challenge and goals.

**2. Build with Agents (most of the time)**
**This is where building happens!** You orchestrate multiple Claude agents to build your systems. Use parallel work for independent tasks, sequential pipelines when outputs feed into each other, specialist roles for ongoing work, and iterative refinement for quality.

**For detailed multi-agent patterns and techniques, see [TUTORIAL.md](TUTORIAL.md)**

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

## ARCHITECTURE: MULTIPLE SERVICES PER DIRECTOR

Each director builds **2-3 microservices** using different agent teams. This teaches service boundaries, agent specialization, and integration.

**Example:** Director of Booking Portal might build:
- Service 1: Flight Search API (port 5001)
- Service 2: Booking API (port 5002)
- Service 3: Frontend UI (port 3000)

**Benefits:**
- Agent specialization (different agent teams for different services)
- Parallel development (build multiple services simultaneously)
- Realistic microservices practice
- Incremental demos (show progress service-by-service)

All services run locally on your laptop using different ports.

---

## INTEGRATION OPTIONS (OPTIONAL)

Departments work independently with mock data. Real integration is optional.

### Recommended: Mock Integration
Use mock/hardcoded data from other departments. Focus on your own multi-service architecture.

```python
# Example: Mock another department's API
def get_flight_availability(flight_id):
    return {"flight_id": flight_id, "seats_available": 42}
```

### Optional: Real Integration (Q4)
For "Launch Day", directors can optionally integrate via:
- **ngrok/localtunnel** (different locations) - Share temporary URLs
- **Shared WiFi** (same location) - Call each other's localhost services

**Independence Principle:** Each director must be able to demo standalone using mock data. Integration is optional enrichment, not required.

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

---

## GETTING STARTED

### Before Game Day
1. **Choose your role** - Review the 8 director roles and pick what excites you
2. **Read your character sheet** - In `characters/` directory for detailed strategies
3. **Review [TUTORIAL.md](TUTORIAL.md)** - Learn multi-agent orchestration patterns
4. **Set up dev environment** - Ensure Claude access and local dev tools ready

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

- **[TUTORIAL.md](TUTORIAL.md)** - Multi-agent orchestration patterns and techniques
- **[DIRECTOR-GUIDE.md](DIRECTOR-GUIDE.md)** - Strategy guide for each quarter
- **[characters/](characters/)** - Detailed role guides with multi-agent strategies
- **[GAMERUNNER.md](GAMERUNNER.md)** - For workshop facilitators

---

*"The best way to learn multi-agent orchestration is to orchestrate multiple agents building something real."*

**Skyward** | Half-day workshop | 4-6 players | Learn multi-agent Claude workflows by building an airline startup
