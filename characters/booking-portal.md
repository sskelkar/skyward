# DIRECTOR OF CUSTOMER BOOKING PORTAL
## Character Sheet

---

## YOUR ROLE

You are the **Director of Customer Booking Portal** at SkywardAI - the face of the company to every customer who wants to fly with us.

**Department:** Customer Experience - Frontend
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Product

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Every customer should be able to book a flight in under 60 seconds."**

You obsess over user experience. If the booking flow has friction, customers abandon and book with competitors. Your success is measured in conversion rate, time-to-book, and customer satisfaction scores.

### What Drives You
- **User delight:** Beautiful, intuitive interfaces that just work
- **Speed:** Fast page loads, instant search results, smooth interactions
- **Clarity:** No confusing forms, no hidden fees, no surprises
- **Trust:** Customers feel confident clicking "Book Now"

### What Keeps You Up at Night
- Broken search forms that drive customers away
- Slow loading times that frustrate users
- Confusing checkout flows with high abandonment
- Mobile experience that doesn't work

---

## CHARACTER FLAVOR

You're the **perfectionist who cares about pixels**. While other directors obsess over algorithms and data, you obsess over whether that button is 2px too far to the left.

**Your mantras:**
- "If users can't find it, it doesn't exist"
- "Every click is a chance to lose them"
- "Make it beautiful, make it fast"
- "The best UX is invisible"

**In board meetings, you say:**
- "Our conversion rate is 12% - industry standard is 8%"
- "Average time-to-book dropped from 90 seconds to 45 seconds"
- "Customer satisfaction score: 4.8/5"
- "Mobile traffic is 60% of our bookings"

**Your personality:**
- User advocate, slightly obsessive
- Cares deeply about craft and polish
- Frustrated by backend folks who say "just use a form"
- Pride yourself on making complex things simple

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Search API** (Agent Team A)
- Tech: Flask/FastAPI backend
- Port: 5001
- Purpose: Flight search, filtering, sorting
- Team: 1-2 backend agents

**Service 2: Booking API** (Agent Team B)
- Tech: Flask/FastAPI backend
- Port: 5002
- Purpose: Create bookings, payments, confirmations
- Team: 1-2 backend agents

**Service 3: Customer UI** (Agent Team C)
- Tech: React/Vue/vanilla JS frontend
- Port: 3000
- Purpose: User interface, booking flow
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
- Research what makes great booking portals (use agents to analyze competitors)
- Define your 2-3 service architecture (Search API, Booking API, Frontend)
- Create vision document with user flows and wireframes
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with architecture diagram and user flows
- Wireframes or mockups of the booking experience
- Simple MVP (if time permits) - basic prototype

**Agent Roles to Use:**
- **Business Analyst:** Research booking portal best practices
- **Product Manager:** Define user stories and requirements
- **UX Designer:** Create wireframes and user flows
- **Technical Architect:** Design service architecture

**Example Prompt:**
```
"You are a UX designer researching flight booking portals.

Analyze 3 successful booking sites (Expedia, Kayak, Airbnb).
Create wireframes for our booking flow:
1. Search page
2. Results page
3. Booking form
4. Confirmation page

Focus on best practices for conversion and user experience."
```

**Demo:** Present your vision doc, wireframes, or MVP. Explain your strategy and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable booking flow (happy path)
- Make it look professional and polished
- Focus on what investors want to see: value proposition

**Deliverable:**
- Working search functionality (mock data is fine)
- Working booking flow OR
- Impressive UI mockup that looks production-ready

**Agent Roles to Use:**
- **Backend Developer:** Build search/booking APIs
- **Frontend Developer:** Build polished UI
- **QA Engineer:** Test the demo flow

**Example Focus:**
```
Priority 1: Make it look amazing (investors care about vision)
Priority 2: Core flow works (search → results → book)
Priority 3: Handle edge cases (defer if time-limited)
```

