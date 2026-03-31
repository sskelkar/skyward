# DIRECTOR OF FLIGHT STATUS & TRACKING
## Character Sheet

---

## YOUR ROLE

You are the **Director of Flight Status & Tracking** at SkywardAI - the information hub that keeps everyone informed about every flight, every minute.

**Department:** Operations - Real-Time Systems
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Flight Operations

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Every passenger, agent, and system should have real-time, accurate flight information."**

You manage the single source of truth for flight status. Is the flight on time? Delayed? Cancelled? Gate changed? Your systems provide this critical information to passengers, airport staff, and other departments. When people ask "Where's my flight?", your systems answer.

### What Drives You
- **Accuracy:** Status information must be 100% correct - no room for stale data
- **Real-time:** Updates propagate within seconds, not minutes
- **Visibility:** Easy access to status from anywhere - web, mobile, airport displays
- **Proactive:** Notify passengers before they have to ask or check

### What Keeps You Up at Night
- Outdated status information causing passengers to miss flights
- Delay notifications arriving after the flight already left
- Passengers showing up at the wrong gate due to incorrect updates
- Different systems showing conflicting status information
- Real-time data feeds going down during peak operations

---

## CHARACTER FLAVOR

You're the **real-time information master** - you obsess over data freshness and accuracy. While other directors worry about features and polish, you worry about whether that status update is 5 seconds old or 50 seconds old.

**Your mantras:**
- "Stale information is worse than no information"
- "Every second counts when flights are delayed"
- "The map is not the territory, but it better be accurate"
- "Proactive notification beats reactive inquiry"

**In board meetings, you say:**
- "Average status update latency: 12 seconds"
- "On-time performance: 87.3%"
- "Delay notifications sent 23 minutes before departure on average"
- "Zero instances of conflicting status information"

**Your personality:**
- Precise, real-time focused, data-driven
- Love live dashboards and constantly refreshing displays
- Frustrated by delayed information and manual updates
- The person who refreshes FlightRadar24 constantly

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Status Tracking System**
- **Purpose:** Track real-time flight status, delays, gate changes, and cancellations
- **Key Decisions:**
  - How frequently should status updates be pulled/pushed?
  - What status values do we track (scheduled, delayed, boarding, departed, etc.)?
  - How do we handle cascading delays (one delayed flight affects the next)?
- **Integration:** Consumes flight schedule data, provides status to passengers and other departments
- **Team:** 1-2 agents

**Service 2: Real-Time Update & Notification System**
- **Purpose:** Push live updates to passengers and systems, trigger proactive alerts
- **Key Decisions:**
  - When should we notify passengers (delay threshold, gate changes, etc.)?
  - How do we ensure updates propagate within seconds, not minutes?
  - What notification channels do we support (SMS, email, push, in-app)?
- **Integration:** Monitors status changes, sends alerts to passenger-facing systems
- **Team:** 1-2 agents

**Service 3: Operations Dashboard & Visualization**
- **Purpose:** Display status boards, flight maps, and operational analytics
- **Key Decisions:**
  - What information is most critical for airport staff vs passengers?
  - How do we visualize flight positions and routes?
  - What metrics matter for operations (on-time %, delay trends, etc.)?
- **Integration:** Displays data from tracking and notification services
- **Team:** 1-2 agents

**Why multiple services?**
- ✅ Each agent team has focused responsibility
- ✅ Services can be built in parallel
- ✅ Easy to demo incrementally (Service 1 in Q1, add Service 2 in Q2, etc.)
- ✅ Realistic microservices practice for real-time systems

**Tech decisions are yours to make in Q1 with your agent teams.**

📚 **For detailed multi-service patterns:** See [MULTI-SERVICE-GUIDE.md](../MULTI-SERVICE-GUIDE.md)

---

## WHAT YOU'LL BUILD

### Quarter 1: Research & Vision (45-60 min)
**Focus:** Strategy, research, and planning - NOT working code yet

**Your Objectives:**
- Research how real-time flight tracking systems work (analyze FlightRadar24, FlightAware)
- Analyze real-time data feed architectures and update strategies
- Design notification strategies for proactive passenger alerts
- Plan your 2-3 service architecture (Status API, Tracking Service, Dashboard)

