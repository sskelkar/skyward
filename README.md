# Skyward

**A half-day workshop game that teaches backend engineers to orchestrate multiple Claude AI agents by building an airline startup.**

---

## What is Skyward?

Skyward is a collaborative learning workshop where participants become **Directors of Engineering** at a fictional airline startup called SkywardAI. Instead of writing code themselves, directors learn to **manage teams of Claude AI agents** to build working microservices.

Think of it as:
- 🎲 **Dungeons & Dragons** meets **Rome: Total War** meets **multi-agent AI orchestration**
- A hands-on way to develop the "manager mindset" for working with AI agents
- A game where you build real software by delegating to AI teams instead of coding yourself

### Key Learning Objectives

- **Multi-agent orchestration**: Coordinate 2-3 specialized AI agent teams building different services
- **Director mindset**: Shift from "I'll code this" to "Which team should build this?"
- **Strategic planning**: Research and design before building
- **Agent delegation**: Write clear prompts that produce working code
- **System integration**: Connect microservices built by different agent teams

---

## Game Overview

**Format:** Half-day workshop (6-6.5 hours with lunch break)
**Players:** 4-6 backend engineers
**Duration:** 4 quarters across 1 fictional year
**Setting:** Building an airline startup from vision to launch

### Timeline

**Morning (Research & Build):**
- 10:00-10:30 | Tutorial on multi-agent basics
- 10:30-11:30 | **Q1 - Research & Vision** (45-60 min)
- 11:30-12:30 | **Q2 - Investor Demo Build** (45-60 min)
- 12:30-13:00 | Investor Demo presentations
- 13:00-14:00 | Lunch

**Afternoon (Launch Sprint):**
- 14:00-15:00 | **Q3 - Integration & Features** (45-60 min, optional chaos)
- 15:00-16:00 | **Q4 - Launch Sprint** (45-60 min, optional chaos)
- 16:00-16:30 | Performance Review & VP Promotion

### The 8 Director Roles

Each player chooses one department to lead:

1. **Director of Customer Booking Portal** - Build the booking experience
2. **Director of Flight Inventory & Scheduling** - Manage flights and seats
3. **Director of Pricing & Revenue Optimization** - Dynamic pricing and analytics
4. **Director of Personalization & Recommendations** - ML-powered recommendations
5. **Director of Customer Service & Support** - Chatbots and support automation
6. **Director of Marketing & Growth** - Campaigns and growth analytics
7. **Director of Check-in & Boarding** - Check-in flows and boarding passes
8. **Director of Flight Status & Tracking** - Real-time flight tracking

Each director builds **2-3 microservices** using **multiple Claude agent teams**.

**See [players/characters/](players/characters/) directory for detailed role guides.**

---

## Game Structure

### Game Premise

You are directors of engineering at **SkywardAI**, a new airline startup racing to launch in 1 year. Each director runs an independent department and builds systems using a team of Claude agents working together.

**The Learning Goal:** Master multi-agent orchestration - learning to coordinate multiple Claude agents, divide work effectively, and build working software faster than you could alone.

**The Challenge:** Across 4 quarters, demonstrate working software running locally on your laptop. Start with research and vision (Q1), build for investors (Q2), navigate market chaos (Q3), and launch to the world (Q4).

**The Constraint:** Everything runs locally - no cloud deployment, no hosting, just your laptop and Claude agents.

---

### Quarter-by-Quarter Breakdown

#### Q1: Research & Vision (45-60 min)
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
**Scoring:** 0-3 points based on strategy quality, not code

---

#### Q2: Investor Demo Build (45-60 min)
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
**Scoring:** 0-3 points based on technical quality, business value, presentation, innovation (see moderator/GAMERUNNER.md for rubric)

---

#### Q3: Market Challenges (45-60 min)
**Focus:** Building under pressure + optional chaos event

**What Directors Do:**
- Continue building features from Q2 roadmap
- **Optional:** Gamerunner may introduce a crisis/opportunity (see moderator/UNIVERSAL_CHAOS_SCENARIOS.md)
- Adapt and respond while continuing to deliver

