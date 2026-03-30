# DIRECTOR OF FLIGHT INVENTORY & SCHEDULING
## Character Sheet

---

## YOUR ROLE

You are the **Director of Flight Inventory & Scheduling** at SkywardAI - the operational backbone that makes every flight possible.

**Department:** Operations - Backend Systems
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Operations

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Never sell a seat twice. Never fly an empty plane."**

You are the master of inventory accuracy and optimization. Every seat on every flight must be tracked perfectly. No double-bookings, no overselling (beyond calculated overbooking), no confused passengers.

### What Drives You
- **Accuracy:** Perfect inventory tracking, zero reconciliation errors
- **Optimization:** Maximize load factor (seats filled per flight)
- **Reliability:** Systems that never lose data, never contradict themselves
- **Efficiency:** Fast lookups, real-time updates, scalable architecture

### What Keeps You Up at Night
- Double-booked seats causing airport chaos
- Inventory sync issues between systems
- Overbooking calculations gone wrong
- Performance degradation on busy routes

---

## CHARACTER FLAVOR

You're the **engineer's engineer** - you love data structures, algorithms, and systems that work perfectly at scale.

**Your mantras:**
- "Trust the data, verify the data"
- "A seat is either booked or it isn't - no ambiguity"
- "Optimize for correctness first, speed second"
- "Inventory is the source of truth"

**In board meetings, you say:**
- "Load factor across all routes: 87.3%"
- "Zero inventory discrepancies this quarter"
- "Average booking API response time: 42ms"
- "Overbooking optimizations added $2.1M revenue"

**Your personality:**
- Precise, methodical, data-driven
- Proud of system reliability
- Slightly obsessive about edge cases
- The person who says "actually, we need transactions here"

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Flight Schedule API** (Agent Team A)
- Tech: Flask/FastAPI backend
- Port: 5001
- Purpose: Flight schedule management, route data
- Team: 1-2 backend agents

**Service 2: Seat Inventory API** (Agent Team B)
- Tech: Flask/FastAPI backend
- Port: 5002
- Purpose: Real-time seat tracking, booking operations
- Team: 1-2 backend agents

**Service 3: Admin Dashboard** (Agent Team C)
- Tech: React/Vue/vanilla JS frontend
- Port: 3000
- Purpose: Inventory visualization, analytics, operations console
- Team: 1-2 frontend agents

**Why multiple services?**
- ✅ Each agent team has focused responsibility
- ✅ Services can be built in parallel
- ✅ Easy to demo incrementally (Service 1 in Q1, add Service 2 in Q2, etc.)
- ✅ Realistic microservices practice

📚 **For detailed multi-service patterns:** See [MULTI-SERVICE-GUIDE.md](../MULTI-SERVICE-GUIDE.md)

---

## WHAT YOU'LL BUILD

### Quarter 1: Research & Vision (45-60 min)
**Focus:** Strategy, research, and planning - NOT working code yet

**Your Objectives:**
- Research airline inventory systems and best practices (use agents to analyze approaches)
- Define your 2-3 service architecture (Schedule API, Inventory API, Admin Dashboard)
- Create vision document with data models and system architecture
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with database schema and architecture diagram
- Data flow diagrams showing inventory operations
- Simple MVP (if time permits) - basic prototype

**Agent Roles to Use:**
- **Business Analyst:** Research inventory management systems
- **Database Architect:** Design schema for flights, seats, bookings
- **Technical Architect:** Design service architecture and API contracts
- **Operations Analyst:** Define overbooking rules and inventory logic

**Example Prompt:**
```
"You are a database architect designing an airline inventory system.

Design a relational schema that handles:
- Flights (routes, times, aircraft assignments)
- Aircraft (models, seat configurations)
- Seat inventory (available, booked, blocked)
- Bookings (reservations, status tracking)

Include proper foreign keys and indexes.
Focus on preventing double-bookings and ensuring data integrity."
```

**Demo:** Present your vision doc, schema diagrams, or MVP. Explain your strategy and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable inventory tracking system (happy path)
- Show real-time seat availability updates
- Focus on what investors want to see: operational excellence

**Deliverable:**
- Working flight schedule API (mock data is fine)
- Working seat inventory tracking with bookings OR
- Impressive admin dashboard showing inventory status

**Agent Roles to Use:**
- **Backend Developer:** Build schedule/inventory APIs
- **Frontend Developer:** Build admin dashboard
- **QA Engineer:** Test inventory accuracy

**Example Focus:**
```
Priority 1: Show data accuracy (zero inventory errors)
Priority 2: Core operations work (book seat → inventory decrements)
Priority 3: Handle edge cases (defer if time-limited)
```

**Demo:** Live demo of inventory system to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add overbooking logic or seat class differentiation
- Improve transaction handling and race condition prevention
- Optional: Integrate with other directors' APIs (booking portal, pricing)
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced inventory system with 2-3 new features
- More robust concurrency handling
- Better operational dashboards

