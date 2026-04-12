# DIRECTOR OF STAFFING
## Character Sheet

---

## YOUR ROLE

You are the **Director of Staffing** at SkywardAI - the puzzle master. You put pilots in cockpits and flight attendants on planes, juggling certifications, rest rules, and last-minute changes.

**Department:** Operations - Internal Systems
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Operations

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Every flight fully crewed, every crew member qualified, every regulation followed."**

You obsess over the schedule. An uncrewed flight can't depart. An unqualified pilot is a liability. Your success is measured in flights crewed on-time, zero compliance violations, and crew satisfaction.

### What Drives You
- **Safety:** Only qualified crew on aircraft - lives depend on it
- **Compliance:** FAA regulations aren't suggestions
- **Efficiency:** Minimize deadheading, maximize crew utilization
- **Fairness:** Balanced workload, respect rest requirements

### What Keeps You Up at Night
- Flights departing without qualified crew
- Pilots exceeding flight hour limits
- Certifications expiring mid-flight
- Last-minute crew callouts with no backup

---

## CHARACTER FLAVOR

You're the **constraint solver**. While other directors worry about customers, you worry about who's flying the plane.

**Your mantras:**
- "Every flight needs a captain and first officer - no exceptions"
- "Rest rules exist for a reason"
- "Qualified means current, certified, and rested"
- "Plan for the callout - it will happen"

**In board meetings, you say:**
- "99.8% on-time crew coverage this quarter"
- "Zero FAA violations"
- "Crew utilization: 87% - industry best is 85%"
- "Average callout response time: 12 minutes"

**Your personality:**
- Systematic, detail-obsessed, contingency planner
- You've modeled every possible scenario
- Trust the schedule, verify the certifications
- Pride yourself on solving impossible puzzles

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Crew Scheduling & Assignment**
- **Purpose:** Assign qualified crew to flights, respect rest rules, optimize coverage
- **Key Decisions:**
  - How to match crew to flights? (qualifications, availability, proximity)
  - How to handle rest period calculations? (FAA limits on flight hours)
  - Automatic assignment vs. manual approval?
  - What happens when no qualified crew available?
- **Integration Points:** Reads flight schedules, writes crew assignments, checks certifications
- **Team:** 1-2 backend-focused agents

**Service 2: Certification & Qualification Tracker**
- **Purpose:** Track pilot licenses, type ratings, medical certificates, expiration dates
- **Key Decisions:**
  - What certifications must be tracked? (ATP, type ratings, medicals, recurrent training)
  - How to handle expiring certifications? (alerts, grace periods, grounding)
  - Qualification matching algorithm? (pilot needs 737 type rating for 737 flights)
  - How to verify currency requirements? (3 takeoffs/landings in 90 days)
- **Integration Points:** Used by scheduling to verify crew qualification, alerts when expiring
- **Team:** 1-2 backend-focused agents

**Service 3: Availability & Callout Management**
- **Purpose:** Track crew availability, time-off requests, sick calls, emergency replacements
- **Key Decisions:**
  - How to handle last-minute callouts? (find backup, notify operations)
  - Time-off request approval workflow?
  - How to calculate rest periods since last flight?
  - On-call vs. scheduled crew pools?
- **Integration Points:** Scheduling checks availability, crew updates their status
- **Team:** 1-2 backend-focused agents

**Why multiple services?**
- ✅ Each agent team has focused responsibility and clear ownership
- ✅ Services can be built in parallel, accelerating delivery
- ✅ Easy to demo incrementally (Scheduling in Q1, add Certifications in Q2, etc.)
- ✅ Realistic separation of concerns - scheduling, qualifications, and availability are distinct domains

📚 **For detailed multi-service patterns:** See [MULTI-SERVICE-GUIDE.md](../MULTI-SERVICE-GUIDE.md)

---

## WHAT YOU'LL BUILD

### Quarter 1: Research & Vision (45-60 min)
**Focus:** Strategy, research, and planning - NOT working code yet

**Your Objectives:**
- Research crew scheduling best practices (use agents to analyze)
- Define your 2-3 service architecture (Scheduling, Certifications, Availability)
- Create vision document with scheduling flows and constraint rules
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with architecture diagram and scheduling algorithms
- Constraint rules document (rest periods, qualifications, etc.)
- Simple MVP (if time permits) - basic crew assignment

**Agent Roles to Use:**
- **Business Analyst:** Research airline crew scheduling practices
- **Operations Specialist:** Define FAA compliance requirements
- **Technical Architect:** Design service architecture
- **Optimization Expert:** Research scheduling algorithms

**Example Prompt:**
```
"You are a crew scheduling specialist researching airline operations.

Research best practices for:
1. Pilot and flight attendant scheduling
2. FAA rest period requirements
3. Certification and qualification tracking
4. Last-minute callout handling

Create architecture diagram for crew scheduling system."
```