**Deliverable Options:**
- Vision document with system architecture and data flow diagrams
- Wireframes of status boards and flight maps
- Simple MVP (if time permits) - basic prototype

**Agent Roles to Use:**
- **Business Analyst:** Research flight status workflows and notification patterns
- **UX Designer:** Create status board designs and map visualizations
- **Technical Architect:** Design real-time data architecture
- **Data Analyst:** Plan delay prediction and analytics approach

**Example Prompt:**
```
"You are a technical architect researching real-time flight tracking systems.

Analyze how FlightRadar24 and FlightAware handle:
1. Real-time position updates
2. Status change notifications
3. Delay prediction
4. Airport status boards

Design our architecture for:
- Status Tracking System (what status data we track, how we handle updates)
- Real-Time Update & Notification System (when/how we alert passengers)
- Operations Dashboard (what we visualize, what metrics we track)

Focus on data freshness and notification speed. Recommend tech approaches but
let the team decide final stack in implementation."
```

**Demo:** Present your vision doc, wireframes, or MVP. Explain your strategy for real-time updates and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable status tracking system (happy path)
- Make it look like a professional flight operations center
- Focus on visual impact: live boards and maps

**Deliverable:**
- Working status lookup and board display (mock data is fine)
- Working flight map with positions OR
- Impressive dashboard that looks production-ready

**Agent Roles to Use:**
- **Backend Developer:** Build status/tracking APIs
- **Frontend Developer:** Build polished status boards and maps
- **QA Engineer:** Test the demo flow

**Example Focus:**
```
Priority 1: Make it look amazing (airport status board + map)
Priority 2: Core flow works (lookup flight → see status → see position)
Priority 3: Handle edge cases (defer if time-limited)
```

**Demo:** Live demo of status tracking to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add delay notifications or predictive alerts
- Improve real-time update mechanisms (WebSockets/SSE)
- Optional: Integrate with other directors' APIs (inventory for schedules, check-in for boarding)
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced tracking system with 2-3 new features
- More sophisticated status update logic
- Better real-time capabilities

**Gamerunner May Introduce:**
- "Major weather delay - 50 flights affected!"
- "Airport changed all gates - update passengers!"
- "Passengers complaining about late notifications!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end status tracking flow
- Handle all status types and edge cases
- Real-time updates without manual refresh
- Professional operations dashboard
- Map visualization with live positions

**Deliverable:**
- Production-ready flight status platform
- Complete tracking journey works smoothly
- Professional appearance worthy of airline operations center

**Demo:** Full status tracking from lookup to live updates to notifications. Company launches! 🎉

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Can look up flight status
- Shows on-time/delayed/cancelled
- Basic departure/arrival board
- Status updates manually

**Silver Tier:**
- Live flight map with positions
- Automatic status updates
- Clean status board UI
- Professional dashboard

**Gold Tier:**
- Real-time tracking with animations
- Predictive delay warnings
- Beautiful visualizations
- "This looks like FlightRadar24"

**Demo Script (30 seconds):**
1. Show airport status board (all departures)
2. Look up specific flight → show details
3. Display flight map with current position
4. Simulate delay → show notification triggered
5. Show operations dashboard (delays, cancellations)
6. Explain multi-agent strategy

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Flight Status & Tracking

**Q1-Q2 (Foundation building):** **Parallel Execution** ⚡
- Agent 1: Status Backend API (status tracking, updates)
- Agent 2: Tracking Service (positions, notifications)
- Agent 3: Dashboard UI (boards, maps)
- **Why:** Fastest way to get working end-to-end tracking system
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Polish & features):** **Iterative Refinement** ✨
- Agent 1: Add new feature (delay prediction, weather integration)
- Agent 2: Review and improve real-time performance
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples


### Role-Specific Tips

**Keep real-time separate from data agents:**
Real-time update mechanisms (WebSockets, SSE) are complex. One agent focuses on push updates while another handles the data layer.

**Use visualization libraries early:**
Prompt agents with "Use Leaflet.js for maps" or "Make status board look like airport displays" rather than building from scratch. Saves time, looks better.

**Demo-first thinking:**
Structure your agents around what you'll show: "Agent 1 builds the data I'll query, Agent 2 builds the map I'll point at, Agent 3 builds the updates that happen live."

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (flight tracking systems)
- "Quick Reference" (cheat sheets)