**Demo:** Live demo of booking flow to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add seat selection or multi-passenger booking
- Improve error handling and validation
- Optional: Integrate with other directors' APIs (inventory, pricing)
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced booking system with 2-3 new features
- More robust error handling
- Better UX polish

**Gamerunner May Introduce:**
- "Competitor launched a better UI - differentiate!"
- "Mobile traffic is 70% - make it responsive!"
- "Accessibility audit failed - fix it!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end booking flow
- Handle edge cases and errors gracefully
- Mobile-responsive design
- Loading states and user feedback
- Final UX polish

**Deliverable:**
- Production-ready booking portal
- Complete customer journey works smoothly
- Professional appearance

**Demo:** Full booking flow from search to confirmation. Company launches! 🎉

---

### Quarter 5: Survive & Adapt (30 min)
**Focus:** Quick response to market conditions (dice-driven scenario)

**Possible Scenarios:**
- Crisis: "Bug causing failed bookings - fix it!"
- Opportunity: "Partner wants API integration - build it!"
- Competition: "Competitor has express checkout - match it!"

**Your Objectives:**
- Respond to gamerunner's dice roll scenario
- Build or fix quickly
- Demonstrate adaptability

**Demo:** Show how you handled the crisis/opportunity.

---

### Quarter 6: Final Challenge (30 min)
**Focus:** One more scenario, final improvements

**Possible Scenarios:**
- Innovation: "Add AI trip planning assistant"
- Premium: "Launch business class booking tier"
- Scale: "Traffic 10x - optimize performance"

**Demo:** Final feature showcase and retrospective.

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Form with input fields that work
- Search returns mock flight data
- Can complete a booking
- Shows confirmation

**Silver Tier:**
- Clean, intentional design
- Smooth user flow
- Handles errors gracefully
- Looks like a real booking site

**Gold Tier:**
- Beautiful UI/UX
- Animations and transitions
- Instant feedback on interactions
- "Wow, you built this in 30 minutes?"

**Demo Script (30 seconds):**
1. Open booking page in browser
2. Enter search criteria, submit
3. Browse results, select a flight
4. Fill passenger details
5. Click book, show confirmation
6. Explain multi-agent strategy used

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Booking Portal

**Q1-Q2 (Foundation building):** **Parallel Execution** ⚡
- Agent 1: Backend API (search + booking endpoints)
- Agent 2: Frontend UI (search form + results display)
- Agent 3: Integration & polish
- **Why:** Fastest way to get working end-to-end flow
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Polish & features):** **Iterative Refinement** ✨
- Agent 1: Add new feature (seat selection, multi-passenger)
- Agent 2: Review and improve UX/code quality
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples

**Q5+ (Complex features):** **Specialist Roles** 🎯
- Frontend Agent: Owns all UI/UX work across quarters
- Backend Agent: Owns all API work across quarters
- Testing Agent: Validates and finds issues
- **Why:** Context retention, domain expertise
- See TUTORIAL.md "Pattern 3: Specialist Roles" for details

### Role-Specific Tips

**Keep frontend separate from backend agents:**
UI iteration is faster when one agent focuses purely on user experience while another handles data/logic.

**Use visual frameworks early:**
Prompt agents with "Use Bootstrap/Tailwind" or "Make it look like Airbnb" rather than writing CSS from scratch. Saves time, looks better.

**Demo-first thinking:**
Structure your agents around what you'll show: "Agent 1 builds what I'll type, Agent 2 builds what I'll click, Agent 3 builds what I'll see."

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (Example 1: Building a Flight Search Page)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Booking Portal-Specific Challenges

**"Frontend can't call backend - CORS errors"**
- **Solution:** Tell backend agent: "Enable CORS for localhost:3000"
- Or use integration agent: "Fix CORS issues between these two services"
- Quick fix: Add `flask-cors` or equivalent