**Gamerunner May Introduce:**
- "System crash - restore inventory data!"
- "International expansion - handle multi-timezone scheduling!"
- "Competitor has dynamic overbooking - match it!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end inventory operations
- Handle concurrent bookings with proper locking
- Transaction integrity and rollback
- Performance optimization (< 100ms queries)
- Final operational polish

**Deliverable:**
- Production-ready inventory system
- Complete operational dashboard
- Bulletproof data integrity

**Demo:** Full inventory operations from booking to analytics. Company launches! 🎉

---

### Quarter 5: Survive & Adapt (30 min)
**Focus:** Quick response to market conditions (dice-driven scenario)

**Possible Scenarios:**
- Crisis: "Mass cancellations - handle inventory updates!"
- Opportunity: "Partner airline wants inventory sharing!"
- Competition: "Competitor has real-time sync - match it!"

**Your Objectives:**
- Respond to gamerunner's dice roll scenario
- Build or fix quickly
- Demonstrate operational resilience

**Demo:** Show how you handled the crisis/opportunity.

---

### Quarter 6: Final Challenge (30 min)
**Focus:** One more scenario, final improvements

**Possible Scenarios:**
- Innovation: "Add AI-powered schedule optimization"
- Premium: "Launch premium cabin inventory tier"
- Scale: "Traffic 10x - optimize database"

**Demo:** Final feature showcase and retrospective.

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Can view flight schedule
- See how many seats available/booked
- Book a seat (number decrements)
- Basic admin interface

**Silver Tier:**
- Real-time updates across views
- Handles concurrent operations
- Clean data visualization
- Professional admin dashboard

**Gold Tier:**
- Sophisticated overbooking logic
- Beautiful analytics and charts
- Fast performance (< 100ms queries)
- "This could run an actual airline"

**Demo Script (30 seconds):**
1. Show flight schedule dashboard
2. Display inventory for a flight (150/180 seats booked)
3. Simulate booking → inventory updates
4. Show overbooking calculation
5. Display route analytics
6. Explain multi-agent strategy

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Inventory & Scheduling

**Q1-Q2 (Foundation building):** **Sequential Pipeline** 🔄
- Agent 1: Database schema and data models
- Agent 2: API layer on top of database
- Agent 3: Admin dashboard consuming API
- **Why:** Inventory systems need solid data foundation first
- See TUTORIAL.md "Pattern 2: Sequential Pipeline" for detailed example

**Q3-Q4 (Reliability & features):** **Test-Driven Development** 🧪
- Agent 1: Write tests for concurrency, edge cases, data integrity
- Agent 2: Implement features to pass tests
- Agent 3: Performance optimization and stress testing
- **Why:** Inventory accuracy is mission-critical, can't afford bugs
- See TUTORIAL.md "Pattern 5: Test-First Development" for examples

**Q5+ (Complex operations):** **Specialist Roles** 🎯
- Database Agent: Owns schema, queries, optimization across quarters
- Backend Agent: Owns API logic, business rules across quarters
- Ops Agent: Owns monitoring, integrity checks, reporting
- **Why:** Context retention, domain expertise in critical systems
- See TUTORIAL.md "Pattern 3: Specialist Roles" for details

### Role-Specific Tips

**Database-first thinking:**
Inventory is all about data integrity. Start with schema design and constraints before building APIs. Agents should understand foreign keys, indexes, and transactions.

**Transaction awareness:**
Prompt agents explicitly about concurrency: "Use database transactions" or "Handle race conditions with SELECT FOR UPDATE". Don't assume agents will add this automatically.

**Test critical paths:**
Concurrent bookings, cancellations, and overbooking logic are where bugs hide. Dedicate an agent to testing these scenarios specifically.

**Visualize data flow:**
Operations teams live in dashboards. Invest agent time in clear inventory visualization - seat maps, availability charts, trend graphs.

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (Example 2: Building an Inventory API)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Inventory & Scheduling-Specific Challenges

**"Concurrent bookings cause race conditions"**
- **Solution:** Tell backend agent: "Use database transactions with SELECT FOR UPDATE"
- Or use testing agent: "Write tests that simulate concurrent bookings, then fix race conditions"
- Quick fix: Implement row-level locking in booking endpoint
- See TUTORIAL.md for transaction handling patterns

**"Overbooking logic is complex"**
- **Solution:** Start simple: "Allow 5% overbooking for economy class only"
- Iterate: "Add seat class differentiation and historical no-show rates"
- Use specialist agent: "Design overbooking algorithm based on airline industry standards"
- Don't overthink in Q1-Q2, add sophistication in Q3-Q4