---

## MULTI-AGENT STRATEGY EXAMPLES

### Strategy 1: Status Engine + Board + Map (Recommended for Q1)
**When to use:** Building complete status system

```
Agent 1 (Status Backend):
"Build flight status tracking system:

WHAT to track:
- Flight status (scheduled, delayed, boarding, departed, in_air, landed, cancelled)
- Scheduled vs actual times
- Gate and terminal assignments
- Status change history

KEY DECISIONS for you to make:
- What status values do we need?
- How do we model status transitions?
- What data do we store in history?
- How do we handle time zones?

Build APIs that let us:
- Query current status for all flights
- Look up specific flight details
- Update status when things change
- View status history timeline

Generate realistic sample data for demo."

Agent 2 (Status Board UI):
"Build departure/arrival board display:

WHAT it shows:
- Flight number, destination/origin, times, status, gate
- Real-time updates without page refresh
- Clear visual status indicators
- Sorted by departure time

KEY DECISIONS for you to make:
- How should we visualize different statuses (colors, icons, etc.)?
- What refresh strategy works best (polling, websockets, etc.)?
- What information is most critical to surface?

Make it look like professional airport displays."

Agent 3 (Flight Map):
"Build live flight tracking visualization:

WHAT it shows:
- Flight routes and current positions
- Visual status indicators
- Interactive flight details
- Origin and destination markers

KEY DECISIONS for you to make:
- How do we visualize flight positions (choose a mapping approach)?
- How do we calculate/simulate positions between origin and destination?
- What level of detail is needed for demo vs production?

Create something visually impressive for demos."
```

**Timeline:**
- Min 0-12: Agent 1 builds status backend
- Min 12-20: Agent 2 builds status board
- Min 20-25: Agent 3 creates flight map

---

### Strategy 2: Alerts & Notifications (Recommended for Q2)
**When to use:** Proactive passenger communication

```
Agent 1 (Alert Engine):
"Build proactive flight alert system:

WHAT triggers alerts:
- Status changes (delayed, gate change, cancelled)
- Significant delays
- Early departures
- Gate reassignments

KEY DECISIONS for you to make:
- When exactly should we notify? (delay threshold, timing, frequency)
- What notification channels do we support?
- How do we prevent notification spam?
- How do we track notification delivery and engagement?

Build system that lets passengers subscribe to flights and receive timely alerts."

Agent 2 (Delay Predictor):
"Build delay prediction and early warning system:

WHAT it predicts:
- Likelihood of delays before they're officially announced
- Cascading delay effects (one delayed flight impacts others)
- Risk factors affecting on-time performance

KEY DECISIONS for you to make:
- What factors should we consider (weather, previous delays, turnaround time)?
- How do we calculate and display probability/confidence?
- When should we show predictions vs confirmed delays?
- How accurate do predictions need to be to be useful?

Create proactive warnings that help passengers plan ahead."

Agent 3 (Notification UI):
"Build passenger notification management interface:

WHAT it manages:
- Active alerts and notification history
- Flight subscriptions and tracking
- Notification preferences and channels
- Alert testing and preview

KEY DECISIONS for you to make:
- How should passengers control what they're notified about?
- How do we display notification templates and previews?
- What notification settings are most important?

Make it easy for passengers to stay informed without being overwhelmed."
```

---

### Strategy 3: Operations Dashboard (Recommended for Q3)
**When to use:** Airline operations management

```
Agent 1 (Operations Analytics):
"Build flight operations analytics and metrics:

WHAT to measure:
- On-time performance and reliability
- Delay patterns and trends
- Cancellation rates and reasons
- Cascading delay impacts

KEY DECISIONS for you to make:
- What metrics matter most for operations?
- How do we categorize and track delay causes?
- How do we identify and track cascading delays?
- What time periods and comparisons are meaningful?

Build analytics that help operations teams understand and improve performance."

Agent 2 (Disruption Dashboard):
"Build operations control center interface:

WHAT it displays:
- Real-time flight status overview
- Disruptions and their ripple effects
- Crisis situations requiring intervention
- Quick action capabilities

KEY DECISIONS for you to make:
- How do we visualize disruptions and their downstream impacts?
- What information is most critical during crisis situations?
- What quick actions should operators be able to take?
- How do we prioritize and surface the most urgent issues?

Make it look and feel like a professional airline operations center."

Agent 3 (Historical Tracking):
"Build flight history and trend analysis:

WHAT it tracks:
- Complete status timeline for flights
- Historical on-time performance
- Delay patterns and seasonality
- Route and aircraft reliability

KEY DECISIONS for you to make:
- How much history should we store and display?
- How do we visualize trends and patterns?
- What comparisons are most valuable?
- How do we calculate and display reliability scores?

Create insights that help predict and prevent future delays."
```

