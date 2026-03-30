# Terminal Velocity

**A full-day workshop game that teaches backend engineers to orchestrate multiple Claude AI agents by building an airline startup.**

## What is Terminal Velocity?

Terminal Velocity is a collaborative learning workshop where participants become **Directors of Engineering** at a fictional airline startup called SkywardAI. Instead of writing code themselves, directors learn to **manage teams of Claude AI agents** to build working microservices.

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

**Format:** Full-day workshop (7 hours with lunch break)
**Players:** 4-6 backend engineers
**Duration:** 6 quarters across 2 fictional years
**Setting:** Building an airline startup from vision to launch to survival

### Timeline

**Morning (Research & Build):**
- 09:00-09:30 | Tutorial on multi-agent basics
- 09:30-10:30 | **Q1 - Research & Vision** (60 min)
- 10:30-11:30 | **Q2 - Investor Demo Build** (60 min)
- 11:30-12:00 | Investor Demo presentations
- 12:00-13:00 | Lunch

**Afternoon (Launch & Survive):**
- 13:00-14:00 | **Q3 - Integration & Features** (60 min)
- 14:00-15:00 | **Q4 - Launch Sprint** (60 min)
- 15:00-15:30 | **Q5 - Crisis Response** (30 min, dice-driven)
- 15:30-16:00 | **Q6 - Final Challenge** (30 min, dice-driven)
- 16:00-16:30 | Performance Review & VP Promotion

### 8 Director Roles

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

---

## Repository Structure

```
terminal-velocity/
├── README.md                    # This file
├── GAME.md                      # Player-facing game overview
├── GAMERUNNER.md                # Facilitator guide (scoring, scenarios, dice mechanics)
├── TUTORIAL.md                  # Multi-agent orchestration tutorial (13K words)
├── DIRECTOR-GUIDE.md            # How to think and operate as a director (7K words)
├── MULTI-SERVICE-GUIDE.md       # Multi-service architecture patterns
├── characters/                  # Character sheets for all 8 director roles
│   ├── README.md
│   ├── booking-portal.md
│   ├── inventory-scheduling.md
│   ├── pricing-revenue.md
│   ├── recommendations.md
│   ├── customer-service.md
│   ├── marketing-growth.md
│   ├── checkin-boarding.md
│   └── flight-status.md
└── design-notes/                # Historical design documents (not needed for gameplay)
    ├── README.md
    ├── idea.txt
    ├── FEEDBACK_AND_OPTIONS.md
    └── GAME_DESIGN.md
```

---

## Quick Start

### For Players

1. **Read the game overview**: Start with [GAME.md](GAME.md)
2. **Choose your role**: Browse [characters/](characters/) and pick a director role
3. **Read your character sheet**: Each role has detailed guidance
4. **Learn the basics**: Skim [TUTORIAL.md](TUTORIAL.md) for multi-agent patterns
5. **Understand director mindset**: Read [DIRECTOR-GUIDE.md](DIRECTOR-GUIDE.md)
6. **Show up ready**: Bring your laptop with Claude access

### For Facilitators

1. **Read the facilitator guide**: [GAMERUNNER.md](GAMERUNNER.md) has everything you need
2. **Prepare materials**: Print scoring sheets, prepare dice for Q5-Q6
3. **Set up the room**: Ensure all players have Claude API access
4. **Run the tutorial**: 30-minute intro to multi-agent basics (09:00-09:30)
5. **Facilitate quarters**: Follow the turn-by-turn guide in GAMERUNNER.md
6. **Score and celebrate**: Use rubrics in GAMERUNNER.md for performance review

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
- **Q3-Q4**: Integration and launch (systems must work)
- **Q5-Q6**: Crisis response (dice-driven chaos)

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

## Example: Director of Booking Portal in Q1

**Q1 Goal**: Research booking portals and create a vision for your department

**Agent Usage:**
```
Agent 1 (UX Researcher):
"Research 3 successful booking sites (Expedia, Kayak, Airbnb).
Create wireframes for our booking flow: Search → Results → Booking → Confirmation"

Agent 2 (Technical Architect):
"Design a 3-service architecture for booking:
- Search API
- Booking API
- Frontend UI
Specify tech stack, ports, and data contracts."

Agent 3 (Product Manager):
"Create product vision document with:
- User stories
- Feature prioritization for Q2-Q4
- Success metrics"
```

**Deliverable**: Vision document with wireframes and architecture plan (no working code needed in Q1!)

---

## Key Concepts

### Multi-Agent Orchestration Patterns

The game teaches 4 fundamental patterns:

1. **Parallel Execution** - Multiple agents work simultaneously on independent tasks
2. **Sequential Pipeline** - Agents build on each other's outputs
3. **Specialist Roles** - Agents have permanent domains (Backend, Frontend, QA)
4. **Iterative Refinement** - Agents improve each other's work

All patterns are detailed in [TUTORIAL.md](TUTORIAL.md).

### Director Responsibilities

As a director, you:
1. **Set the Vision** - Define what success looks like
2. **Delegate to Teams** - Assign work to agent teams
3. **Review & Decide** - Test outputs, ship/revise/scrap decisions
4. **Integrate & Coordinate** - Ensure services work together
5. **Adapt Strategy** - Pivot when things don't work

Learn more in [DIRECTOR-GUIDE.md](DIRECTOR-GUIDE.md).

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

## Scoring System

Directors are evaluated on:

1. **Delivery Score** (max 18 points)
   - 1-3 points per quarter based on demo quality
   - Bronze (1pt): Works
   - Silver (2pts): Polished
   - Gold (3pts): Impressive

2. **Tech Debt Score** (max 15 points)
   - AI reviews code quality
   - Lower debt = higher score

3. **API Cost Efficiency** (max 10 points)
   - Based on Claude API usage
   - Lower cost = higher score

4. **Collaboration Bonus** (max 5 points)
   - Helping other directors
   - Successful integrations

**Total possible: 48 points**

Director with best metrics gets promoted to VP! 🏆

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
- **New scenarios**: Q5-Q6 crisis scenarios for the dice table
- **Alternative settings**: Adapt the game to different industries
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

- **For players**: Read [GAME.md](GAME.md) and your [character sheet](characters/)
- **For facilitators**: See [GAMERUNNER.md](GAMERUNNER.md)
- **For learning**: Explore [TUTORIAL.md](TUTORIAL.md) and [DIRECTOR-GUIDE.md](DIRECTOR-GUIDE.md)
- **Issues**: Open a GitHub issue for questions or problems

---

**Ready to learn multi-agent orchestration by building an airline? Let's fly.** ✈️