**Demo:** Present your vision doc, constraint rules, or MVP. Explain your approach and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build crew assignment system (mock flight data is fine)
- Show qualification matching (pilot has 737 rating → assigned to 737 flight)
- Show rest period calculations
- Focus on reliability and compliance narrative

**Deliverable:**
- Working crew assignment endpoint OR
- Certification tracker working OR
- Simple scheduling UI showing crew assignments

**Agent Roles to Use:**
- **Backend Developer:** Build scheduling APIs
- **Compliance Engineer:** Implement rest rules and qualification checks
- **QA Engineer:** Test scheduling flows

**Example Focus:**
```
Priority 1: Crew assignment works and respects constraints
Priority 2: Compliance story is solid (rest rules, qualifications)
Priority 3: Show how you handle edge cases
```

**Demo:** Live demo of crew scheduling to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add certification expiration tracking
- Add callout/replacement handling
- Optional: Integrate with Flight Inventory for real schedules
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced scheduling system with certifications
- More robust constraint handling
- Better edge case coverage

**Gamerunner May Introduce:**
- "Pilot calls in sick 2 hours before departure - find replacement!"
- "FAA audit tomorrow - prove all crew are qualified!"
- "New aircraft type delivered - update certification requirements!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end scheduling workflow
- Handle edge cases (no qualified crew, expired certifications, callouts)
- Rest period compliance verification
- Final optimization and reporting

**Deliverable:**
- Production-ready crew scheduling system
- Complete scheduling lifecycle works smoothly
- Comprehensive compliance tracking

**Demo:** Full scheduling flow from flight schedule to crew assignment. Company launches! 🎉

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- API assigns crew to flights
- Checks basic qualifications (pilot has right aircraft type)
- Returns crew assignment
- Shows crew roster

