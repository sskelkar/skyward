# DIRECTOR OF CHECK-IN & BOARDING
## Character Sheet

---

## YOUR ROLE

You are the **Director of Check-in & Boarding** at SkywardAI - the gatekeeper who turns bookings into successful flights.

**Department:** Operations - Passenger Services
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Airport Operations

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Every passenger checked in, every seat assigned, every boarding pass in hand - 24 hours before departure."**

You manage the critical transition from "I have a booking" to "I'm on the plane." Missed check-ins mean missed flights. Poor seat assignments mean angry passengers. Your systems ensure smooth airport operations and happy travelers.

### What Drives You
- **Efficiency:** Check-in completed in under 90 seconds
- **Accuracy:** Zero seat conflicts at the gate
- **Self-service:** 95% online check-in rate
- **Optimization:** Perfect seat assignment balancing passenger preferences and revenue

### What Keeps You Up at Night
- Gate agents dealing with double-assigned seats
- Long airport check-in lines
- Passengers who forgot to check in and miss flights
- Seat assignment algorithms that upset families

---

## CHARACTER FLAVOR

You're the **operations perfectionist** - you see check-in as the moment where everything must work flawlessly. While other directors obsess over bookings or prices, you obsess over boarding efficiency and zero seat conflicts.

**Your mantras:**
- "Check-in is the first impression at the airport"
- "Every seat assignment is an optimization problem"
- "Self-service is better service"
- "A smooth boarding saves 10 minutes - do that 100 times a day"

**In board meetings, you say:**
- "Online check-in rate: 94%, up from 78%"
- "Average check-in time: 47 seconds"
- "Zero seat conflicts at gates this quarter"
- "Boarding time reduced from 35 to 28 minutes per flight"

**Your personality:**
- Detail-oriented, process-driven, passenger-focused
- Love optimizing logistics
- Proud of smooth operations
- The person who says "but what about edge cases?"

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Check-in API** (Agent Team A)
- Tech: Flask/FastAPI backend
- Port: 5001
- Purpose: Check-in processing, booking validation, status management
- Team: 1-2 backend agents

**Service 2: Seat Assignment Service** (Agent Team B)
- Tech: Flask/FastAPI backend
- Port: 5002
- Purpose: Seat map management, assignment algorithms, availability tracking
- Team: 1-2 backend agents

**Service 3: Boarding Pass Generator** (Agent Team C)
- Tech: Python/Node.js service or frontend integration
- Port: 5003 or embedded in frontend
- Purpose: Generate boarding passes with QR codes, mobile passes
- Team: 1-2 agents (backend + frontend)

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
- Research what makes great check-in systems (use agents to analyze airline apps)
- Define your 2-3 service architecture (Check-in API, Seat Assignment, Boarding Pass)
- Create vision document with user flows and seat map designs
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with architecture diagram and user flows
- Wireframes or mockups of seat selection and boarding pass
- Simple MVP (if time permits) - basic prototype

**Agent Roles to Use:**
- **Business Analyst:** Research check-in process best practices and boarding flows
- **UX Designer:** Create seat map wireframes and boarding pass designs
- **Technical Architect:** Design service architecture and seat assignment algorithms

**Example Prompt:**
```
"You are a business analyst researching airline check-in systems.

Analyze 3 successful airline check-in flows (United, Southwest, Delta).
Document best practices for:
1. Online check-in process
2. Seat selection interfaces
3. Boarding pass formats
4. Mobile check-in experience

Focus on efficiency and passenger satisfaction."
```

**Demo:** Present your vision doc, wireframes, or MVP. Explain your strategy and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable check-in flow (happy path)
- Make boarding pass look professional
- Focus on what investors want to see: seamless operations

**Deliverable:**
- Working check-in functionality (mock data is fine)
- Interactive seat map OR
- Impressive boarding pass design with QR code

**Agent Roles to Use:**
- **Backend Developer:** Build check-in/seat assignment APIs
- **Frontend Developer:** Build polished seat selection UI
- **QA Engineer:** Test the demo flow

**Example Focus:**
```
Priority 1: Make it look professional (investors care about polish)
Priority 2: Core flow works (check-in → seat select → boarding pass)
Priority 3: Handle edge cases (defer if time-limited)
```

