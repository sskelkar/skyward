# Player Materials

This folder contains everything you need to participate in Skyward as a director.

## Core Guides

### `TUTORIAL.md`
**Multi-agent orchestration tutorial** (49KB) - Learn how to coordinate multiple Claude agents:

**Core concepts:**
- What is an agent?
- Agent coordination patterns (parallel, sequential, specialist, iterative)
- How to spawn agents in Claude Code CLI

**The four fundamental patterns:**
1. **Parallel Execution** - Multiple agents work simultaneously
2. **Sequential Pipeline** - Agents build on each other's outputs
3. **Specialist Roles** - Agents with permanent domains
4. **Iterative Refinement** - Agents improve each other's work

**Practical sections:**
- Detailed examples (flight search, booking flow, quality polish)
- Prompt engineering templates
- Context management strategies
- Common pitfalls and solutions
- Debugging agent outputs
- Advanced techniques (background agents, adversarial agents, specialist reviews)
- Quick reference cheat sheets

**Start here** if you're new to multi-agent orchestration.

---

### `DIRECTOR-GUIDE.md`
**Strategy guide for directors** (22KB) - How to think and operate as a director:

**Director mindset:**
- From implementer to orchestrator
- Strategic thinking over tactical execution
- Delegation and trust

**Quarter-by-quarter strategy:**
- Q1: Research & Vision (plan without code)
- Q2: Investor Demo (build to impress)
- Q3: Integration & Features (handle chaos)
- Q4: Launch Sprint (ship it)

**Building multi-service architecture:**
- Service boundaries and responsibilities
- Agent team organization
- Integration strategies

**Maximizing your score:**
- Delivery score optimization
- Tech debt management
- API cost efficiency
- Collaboration opportunities

**Read this** to understand the director role and quarter strategies.

---

### `MULTI-SERVICE-GUIDE.md`
**Multi-service architecture patterns** (10KB) - Practical guide to building 2-3 microservices:

**Topics:**
- Why multiple services?
- Common architecture patterns per role
- Service communication strategies
- Port management
- Running services locally (terminals, Docker Compose, etc.)
- Mock data strategies
- Integration approaches

**Use this** when planning your department's architecture.

---

## Character Sheets

### `characters/` directory
**8 detailed director role guides** - One for each department:

1. **booking-portal.md** - Customer booking experience
2. **inventory-scheduling.md** - Flight schedules and seat inventory
3. **pricing-revenue.md** - Dynamic pricing and revenue optimization
4. **recommendations.md** - Personalization and recommendations
5. **customer-service.md** - Support chatbots and ticketing
6. **marketing-growth.md** - Campaigns and growth analytics
7. **checkin-boarding.md** - Check-in flows and boarding passes
8. **flight-status.md** - Real-time flight tracking

**Each character sheet includes:**
- Your role and mission
- Your north star (goals and motivations)
- Department architecture (2-3 service recommendations)
- Quarter-by-quarter goals
- Multi-agent strategy examples
- Visual demo ideas
- Role-specific challenges and solutions
- Integration points with other departments

**Choose your role**, then read your character sheet for detailed guidance.

---

## Quick Start

### Before Game Day

1. **Read the overview**: Start with `../README.md` for game structure and rules
2. **Choose your role**: Browse `characters/` and pick a director position
3. **Read your character sheet**: Get familiar with your department
4. **Skim TUTORIAL.md**: Learn multi-agent patterns (focus on the 4 fundamental patterns)
5. **Skim DIRECTOR-GUIDE.md**: Understand the director mindset

### On Game Day

1. **Tutorial session** (30 min) - Hands-on multi-agent basics
2. **Q1: Research & Vision** - Plan your architecture with agents
3. **Q2: Investor Demo** - Build something impressive
4. **Lunch break** - Recharge
5. **Q3: Integration** - Continue building, handle any chaos
6. **Q4: Launch Sprint** - Final polish and ship it
7. **Performance Review** - See who becomes VP!

### Key Resources During Gameplay

- **Quick help**: TUTORIAL.md "Quick Reference" section
- **Prompt templates**: TUTORIAL.md "Prompt Engineering" section
- **Debugging**: TUTORIAL.md "Debugging Agent Outputs" section
- **Quarter strategy**: DIRECTOR-GUIDE.md quarter-specific sections
- **Your role**: Your character sheet in `characters/`

---

**Ready to become a director? Pick your character sheet and start building!**