**Silver Tier:**
- Respects rest period rules (pilots can't fly if recently flew)
- Handles qualification matching (737 pilot → 737 flights only)
- Certification expiration checking
- Clear constraint violation messages

**Gold Tier:**
- Automatic backup crew assignment on callouts
- Optimization algorithm (minimize deadheading)
- Real-time compliance dashboard
- Predictive alerts for upcoming violations
- "This could run a real airline"

**Demo Script (30 seconds):**
1. Show flight schedule needing crew
2. Demonstrate crew assignment respecting qualifications
3. Demonstrate rest period checking
4. Show callout scenario and replacement
5. Show certification tracking
6. Explain compliance approach

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Staffing

**Q1-Q2 (Foundation building):** **Sequential Pipeline** 🔗
- Agent 1: Design constraint rules and qualification model
- Agent 2: Build scheduling algorithm using Agent 1's constraints
- Agent 3: Build availability tracking based on scheduler
- **Why:** Staffing systems have dependencies - constraints → scheduling → availability
- See TUTORIAL.md "Pattern 2: Sequential Pipeline" for detailed example

**Q3-Q4 (Polish & features):** **Parallel Execution** ⚡
- Agent 1: Add certification expiration alerts
- Agent 2: Add callout replacement logic (independent work)
- **Why:** Features are independent and can be built simultaneously
- See TUTORIAL.md "Pattern 1: Parallel Execution" for examples

### Director-Level Strategy Tips

**Constraints-first thinking:**
Give agents clear constraint rules upfront: "Pilots need 10 hours rest between flights" or "Only 737-rated pilots on 737 flights." Direction beats cleanup.

**Edge cases matter:**
Ask agents to think through failure scenarios: "What happens when no qualified crew available?" or "How do we handle expired medical certificates?"

**Test complex scenarios:**
Structure your agent teams around constraint violations: "Test with pilot who just flew 8 hours, pilot with expired cert, flight with no qualified crew." Work through the violations.

**Focus on correctness, not speed:**
Ask "Will this keep us FAA compliant?" not "Can we ship this faster?" Your agent teams optimize for safety and compliance.

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Debugging Agent Outputs" (for scheduling bugs)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Staffing-Specific Challenges

**"Scheduler assigns unqualified crew"**
- **Solution:** Be explicit in prompts: "Check pilot has type rating for aircraft type before assignment"
- Use testing agent: "Test with pilot who doesn't have 737 rating - should reject assignment"
- Director mindset: "What qualifications must match, and how do we verify?"

**"Rest period calculations are wrong"**
- **Solution:** Define rules clearly: "FAA requires 10 hours rest after 8-hour flight duty period"
- Use compliance agent: "Implement FAA rest period calculations per Part 117"
- Director mindset: "What are the actual regulations, and how do we encode them?"

**"No handling for 'no crew available' scenario"**
- **Solution:** Be explicit: "If no qualified crew available, return error with reason and suggestions"
- Use edge case agent: "Test scheduling when all qualified pilots are already assigned"
- Director mindset: "What do we do when the puzzle has no solution?"

**"Certification expiration dates ignored"**
- **Solution:** Add to requirements: "Check certification expiration dates - expired certs = crew unavailable"
- Use compliance agent: "Add expiration checking to crew qualification logic"
- Director mindset: "How do we prevent expired certifications from slipping through?"

**"Callout scenario breaks the schedule"**
- **Solution:** Define replacement algorithm: "On callout, find backup crew with same qualifications and availability"
- Use testing agent: "Simulate pilot callout 2 hours before flight, verify replacement found"
- Director mindset: "What's our backup plan when the plan breaks?"

---

## TECHNICAL APPROACH

As a director, you'll work with your agent teams to determine the technical approach. Here are the key decisions to consider:

### Key Technical Decisions

**Scheduling Algorithm:**
- Simple rule-based assignment vs. optimization algorithm?
- How to prioritize crew (seniority, location, recent flights)?
- Real-time scheduling vs. batch processing?

**Constraint Modeling:**
- How to represent rest rules, qualifications, availability?
- Hard constraints (must satisfy) vs. soft constraints (prefer)?
- How to explain constraint violations to users?

**Data Storage:**
- How to store crew qualifications, certifications, flight history?
- Database vs. file-based for crew records?
- How to track historical assignments for compliance audits?

**Optimization Strategy:**
- Minimize crew changes vs. minimize deadheading?
- Automated assignment vs. human approval?
- How to handle conflicting constraints?

### Director-Level Guidance

**For Q1-Q2:** Start simple - basic qualification matching and rest period checks. Use mock flight and crew data. Focus on the core scheduling logic.

**For Q3-Q4:** Add sophistication - optimization algorithms, expiration tracking, callout handling. Consider real-time constraint checking.

**Pro tip:** Start with hardcoded constraint rules (10-hour rest, type ratings). You can make them configurable later if time permits.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research crew scheduling best practices
- Define your service architecture
- Create vision doc with constraint rules and scheduling flows
- **Success = clear strategy and constraint model for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build crew assignment system
- Focus on compliance and reliability narrative
- Core scheduling logic works
- **Success = impressive demo showing solid scheduling foundation**

### Q3: Integration & Features (60 min)
- Add certification tracking
- Better constraint handling
- Optional integration with Flight Inventory
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete scheduling and callout flows
- Edge case handling
- Compliance verification
- Professional polish
- **Success = production-ready staffing system, ready to launch!**

---

## INTEGRATION POINTS (OPTIONAL)

You can work completely independently with mock data, or optionally integrate:

### With Flight Inventory & Scheduling
- Get real flight schedules to assign crew
- Or use mock flight data

### With Operations & Disruption
- Handle crew reassignments during delays/cancellations
- Or mock disruption scenarios

### With Notifications
- Send crew assignment notifications
- Or mock notification calls

### With Analytics
- Provide crew utilization data
- Or mock reporting exports

**Remember:** Integration is bonus points, not required. Focus on your own system first.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Crew assignment works and respects constraints in every demo
- ✅ Qualification matching is accurate
- ✅ Rest period compliance verified
- ✅ You improve and add features each quarter
- ✅ Edge cases (no crew, callouts) handled gracefully

### Red Flags to Avoid
- ❌ Assigning unqualified crew to flights
- ❌ Ignoring rest period requirements
- ❌ No handling for "no crew available" scenario
- ❌ Expired certifications not checked
- ❌ Demos that require "imagine compliance works"

---

## QUICK START GUIDE

### Before Game Day
- Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) - Learn to think like a director
- Read [TUTORIAL.md](../TUTORIAL.md) - Multi-agent patterns
- Bookmark TUTORIAL.md "Quick Reference" for prompt templates

### Quarter 1: Research & Vision (60 min)

**First 10 minutes:**
1. Decide: What will I deliver? (Vision doc? Constraint rules? MVP?)
2. Plan your agent strategy: Which agents for which tasks?
3. Start Agent 1 (Operations Specialist): Begin compliance research

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research crew scheduling best practices
- Agent 2: Define FAA constraint rules
- Agent 3: Create scheduling flow diagrams

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision
2. Decide which service to build first
3. Start Agent 1 (Backend): Build crew assignment

**Minutes 5-50:**
Build your investor demo:
- Agents build services based on Q1 architecture
- Focus on compliance and constraint handling
- Test as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to answer compliance questions

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

> "Crew scheduling is the ultimate constraint satisfaction problem. You're solving a jigsaw puzzle where the pieces keep changing shape. Make it work, make it compliant, make it resilient. When the pilot calls in sick, your system better have an answer."

Good luck, Director. The company's operational safety is in your hands. ✈️👨‍✈️