**Demo:** Live demo of check-in flow to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add group check-in or special requirements handling
- Improve seat assignment algorithm
- Optional: Integrate with other directors' APIs (bookings, inventory)
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced check-in system with 2-3 new features
- More robust error handling
- Better UX polish

**Gamerunner May Introduce:**
- "Peak check-in causing system slowdown - optimize!"
- "Gate agents reporting seat conflicts - fix assignment logic!"
- "Need biometric boarding for premium passengers!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end check-in and boarding flow
- Handle edge cases (special needs, groups, standby)
- Mobile-responsive boarding passes
- Gate operations dashboard
- Final UX polish

**Deliverable:**
- Production-ready check-in platform
- Complete passenger journey works smoothly
- Professional boarding pass design

**Demo:** Full check-in flow from booking lookup to boarding pass. Company launches! 🎉

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Can check in for a flight
- Select seat on basic map
- Generate boarding pass
- View check-in status

**Silver Tier:**
- Smart seat selection UI
- Beautiful boarding pass design
- Group check-in works
- Clean operations dashboard

**Gold Tier:**
- Sophisticated seat optimization
- Mobile-responsive boarding passes
- Real-time boarding updates
- "This looks like airline software"

**Demo Script (30 seconds):**
1. Show check-in interface
2. Enter booking reference, check in
3. Display seat map, select seat 12A
4. Generate boarding pass with QR code
5. Show gate agent dashboard (checked-in passengers)
6. Explain multi-agent strategy

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Check-in & Boarding

**Q1-Q2 (Foundation building):** **Parallel Execution** ⚡
- Agent 1: Check-in API (booking validation, status management)
- Agent 2: Seat Assignment Service (seat map, selection logic)
- Agent 3: Boarding Pass Generator (QR codes, mobile format)
- **Why:** Fastest way to get working end-to-end check-in flow
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Polish & features):** **Iterative Refinement** ✨
- Agent 1: Add new feature (group check-in, boarding groups)
- Agent 2: Review and improve algorithms/UX
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples


### Role-Specific Tips

**Keep seat assignment separate from check-in logic:**
Algorithm complexity is easier to manage when one agent focuses purely on optimization while another handles the check-in workflow.

**Use visual libraries early:**
Prompt agents with "Use CSS Grid for seat map" or "Make boarding pass look like Southwest Airlines" rather than building from scratch. Saves time, looks better.

**Demo-first thinking:**
Structure your agents around what you'll show: "Agent 1 builds check-in API, Agent 2 builds seat selection UI, Agent 3 builds boarding pass display."

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (relevant patterns for service APIs and UI)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Check-in & Boarding-Specific Challenges

**"Seat map is hard to visualize"**
- **Solution:** Tell agent: "Use CSS Grid with 6 columns and 30 rows for seat layout"
- Or use integration agent: "Create interactive seat map with color coding for status"
- Quick fix: Use HTML table as fallback, style with Bootstrap
- Show examples: "Make it look like airline seat selection screens"

**"QR code generation is complex"**
- **Solution:** Be specific in prompts: "Use Python qrcode library" or "Use JavaScript qrcode.js"
- Common issue: QR code too small to scan - specify minimum 300x300px
- Tell agent: "Generate QR code from booking ID and embed in boarding pass HTML"
- Quick win: "Use qrcode library to generate PNG, display in img tag"

**"Seat assignment algorithm is complicated"**
- **Solution:** Start simple: "Assign window-preference passengers to window seats first"
- Or use specialist agent: "Build seat assignment algorithm with preference matching"
- Common issue: Overthinking optimization - simple rules work for demos
- Quick fix: "Random assignment from available seats as MVP, improve later"

**"Boarding pass doesn't look real"**
- **Solution:** Add to prompt: "Design boarding pass similar to Southwest Airlines"
- Or use refinement agent: "Make this boarding pass look professional and airline-quality"
- Show examples: "Include airline branding, large seat number, QR code, barcode aesthetic"
- Quick win: "Use template from airline boarding pass examples online"