**Deliverable:**
- Continued progress on department roadmap
- If chaos occurred: evidence of handling the situation
- Working software ready for Q4 launch prep

**Demo:** Show progress + how you handled any challenges
**Scoring:** 0-3 points based on delivery quality

---

#### Q4: Launch Sprint (45-60 min)
**Focus:** Final polish + launch prep + optional chaos event

**What Directors Do:**
- Complete end-to-end customer/user flows
- Handle edge cases and error states
- Add loading states and user feedback
- Final UX polish and responsiveness
- **Optional:** Gamerunner may introduce a last-minute crisis

**Deliverable:**
- Production-ready system
- Complete customer journey works end-to-end
- Professional appearance worthy of launch day

**Demo:** Full end-to-end flow demonstration
**Milestone:** SkywardAI officially launches! 🚀
**Scoring:** 0-3 points based on delivery quality

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

---

## How Each Quarter Works

### Q1 Turn Structure (Research & Vision)

**1. Introduction (5 min)**
- Gamerunner explains Q1 focus: research and planning, not coding
- Directors ask clarifying questions

**2. Research & Planning with Agents (45-50 min)**
Use agents to research, plan, design, and create vision documents. See [players/TUTORIAL.md](players/TUTORIAL.md) for multi-agent techniques.

**3. Vision Presentation (5 min per director)**
- Present your vision document, wireframes, or MVP
- Explain your strategy for Q2-Q4

---

### Q2-Q4 Turn Structure (Building)

**1. Scenario Introduction (3-5 min)**
The gamerunner announces the quarter's challenge and goals.

**2. Build with Agents (most of the time)**
Orchestrate multiple Claude agents to build your systems. Use parallel work for independent tasks, sequential pipelines when outputs feed into each other, specialist roles for ongoing work, and iterative refinement for quality.

**For detailed multi-agent patterns, see [players/TUTORIAL.md](players/TUTORIAL.md)**

**3. Demo Time (last few minutes)**
Each director demonstrates their working software.

---

## Success Criteria

### What Makes a Good Demo?

**✅ Bronze: It Works (1 point)**
- Code runs without errors
- Core functionality demonstrated
- Basic happy path works

**✅ Silver: It's Polished (2 points)**
- Handles edge cases gracefully
- UI looks intentional
- Error messages make sense

**✅ Gold: It's Impressive (3 points)**
- Sophisticated features working smoothly
- Great UX/UI polish
- Handles complex scenarios

**Remember:** You're evaluated on delivery quality, tech debt, cost efficiency, and collaboration. The goal is learning, but there's friendly competition for the VP promotion!

---

## Architecture & Technology

### Multiple Services Per Director

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

### Recommended Tech Stack

- **Backend Services:** Python (Flask/FastAPI), Node.js (Express), or anything you know
- **Frontend:** React, Vue, vanilla HTML/CSS/JS, or anything that renders in a browser
- **Database:** SQLite (simple), Postgres, or even JSON files
- **Local Development:** Everything runs on `localhost` on different ports
- **No cloud/hosting:** No deployment, no cloud services, no Kubernetes

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

---

### Integration Options (Optional)

Departments work independently with mock data. Real integration is optional.

**Recommended: Mock Integration**
Use mock/hardcoded data from other departments. Focus on your own multi-service architecture.

```python
# Example: Mock another department's API
def get_flight_availability(flight_id):
    return {"flight_id": flight_id, "seats_available": 42}
```

**Optional: Real Integration (Q4)**
For "Launch Day", directors can optionally integrate via ngrok/localtunnel or shared WiFi.

**Independence Principle:** Each director must be able to demo standalone using mock data. Integration is optional enrichment, not required.

---

## Scoring System

Directors are evaluated on:

1. **Delivery Score** (max 12 points)
   - 0-3 points per quarter based on demo quality
   - 0pt: Nothing works
   - 1pt: Partial/struggling
   - 2pts: Solid/working
   - 3pts: Exceptional/polished

2. **Tech Debt Score** (max 15 points)
   - AI reviews code quality
   - Lower debt = higher score