**"UI looks terrible / like HTML from 1998"**
- **Solution:** Be specific in prompts: "Use Tailwind CSS" or "Make it look like modern SaaS booking site"
- Show examples: "Style similar to Airbnb search page"
- Dedicate Agent 2 purely to polish: "Review this UI and make it beautiful"

**"Search works but booking breaks"**
- **Solution:** Test each endpoint separately first with curl/Postman
- Common issue: Frontend sending wrong data format to booking endpoint
- Use integration agent to bridge: "Frontend sends X, backend expects Y, fix the mismatch"

**"Mobile layout is broken"**
- **Solution:** Add to prompt: "Make fully responsive, test on mobile viewport"
- Or use refinement agent: "Make this mobile-responsive with proper breakpoints"
- Quick win: "Use Bootstrap grid for responsiveness"

**"Demo works on my machine but looks different on screen share"**
- **Solution:** Use simple, self-contained HTML files
- Avoid localhost URLs that others can't access
- Test your demo setup 2 minutes before presenting

---

## TECH STACK SUGGESTIONS

### Option A: Simple & Fast (Recommended for Q1-Q2)
- **Backend:** Flask (Python) or Express (Node.js)
- **Frontend:** Vanilla HTML/CSS/JavaScript
- **Database:** SQLite or JSON files
- **Why:** Minimal setup, agents know these well

### Option B: Modern Stack (If you're comfortable)
- **Backend:** FastAPI or Express
- **Frontend:** React or Vue
- **Database:** Postgres or SQLite
- **Why:** More realistic, better UX capabilities

### Option C: Full-Stack Framework
- **Framework:** Next.js or Django
- **Database:** Built-in SQLite
- **Why:** Less coordination between frontend/backend

**Pro tip:** Use whatever you know best. Learning a new framework + learning multi-agent = too much for 30 minutes.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research successful booking portals
- Define your service architecture
- Create vision doc with wireframes
- **Success = clear strategy and plan for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on polish and "wow factor"
- Core booking flow works
- **Success = impressive demo that shows vision and potential**

### Q3: Integration & Features (60 min)
- Add 2-3 significant features
- Better error handling
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete end-to-end flow
- Edge case handling
- Mobile responsive
- Professional polish
- **Success = production-ready booking portal, ready to launch!**

### Q5: Survive Competition (30 min)
- Quick response to dice-driven scenario
- Crisis management or opportunity capture
- **Success = adapted quickly, maintained quality**

### Q6: Final Challenge (30 min)
- One more scenario response
- Final improvements or innovation
- **Success = strong finish, learned multi-agent orchestration**

---

## INTEGRATION POINTS (OPTIONAL)

You can work completely independently with mock data, or optionally integrate:

### With Flight Inventory
- Call their API to get real flight availability
- Or use mock data shaped like their format

### With Pricing
- Display dynamic prices from their system
- Or hardcode prices

### With Payments
- Call payment processing endpoint
- Or mock successful payment

### With Notifications
- Trigger booking confirmation email
- Or show "email sent" message

**Remember:** Integration is bonus points, not required. Focus on your own system first.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Customers can complete bookings in every demo
- ✅ UI looks intentional and professional
- ✅ Multi-agent strategy is clear and effective
- ✅ You improve and add features each quarter
- ✅ Edge cases are handled gracefully

### Red Flags to Avoid
- ❌ Broken search that returns errors
- ❌ Confusing user flows
- ❌ UI that looks like 1998
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
3. Start Agent 1 (Researcher or PM): Begin research/vision work

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research booking portal best practices
- Agent 2: Create wireframes based on research
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

### Quarters 3-6: Execute & Adapt

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

> "You have 30 minutes to build what normally takes 3 hours. Your secret weapon is coordinating 2-3 agents efficiently. The agent that builds it doesn't have to be the agent that polishes it. Assembly line > single artisan."

Good luck, Director. The company's first impression is in your hands. 🎫✨