**"Check-in API can't validate bookings"**
- **Solution:** Use mock data: "Create sample bookings table with 20 test passengers"
- Or integrate with booking system if available
- Test with curl: "Test check-in endpoint with booking reference ABC123"

---

## TECH STACK SUGGESTIONS

### Option A: Simple & Fast (Recommended for Q1-Q2)
- **Backend:** Flask (Python) or Express (Node.js)
- **Frontend:** Vanilla HTML/CSS/JavaScript for seat map
- **QR Code:** Python qrcode library or qrcode.js
- **Database:** SQLite or JSON files
- **Why:** Minimal setup, agents know these well, easy QR generation

### Option B: Modern Stack (If you're comfortable)
- **Backend:** FastAPI or Express
- **Frontend:** React or Vue for interactive seat map
- **QR Code:** qrcode.js or node-qrcode
- **Database:** Postgres or SQLite
- **Why:** More realistic, better interactive capabilities

### Option C: Full-Stack Framework
- **Framework:** Next.js or Django
- **QR Code:** Built-in library support
- **Database:** Built-in SQLite
- **Why:** Less coordination between frontend/backend

**Pro tip:** Use whatever you know best. Learning a new framework + learning multi-agent = too much for 30 minutes. Focus on the seat selection UX and boarding pass design - those are the most visual and impressive parts.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research successful check-in systems
- Define your service architecture
- Create vision doc with seat map and boarding pass wireframes
- **Success = clear strategy and plan for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on polish and "wow factor"
- Core check-in flow works with seat selection
- **Success = impressive demo that shows vision and potential**

### Q3: Integration & Features (60 min)
- Add 2-3 significant features (group check-in, boarding groups)
- Better seat assignment algorithms
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete end-to-end check-in and boarding flow
- Edge case handling (special needs, standby)
- Mobile responsive boarding passes
- Professional polish
- **Success = production-ready check-in platform, ready to launch!**

---

## INTEGRATION POINTS (OPTIONAL)

You can work completely independently with mock data, or optionally integrate:

### With Booking Portal
- Call their API to get booking details for check-in
- Or use mock bookings shaped like their format

### With Flight Inventory
- Check real seat availability from their system
- Or hardcode seat status

### With Flight Status
- Display current flight status and gate assignments
- Or mock flight information

### With Notifications
- Trigger check-in confirmation and boarding notifications
- Or show "notification sent" message

**Remember:** Integration is bonus points, not required. Focus on your own system first.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Passengers can complete check-in in every demo
- ✅ Seat map is intuitive and interactive
- ✅ Boarding pass looks professional with working QR codes
- ✅ Multi-agent strategy is clear and effective
- ✅ You improve and add features each quarter
- ✅ Edge cases are handled gracefully

### Red Flags to Avoid
- ❌ Check-in flow that returns errors
- ❌ Seat map that's confusing or non-functional
- ❌ Boarding pass that looks amateurish
- ❌ QR codes that don't generate
- ❌ Demos that require "imagine this works"
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
3. Start Agent 1 (Researcher or BA): Begin research/vision work

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research check-in system best practices
- Agent 2: Create seat map and boarding pass wireframes
- Agent 3: Design service architecture

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision
2. Decide which 1-2 services to build
3. Start Agent 1 (Backend): Build first service

**Minutes 5-50:**
Build your investor demo:
- Agents build services based on Q1 architecture
- Focus on polish and "wow factor"
- Test as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to answer investor questions

### Quarter 3 & Beyond: Execute & Adapt

**Each quarter:**
1. Listen to gamerunner scenario
2. Decide: What agents do I need?
3. Build/fix quickly
4. Demo at end

**Between quarters:**
- Reflect: What worked? What didn't?
- Review TUTORIAL.md for new techniques
- Plan: How will I improve next quarter?

---

## PARTING WISDOM

> "You have 30 minutes to build what normally takes 3 hours. Your secret weapon is coordinating 2-3 agents efficiently. The agent that builds the check-in API doesn't have to be the agent that designs the boarding pass. Assembly line > single artisan."

Good luck, Director. Every passenger's journey through your systems sets the tone for their flight. Make it seamless. 🎫✈️