---

### Strategy 4: Real-Time Simulation (Recommended for Q4)
**When to use:** Demonstrating live updates

```
Agent 1 (Flight Simulator):
"Build realistic flight simulation for demos:

WHAT it simulates:
- Flight progression from origin to destination
- Position updates and flight phases
- Realistic delays and disruptions
- Status changes throughout journey

KEY DECISIONS for you to make:
- How frequently should positions update?
- How do we make simulated flight paths look realistic?
- What flight phases should we model (taxi, cruise, landing, etc.)?
- How often should we inject delays for demo realism?

Create a convincing simulation that makes demos look live and dynamic."

Agent 2 (Live Update Engine):
"Build real-time update delivery system:

WHAT it delivers:
- Instant status updates to all connected clients
- Automatic refresh without user action
- Smooth visual transitions
- Live indicators and animations

KEY DECISIONS for you to make:
- What's the best approach for pushing updates (websockets, polling, SSE)?
- How do we ensure updates propagate within seconds?
- How do we handle visual transitions smoothly?
- What feedback tells users they're seeing live data?

Make the system feel truly real-time like professional airport displays."

Agent 3 (Multi-Flight Tracker):
"Build personal flight tracking and sharing:

WHAT it enables:
- Tracking multiple flights simultaneously
- Comparing flight statuses side-by-side
- Sharing tracking with others
- Embedded status widgets

KEY DECISIONS for you to make:
- How should users manage their tracked flights?
- What's the best way to display multiple flights?
- How do we enable sharing and embedding?
- What alerts matter for personal flight tracking?

Let passengers easily track and share flight status with friends and family."
```

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Flight Status & Tracking-Specific Challenges

**"Don't have real flight position data"**
- **Solution:** Work with your agents to design a simulation approach. Key decision: How do you model flight progression realistically? Consider phases (taxi, cruise, landing) and update frequencies.
- Director mindset: "We need simulated positions that look real for demos - what approaches should we explore?"

**"Status board looks terrible / like a basic HTML table"**
- **Solution:** Set clear expectations for visual quality. Reference real systems (FIDS displays at airports).
- Director mindset: "The status board needs to look professional - research real airport displays and make design decisions about layout, colors, and information hierarchy."

**"Real-time updates don't work / require manual refresh"**
- **Solution:** This is a key architectural decision. Have your agents research and recommend update strategies (polling, websockets, SSE) with tradeoffs.
- Director mindset: "Updates must happen automatically - research approaches and decide what works best for our use case."

**"Map visualization is too complex to build quickly"**
- **Solution:** Scope appropriately. Decide what level of sophistication you need for your demo vs production goals.
- Director mindset: "We need flight visualization - research options and recommend an approach that balances visual impact with implementation time."

**"Demo shows static data - not impressive for 'real-time' system"**
- **Solution:** Plan for simulation as a deliberate feature. Real-time systems need dynamic data for compelling demos.
- Director mindset: "Our demos must show live updates - design a simulation system that makes our real-time capabilities visible."

**"Can't show accurate ETAs or delay predictions"**
- **Solution:** This is a product decision. Define what accuracy means for your system and what factors to consider.
- Director mindset: "What prediction capabilities are valuable vs realistic to build? Research approaches and decide on scope."

---

## TECH CONSIDERATIONS

**You'll decide tech stack with your agent teams in Q1.** Here are some considerations:

### Key Technical Decisions to Make

**Real-Time Update Strategy:**
- How will you push updates to clients? (polling, websockets, server-sent events)
- What update frequency balances freshness with performance?
- How do you handle many concurrent connections?

