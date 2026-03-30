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

**Service 1: Status Update API** (Agent Team A)
- Tech: Flask/FastAPI backend
- Port: 5001
- Purpose: Track flight status, position updates, gate changes
- Team: 1-2 backend agents

**Service 2: Flight Tracking Service** (Agent Team B)
- Tech: Flask/FastAPI backend + WebSocket/SSE
- Port: 5002
- Purpose: Real-time position tracking, delay prediction, notifications
- Team: 1-2 backend agents

**Service 3: Airport Status Board Dashboard** (Agent Team C)
- Tech: React/Vue/vanilla JS frontend
- Port: 3000
- Purpose: Status boards, flight maps, operations dashboard
- Team: 1-2 frontend agents

**Why multiple services?**
- ✅ Each agent team has focused responsibility
- ✅ Services can be built in parallel
- ✅ Easy to demo incrementally (Service 1 in Q1, add Service 2 in Q2, etc.)
- ✅ Realistic microservices practice for real-time systems

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
- Status Update API (flight status, gate changes)
- Flight Tracking Service (positions, ETAs)
- Dashboard UI (boards, maps, alerts)

Focus on data freshness and notification speed."
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

### Quarter 5: Survive & Adapt (30 min)
**Focus:** Quick response to market conditions (dice-driven scenario)

**Possible Scenarios:**
- Crisis: "Data feed down - need fallback system!"
- Opportunity: "Airport wants our status API - build integration!"
- Competition: "Competitor has predictive delays - match it!"

**Your Objectives:**
- Respond to gamerunner's dice roll scenario
- Build or fix quickly
- Demonstrate adaptability

**Demo:** Show how you handled the crisis/opportunity.

---

### Quarter 6: Final Challenge (30 min)
**Focus:** One more scenario, final improvements

**Possible Scenarios:**
- Innovation: "Add AI-powered delay prediction"
- Premium: "Build VIP passenger tracking dashboard"
- Scale: "Airport operations center wants your platform"

**Demo:** Final feature showcase and retrospective.

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

**Q5+ (Complex features):** **Specialist Roles** 🎯
- Real-Time Agent: Owns all WebSocket/SSE work across quarters
- Data Agent: Owns all status tracking and analytics work
- UI Agent: Owns all dashboard and visualization work
- **Why:** Context retention, domain expertise in real-time systems
- See TUTORIAL.md "Pattern 3: Specialist Roles" for details

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
"Build flight status system:

Database:
- FlightStatus: flight_id, flight_number, status, scheduled_time, actual_time, gate, terminal
- StatusHistory: status_id, flight_id, old_status, new_status, timestamp, reason

Status values: 'scheduled', 'delayed', 'boarding', 'departed', 'in_air', 'landed', 'arrived', 'cancelled'

API:
- GET /flights (all flights with current status)
- GET /flights/{number} (specific flight details)
- PUT /flights/{id}/status (update status)
- GET /flights/{id}/history (status change timeline)

Generate 50 sample flights with realistic statuses."

Agent 2 (Status Board UI):
"Build departure/arrival board (like at airport):
- Table with columns: Flight, Destination/Origin, Scheduled, Actual, Status, Gate
- Color coding:
  - Green: On time
  - Yellow: Delayed
  - Red: Cancelled
  - Blue: Boarding
- Auto-refresh every 30 seconds
- Sort by departure time

Make it look like real airport displays."

Agent 3 (Flight Map):
"Build live flight map visualization:
- Map showing flight routes (simple lines)
- Plane icons at current positions
- Click plane → show flight details
- Color by status (green on-time, yellow delayed)
- Show origin/destination markers

Use simple map library (Leaflet.js) or just SVG.
Simulate flight positions between origin and destination."
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
"Build flight alert system:

Alert triggers:
- Status changes (delayed, gate change, cancelled)
- Delay > 30 minutes
- Gate change
- Early departure
- Weather warnings for route

Alert channels:
- Email
- SMS
- Push notification
- In-app alert

API:
- POST /alerts/subscribe (flight_number, passenger_id, channels)
- GET /alerts/{passenger_id} (active alerts)
- POST /alerts/send (trigger notification)

Track: alert sent, delivered, opened."

Agent 2 (Delay Predictor):
"Build delay prediction system:

Factors:
- Weather at origin/destination
- Previous flight delays (cascading)
- Aircraft turnaround time
- Time of day (peak vs off-peak)

Calculate delay probability:
- Green: < 10% chance
- Yellow: 10-50% chance
- Red: > 50% chance

Show 'likely delayed' warnings before official delay announced.
API: GET /flights/{id}/delay-prediction"

Agent 3 (Notification UI):
"Build passenger notification center:
- List of all active alerts for user
- Notification history
- Subscription management (which flights to track)
- Alert preferences (email vs SMS)
- Test notification sender

Create notification templates (delay, gate change, cancellation)."
```

---

### Strategy 3: Operations Dashboard (Recommended for Q3)
**When to use:** Airline operations management

```
Agent 1 (Operations Analytics):
"Build flight operations analytics:

Metrics:
- On-time performance (% of flights on time)
- Average delay duration
- Cancellation rate
- Delays by reason (weather, mechanical, crew, etc.)
- Cascading delay tracking (delayed flight affects next flight)

Calculate:
- By route
- By time of day
- By aircraft
- Trend over time