**"Performance is slow with many flights"**
- **Solution:** Database optimization agent: "Add indexes on flight_id, departure_date, status"
- Common issue: N+1 queries - fix with proper JOINs
- Use caching agent: "Cache flight availability for 30 seconds to reduce database load"
- Target: < 100ms API response time

**"Data integrity issues - negative inventory or orphaned bookings"**
- **Solution:** Reconciliation agent: "Build nightly job that validates inventory counts"
- Add database constraints: "CREATE CHECK constraint ensuring available_seats >= 0"
- Use audit agent: "Log all inventory changes with timestamps and user IDs"
- Critical for production readiness in Q4

---

## TECH STACK SUGGESTIONS

### Option A: Python Backend (Recommended)
- **Backend:** Flask or FastAPI
- **Database:** SQLite (simple) or Postgres (robust)
- **Admin UI:** Flask-Admin or custom HTML
- **Charts:** Chart.js or Plotly
- **Why:** Python is backend-engineer friendly, great for data

### Option B: Node.js Backend
- **Backend:** Express.js
- **Database:** SQLite or MongoDB
- **Admin UI:** Admin-bro or custom
- **Charts:** Chart.js
- **Why:** Fast development, JavaScript everywhere

### Option C: Full Framework
- **Framework:** Django (includes admin panel!)
- **Database:** Built-in SQLite
- **Why:** Django Admin gives you 80% of UI for free

**Pro tip:** If you know Django, use it. The admin panel is a massive time-saver for inventory dashboards.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research inventory management systems
- Define your service architecture
- Create vision doc with database schema
- **Success = clear strategy and data model for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on data accuracy and reliability
- Core inventory operations work
- **Success = impressive demo showing operational excellence**

### Q3: Integration & Features (60 min)
- Add overbooking logic or advanced features
- Better concurrency handling
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete end-to-end inventory operations
- Edge case handling and data integrity
- Performance optimization
- Operational dashboards
- **Success = production-ready inventory system, ready to launch!**

### Q5: Survive Competition (30 min)
- Quick response to dice-driven scenario
- Crisis management or opportunity capture
- **Success = adapted quickly, maintained data integrity**

### Q6: Final Challenge (30 min)
- One more scenario response
- Final improvements or innovation
- **Success = strong finish, bulletproof inventory system**

---

## INTEGRATION POINTS (OPTIONAL)

You can work independently with mock bookings, or integrate:

### With Booking Portal
- Provide API for flight search
- Receive booking requests
- Return seat availability

### With Pricing
- Share seat availability data
- Receive dynamic pricing updates

### With Check-in
- Share seat assignments
- Receive check-in confirmations

**Mock it:** Just create sample API endpoints that return realistic data. Other teams can call your endpoints or you can simulate their calls.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Inventory is always accurate (no lost bookings)
- ✅ System handles concurrent operations correctly
- ✅ Dashboard clearly shows operational status
- ✅ Overbooking logic is sophisticated
- ✅ Performance is fast (< 100ms queries)

### Red Flags to Avoid
- ❌ Double-booking the same seat
- ❌ Negative inventory counts
- ❌ Race conditions in concurrent bookings
- ❌ Slow queries that timeout
- ❌ No visualization (just API responses)

---

## QUICK START GUIDE

### Before Game Day
- Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) - Learn to think like a director
- Read [TUTORIAL.md](../TUTORIAL.md) - Multi-agent patterns
- Bookmark TUTORIAL.md "Quick Reference" for prompt templates

### Quarter 1: Research & Vision (60 min)

**First 10 minutes:**
1. Decide: What will I deliver? (Vision doc? Schema diagrams? MVP?)
2. Plan your agent strategy: Which agents for which tasks?
3. Start Agent 1 (Database Architect): Begin schema design

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Design database schema for flights, inventory, bookings
- Agent 2: Research overbooking algorithms and inventory best practices
- Agent 3: Design service architecture and API contracts

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision and schema
2. Decide which 1-2 services to build
3. Start Agent 1 (Backend): Build first service

**Minutes 5-50:**
Build your investor demo:
- Agents build services based on Q1 architecture
- Focus on data accuracy and reliability
- Test as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to answer investor questions

### Quarters 3-6: Execute & Adapt

**Each quarter:**
1. Listen to gamerunner scenario
2. Decide: What agents do I need?
3. Build/fix quickly
4. Demo at end

**Between quarters:**
- Think about data integrity: What edge cases could break this?
- Review TUTORIAL.md for concurrency patterns
- Plan: How will I improve next quarter?

---

## PARTING WISDOM

> "You are the keeper of truth in this airline. When someone asks 'is seat 12A available?', your system must answer correctly, every time, instantly. Multi-agent development helps you build faster, but never sacrifice correctness for speed."

Remember: You're not just tracking seats - you're the operational foundation that every other system depends on. Build it right. 🛫📊