**Data Storage:**
- What data needs to be persisted vs in-memory?
- How do you store and query status history?
- How do you handle time zones and timestamps?

**Visualization Approach:**
- How will you render maps and flight positions?
- What libraries or approaches work best for status boards?
- How do you create smooth, live-updating displays?

**Integration Strategy:**
- How do services communicate with each other?
- What data formats work best (JSON, Protocol Buffers, etc.)?
- How do you handle service failures gracefully?

**Your agent teams will research options and recommend approaches based on your requirements.**

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research real-time flight tracking systems
- Analyze data feed architectures and notification strategies
- Design your service architecture
- Create vision doc with status board and map wireframes
- **Success = clear strategy and plan for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on visual impact (status boards look like airports)
- Core tracking flow works
- **Success = impressive demo that shows real-time capabilities**

### Q3: Integration & Features (60 min)
- Add 2-3 significant features (notifications, predictions)
- Implement proper real-time updates
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system with better real-time capabilities**

### Q4: Launch Ready (60 min)
- Complete end-to-end tracking flow
- All status types handled
- Auto-updating displays without refresh
- Professional operations dashboard
- **Success = production-ready tracking platform, ready to launch!**

---

## INTEGRATION POINTS (OPTIONAL)

Work independently with mock flight data, or integrate:

### With Inventory
- Get flight schedule data
- Update with actual times

### With Check-in
- Provide status for boarding
- Gate change alerts

### With Customer Service
- Status for support queries
- Delay compensation triggers

**Mock it:** Generate realistic flight schedules and simulate status changes. You don't need real integration.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Status board looks like real airport display
- ✅ Flight map shows positions visually
- ✅ Alerts trigger on status changes
- ✅ Updates happen automatically (no manual refresh)
- ✅ Dashboard is information-rich and real-time
- ✅ Multi-agent strategy is clear and effective
- ✅ You improve and add features each quarter
- ✅ Real-time updates are visible during demos

### Red Flags to Avoid
- ❌ Status updates require manual page refresh
- ❌ Board looks like generic HTML table from 1998
- ❌ No visual flight tracking or map
- ❌ Can't demonstrate real-time updates during demo
- ❌ Status information is static and stale
- ❌ Demos that require "imagine this updates live"
- ❌ Same demo every quarter with no evolution

---

## QUICK START GUIDE

### Before Game Day
- Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) - Learn to think like a director
- Read [TUTORIAL.md](../TUTORIAL.md) - Multi-agent patterns
- Bookmark TUTORIAL.md "Quick Reference" for prompt templates

### Quarter 1: Research & Vision (60 min)

**First 10 minutes:**
1. Decide: What will I deliver? (Vision doc? Wireframes? MVP?)
2. Plan your agent strategy: Which agents for which tasks?
3. Start Agent 1 (Researcher or Technical Architect): Begin research on real-time systems

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research flight tracking systems and real-time data architectures
- Agent 2: Design status board and map visualizations
- Agent 3: Plan notification strategies and delay prediction

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision
2. Decide which 1-2 services to build (Status API + Dashboard recommended)
3. Start Agent 1 (Backend): Build status tracking service

**Minutes 5-50:**
Build your investor demo:
- Agents build services based on Q1 architecture
- Focus on visual impact (status boards, maps)
- Test real-time updates as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to show live status updates

### Quarter 3 & Beyond: Execute & Adapt

**Each quarter:**
1. Listen to gamerunner scenario
2. Decide: What agents do I need?
3. Build/fix quickly with focus on real-time capabilities
4. Demo at end

**Between quarters:**
- Reflect: What worked? What didn't?
- Review TUTORIAL.md for new techniques
- Plan: How will I improve real-time performance next quarter?

---

## PARTING WISDOM

> "You have 30 minutes to build what normally takes 3 hours. Your secret weapon is coordinating 2-3 agents efficiently. The agent that builds the status API doesn't have to be the agent that makes it update in real-time. The agent that creates the map doesn't have to be the agent that polishes the dashboard. Assembly line beats single artisan - especially for real-time systems."

Good luck, Director. Every passenger checking "Where's my flight?" depends on you. Make the answer instant, accurate, and beautiful. 🛫📍