API: GET /analytics/performance"

Agent 2 (Disruption Dashboard):
"Build operations control dashboard:
- Real-time view of all flights
- Highlight delayed/cancelled flights
- Show ripple effects (delay causes 3 downstream delays)
- Weather overlay on map
- Quick actions (send notifications, reassign gates)
- Crisis mode (mass cancellation handling)

Make it look like airline operations center."

Agent 3 (Historical Tracking):
"Build flight history system:
- Complete status timeline for any flight
- On-time performance history by route
- Delay pattern analysis
- Seasonal trends
- Reliability scoring

Visualize:
- Status change timeline
- Delay duration charts
- Reliability heatmap

Store 30 days of historical data for demo."
```

---

### Strategy 4: Real-Time Simulation (Recommended for Q4)
**When to use:** Demonstrating live updates

```
Agent 1 (Flight Simulator):
"Build flight position simulator:
- Simulate flights moving from origin to destination
- Update position every 30 seconds
- Progress: 0% (at gate) → 100% (arrived)
- Include phases: taxi, takeoff, cruise, descent, landing
- Random delays injection (5% chance per flight)

Make it look realistic with simulated speeds and routes.
API: Continuously updates flight positions."

Agent 2 (Live Update Engine):
"Build real-time update system:
- WebSocket or Server-Sent Events for live updates
- Push status changes to all connected clients
- No page refresh needed
- Smooth animations for status transitions
- Show 'LIVE' indicator on dashboard

Make the board update automatically like real airport displays."

Agent 3 (Multi-Flight Tracker):
"Build personal flight tracker:
- User can 'follow' multiple flights
- Dashboard shows all tracked flights
- Side-by-side comparison
- Alerts for any status changes
- Share tracking link with others
- Embed flight status widget

Let users track friends/family flights."
```

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Flight Status & Tracking-Specific Challenges

**"Don't have real flight position data"**
- **Solution:** Tell agent: "Simulate flight positions based on departure time and route duration. Calculate progress percentage and interpolate lat/lon between origin and destination. Update position every 30 seconds."
- Or use integration agent: "Create flight simulator that progresses flights from 0% to 100% with realistic phases: taxi, takeoff, cruise, descent, landing"
- Quick fix: Simple linear interpolation between two points

**"Status board looks terrible / like a basic HTML table"**
- **Solution:** Be specific in prompts: "Style like real airport departure boards - dark background, monospace font, yellow/white text, blinking BOARDING status"
- Show examples: "Look at real FIDS (Flight Information Display System) for reference"
- Dedicate Agent 2 purely to visual polish: "Make this status board look like a professional airport display"

**"Real-time updates don't work / require manual refresh"**
- **Solution:** Start simple with polling: "Use setInterval to fetch status every 30 seconds"
- For advanced: "Implement Server-Sent Events for push updates from backend"
- Use integration agent to bridge: "Connect frontend polling to backend status changes"
- Quick win: "Add auto-refresh every 30 seconds with visual indicator"

**"Map visualization is too complex to build quickly"**
- **Solution:** Add to prompt: "Use Leaflet.js library for simple map with markers and lines"
- Or simplify: "Create SVG-based flight map - just draw lines between origin/destination with plane icon at current position"
- Quick win: "Show flight route as line with progress indicator, no need for real geography"

**"Demo shows static data - not impressive for 'real-time' system"**
- **Solution:** Use simulation agent: "Create background simulator that randomly delays flights, changes gates, and updates positions every 30 seconds during demo"
- Or use refinement agent: "Add demo mode that injects realistic status changes to show live updates"
- Test your demo setup 2 minutes before presenting to ensure updates are visible

**"Can't show accurate ETAs or delay predictions"**
- **Solution:** Tell agent: "Calculate ETA based on current position, remaining distance, and average speed. Add random delay factor for realism."
- Or use data agent: "Build simple delay predictor - if previous flight delayed, next flight 70% likely delayed. Show prediction confidence."
- Quick win: "Show basic ETA calculation - scheduled time plus current delay duration"

---

## TECH STACK SUGGESTIONS

### Option A: Python + JavaScript Frontend (Recommended)
- **Backend:** Flask or FastAPI
- **Frontend:** HTML/CSS/JavaScript
- **Map:** Leaflet.js or simple SVG
- **Real-time:** Simple polling or SSE
- **Database:** SQLite for flight data
- **Why:** Easy to build status APIs and boards

### Option B: Node.js Real-Time Stack
- **Backend:** Express.js with Socket.io
- **Frontend:** React
- **Map:** Leaflet or Mapbox
- **Real-time:** WebSockets via Socket.io
- **Why:** Great for real-time updates

### Option C: Data Visualization Focus
- **Backend:** Any
- **Frontend:** D3.js for visualizations
- **Why:** Beautiful data-driven displays

**Pro tip:** Focus on the status board and map visualization - those are the most impressive and visual parts.

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

### Q5: Survive Competition (30 min)
- Quick response to dice-driven scenario
- Crisis management (data feed down, mass delays)
- **Success = adapted quickly, maintained data accuracy**

### Q6: Final Challenge (30 min)
- One more scenario response
- Final improvements or innovation
- **Success = strong finish, mastered real-time multi-agent systems**

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

### Quarters 3-6: Execute & Adapt

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