3. **API Cost Efficiency** (max 10 points)
   - Based on Claude API usage
   - Lower cost = higher score

4. **Collaboration Bonus** (max 5 points)
   - Helping other directors
   - Successful integrations

**Total possible: 42 points**

Director with best metrics gets promoted to VP! 🏆

---

## Getting Started

### For Players

1. **Choose your role**: Browse [players/characters/](players/characters/) and pick a director role
2. **Read your character sheet**: Each role has detailed guidance
3. **Learn the basics**: Skim [players/TUTORIAL.md](players/TUTORIAL.md) for multi-agent patterns
4. **Understand director mindset**: Read [players/DIRECTOR-GUIDE.md](players/DIRECTOR-GUIDE.md)
5. **Show up ready**: Bring your laptop with Claude access

### For Facilitators

1. **Read the facilitator guide**: [moderator/GAMERUNNER.md](moderator/GAMERUNNER.md) has everything you need
2. **Review chaos scenarios**: Read [moderator/UNIVERSAL_CHAOS_SCENARIOS.md](moderator/UNIVERSAL_CHAOS_SCENARIOS.md) for optional Q3/Q4 challenges
3. **Prepare materials**: Print scoring sheets, prepare d6 die if using chaos scenarios
4. **Set up the room**: Ensure all players have Claude API access
5. **Run the tutorial**: 30-minute intro to multi-agent basics (10:00-10:30)
6. **Facilitate quarters**: Follow the quarter-by-quarter guide in GAMERUNNER.md
7. **Score and celebrate**: Use rubrics in GAMERUNNER.md for performance review

---

## Repository Structure

```
skyward/
├── README.md                    # This file
├── PITCH.md                     # Why this game exists
├── moderator/                   # Facilitator materials
│   ├── GAMERUNNER.md            # Facilitator guide (scoring, scenarios)
│   └── UNIVERSAL_CHAOS_SCENARIOS.md  # 6 chaos scenarios for Q3/Q4
├── players/                     # Player materials
│   ├── TUTORIAL.md              # Multi-agent orchestration tutorial
│   ├── DIRECTOR-GUIDE.md        # How to think and operate as a director
│   ├── MULTI-SERVICE-GUIDE.md   # Multi-service architecture patterns
│   └── characters/              # Character sheets for all 8 director roles
│       ├── README.md
│       ├── booking-portal.md
│       ├── inventory-scheduling.md
│       ├── pricing-revenue.md
│       ├── recommendations.md
│       ├── customer-service.md
│       ├── marketing-growth.md
│       ├── checkin-boarding.md
│       └── flight-status.md
└── design-notes/                # Historical design documents
```

---

## What Makes This Different?

### Not Just a Coding Exercise

- **You don't write code** - you orchestrate AI agents who write code
- **You manage teams** - each with specialized roles (PM, Backend Dev, Frontend Dev, QA)
- **You make strategic decisions** - what to build, when, and how
- **You deal with constraints** - time pressure, technical debt, API costs

### Progressive Difficulty

- **Q1**: Research and vision (no code pressure)
- **Q2**: Build for investors (polish matters)
- **Q3**: Integration and features (optional chaos scenarios)
- **Q4**: Launch sprint (systems must work, optional chaos)

### Real-World Parallels

- **Multi-service architecture**: Build 2-3 microservices per department
- **Agent specialization**: Backend agents, frontend agents, QA agents, PMs
- **Integration challenges**: Services must talk to each other
- **Technical debt tracking**: AI reviews code quality
- **Performance metrics**: Delivery score, tech debt, API cost efficiency

### Competitive But Collaborative

- **Collaborate**: All directors work toward company success
- **Compete**: Best metrics earn VP promotion
- **No sabotage**: You can't harm other directors
- **Peer learning**: Share techniques and help each other

---

## Key Concepts

### Multi-Agent Orchestration Patterns

The game teaches 4 fundamental patterns:

1. **Parallel Execution** - Multiple agents work simultaneously on independent tasks
2. **Sequential Pipeline** - Agents build on each other's outputs
3. **Specialist Roles** - Agents have permanent domains (Backend, Frontend, QA)
4. **Iterative Refinement** - Agents improve each other's work

All patterns are detailed in [players/TUTORIAL.md](players/TUTORIAL.md).

### Director Responsibilities

As a director, you:
1. **Set the Vision** - Define what success looks like
2. **Delegate to Teams** - Assign work to agent teams
3. **Review & Decide** - Test outputs, ship/revise/scrap decisions
4. **Integrate & Coordinate** - Ensure services work together
5. **Adapt Strategy** - Pivot when things don't work

Learn more in [players/DIRECTOR-GUIDE.md](players/DIRECTOR-GUIDE.md).

### Organizational Roles

Directors can assign agents to roles like:
- **Product Manager** - Define requirements and vision
- **Backend Developer** - Build APIs and services
- **Frontend Developer** - Build UIs
- **QA Engineer** - Test and find bugs
- **Business Analyst** - Analyze requirements
- **DevOps Engineer** - Docker, deployment, automation
- **UX Designer** - Design flows and wireframes
- **Technical Writer** - Documentation

---

## Requirements

### For Participants

- **Claude Access**: API key or Claude.ai Pro subscription
- **Laptop**: Local development environment
- **Tech Stack**: Python/Flask or Node.js/Express recommended
- **Git**: Optional but helpful
- **Docker**: Optional for multi-service management

### Technical Constraints

- **Local only**: All services run on localhost
- **No cloud deployment**: No AWS, GCP, Kubernetes, etc.
- **Mock integrations**: Use mock data or simple localhost API calls
- **2-3 services max**: Keep cognitive load manageable

---

## Philosophy

### Why This Game Exists

Modern software engineering is shifting from "write every line yourself" to "orchestrate AI agents who write code." This game teaches that mindset shift in a safe, fun environment.

### Design Principles

1. **Learning by doing** - You build real software, not toy examples
2. **Safe failure** - It's a game, mistakes are learning opportunities
3. **Progressive complexity** - Start with research, build to crisis management
4. **Realistic constraints** - Time pressure, technical debt, integration challenges
5. **Director mindset** - Manage teams, don't micromanage implementation

### What You'll Learn

- How to break work into agent-sized tasks
- How to write effective prompts for different agent roles
- When to use parallel vs sequential agent workflows
- How to integrate outputs from multiple agents
- How to review AI-generated code effectively
- How to adapt strategy when agents struggle
- How to think like a manager, not just an engineer

---

## Contributing

This is an open-source educational game. Contributions welcome!

### Ideas for Contributions

- **New character roles**: Suggest additional director positions
- **New chaos scenarios**: Additional crisis scenarios for Q3/Q4
- **Alternative settings**: Adapt the game to different industries (e-commerce, fintech, etc.)
- **Translations**: Help make this accessible globally
- **Actual play reports**: Document your gameplay sessions
- **Improvements**: Better rubrics, clearer instructions, new patterns

### How to Contribute

1. Fork this repository
2. Create your feature branch
3. Test your changes (ideally by playing the game!)
4. Submit a pull request with clear description

---

## Credits

**Game Design**: Developed through iterative multi-agent design process (meta!)

**Inspired By**:
- Dungeons & Dragons (narrative and roleplay)
- Rome: Total War (turn-based strategy)
- Real-world engineering management challenges

**Powered By**: [Claude AI](https://www.anthropic.com/claude) by Anthropic

---

## License

MIT License - See LICENSE file for details

---

## Questions?

- **For players**: Read your [character sheet](players/characters/)
- **For facilitators**: See [moderator/GAMERUNNER.md](moderator/GAMERUNNER.md)
- **For learning**: Explore [players/TUTORIAL.md](players/TUTORIAL.md) and [players/DIRECTOR-GUIDE.md](players/DIRECTOR-GUIDE.md)
- **Issues**: Open a GitHub issue for questions or problems

---

**Ready to learn multi-agent orchestration by building an airline? Let's fly.** ✈️
