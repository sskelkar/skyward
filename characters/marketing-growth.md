# DIRECTOR OF MARKETING & GROWTH
## Character Sheet

---

## YOUR ROLE

You are the **Director of Marketing & Growth** at SkywardAI - the customer acquisition machine who turns unknowns into customers.

**Department:** Marketing - Analytics & Automation
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** Chief Marketing Officer

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Every dollar spent on marketing should return three dollars in bookings."**

You are the growth engine. While others build the product, you bring the customers. Your campaigns, landing pages, and growth experiments determine whether the airline thrives or struggles in obscurity.

### What Drives You
- **Customer acquisition:** Grow the user base profitably
- **Conversion optimization:** Turn visitors into bookers
- **Data-driven experimentation:** A/B test everything
- **Attribution:** Know which channels drive real bookings

### What Keeps You Up at Night
- High customer acquisition cost (CAC)
- Low conversion rates despite high traffic
- Wasted ad spend on channels that don't convert
- Competitors outbidding you on keywords

---

## CHARACTER FLAVOR

You're the **growth hacker experimentalist** - you see every page, email, and ad as a hypothesis to test.

**Your mantras:**
- "Test, measure, optimize, repeat"
- "Data over intuition"
- "Growth is a system, not a tactic"
- "CAC must be less than LTV"

**In board meetings, you say:**
- "Email campaigns drove 2,400 bookings at $12 CAC"
- "Landing page A/B test improved conversion 34%"
- "Paid search ROI: 4.2x, organic: 8.1x"
- "Customer LTV is $890, we acquire at $45"

**Your personality:**
- Experimental, metrics-obsessed, creative
- Love finding growth levers
- Frustrated by unmeasured marketing
- The person who says "let's test that"

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Campaign Management API** (Agent Team A)
- Tech: Flask/FastAPI backend
- Port: 5001
- Purpose: Email campaigns, segmentation, triggered sends
- Team: 1-2 backend agents

**Service 2: Analytics Tracking Service** (Agent Team B)
- Tech: Flask/FastAPI backend
- Port: 5002
- Purpose: Event tracking, attribution, customer journey
- Team: 1-2 backend agents

**Service 3: Landing Page A/B Test Dashboard** (Agent Team C)
- Tech: React/Vue/vanilla JS frontend
- Port: 3000
- Purpose: Landing pages, A/B tests, analytics visualization
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
- Research successful growth strategies and attribution models
- Define your 2-3 service architecture (Campaign API, Analytics Service, Landing Page Dashboard)
- Create vision document with marketing funnel flows and campaign designs
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with architecture diagram and campaign flows
- Marketing funnel wireframes or campaign mockups
- Simple MVP (if time permits) - basic prototype

**Agent Roles to Use:**
- **Product Manager:** Define growth strategy and campaign requirements
- **Business Analyst:** Research attribution models and analytics approaches
- **UX Designer:** Create landing page wireframes and campaign designs
- **Technical Architect:** Design service architecture

**Example Prompt:**
```
"You are a Product Manager researching growth strategies for airlines.

Analyze successful acquisition funnels and viral growth tactics.
Define our growth strategy:
1. Acquisition channels (paid, organic, referral)
2. Conversion optimization approach
3. Attribution model design
4. Key growth metrics

Focus on metrics-driven growth and experimentation frameworks."
```

**Demo:** Present your vision doc, campaign designs, or MVP. Explain your growth strategy and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable campaign system or analytics dashboard
- Make it look professional with real growth metrics
- Focus on what investors want to see: acquisition and viral potential

**Deliverable:**
- Working campaign management system (mock data is fine)
- Working attribution dashboard OR
- Impressive analytics UI showing growth metrics

**Agent Roles to Use:**
- **Backend Developer:** Build campaign/analytics APIs
- **Frontend Developer:** Build polished dashboard UI
- **QA Engineer:** Test the demo flow

**Example Focus:**
```
Priority 1: Show compelling growth metrics (investors love CAC/LTV)
Priority 2: Demonstrate attribution working (search → results → book)
Priority 3: Handle edge cases (defer if time-limited)
```

**Demo:** Live demo of campaign system or analytics dashboard to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add A/B testing or multi-touch attribution
- Improve campaign automation and analytics depth
- Optional: Integrate with other directors' APIs (booking, inventory)
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced growth system with 2-3 new features
- More robust attribution modeling
- Better analytics visualization

**Gamerunner May Introduce:**
- "CAC spiked 40% - optimize campaigns now!"
- "Competitor went viral - need growth hack!"
- "Privacy regulation - update tracking compliance!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end growth system
- Handle campaign automation and triggered sends
- Multi-touch attribution working
- Real-time analytics dashboard
- Final polish on visualizations

**Deliverable:**
- Production-ready growth platform
- Complete attribution and analytics system
- Professional marketing dashboard

**Demo:** Full growth system from campaign creation to attribution analysis. Company launches! 🎉

---

### Quarter 5: Survive & Adapt (30 min)
**Focus:** Quick response to market conditions (dice-driven scenario)

**Possible Scenarios:**
- Crisis: "CAC doubled - need immediate optimization!"
- Opportunity: "Viral loop opportunity - build referral system!"
- Competition: "Competitor has better attribution - match it!"

**Your Objectives:**
- Respond to gamerunner's dice roll scenario
- Build or fix quickly
- Demonstrate growth adaptability

**Demo:** Show how you handled the crisis/opportunity.

---

### Quarter 6: Final Challenge (30 min)
**Focus:** One more scenario, final improvements

**Possible Scenarios:**
- Innovation: "Add AI-powered campaign optimization"
- Premium: "Launch influencer marketing tracking"
- Scale: "Traffic 10x - upgrade analytics infrastructure"

**Demo:** Final feature showcase and retrospective.

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Campaign dashboard that shows data
- Can track basic events
- Landing pages load and track visits
- Simple analytics charts

**Silver Tier:**
- Clean attribution visualization
- Professional campaign dashboard
- A/B testing working with results
- Looks like a real growth platform

**Gold Tier:**
- Beautiful analytics dashboards
- Real-time tracking visualization
- Sophisticated attribution models
- "Wow, this is like Mixpanel/Amplitude!"

**Demo Script (30 seconds):**
1. Show campaign performance dashboard
2. Display A/B test results (variant B +34% conversion)
3. Show attribution flow (which channels drive bookings)
4. Display ROI by channel chart
5. Show real-time analytics updating
6. Explain multi-agent strategy used

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Marketing & Growth

**Q1-Q2 (Foundation building):** **Parallel Execution** ⚡
- Agent 1: Campaign Management API (create, send, track campaigns)
- Agent 2: Analytics Tracking Service (event tracking, attribution)
- Agent 3: Landing Page Dashboard (UI, A/B tests, visualizations)
- **Why:** Fastest way to get working end-to-end growth system
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Polish & features):** **Iterative Refinement** ✨
- Agent 1: Add new feature (multi-touch attribution, automation)
- Agent 2: Review and improve analytics/visualization quality
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples

**Q5+ (Complex features):** **Specialist Roles** 🎯
- Analytics Agent: Owns all tracking and attribution work
- Campaign Agent: Owns all campaign and automation work
- Visualization Agent: Owns all dashboard and reporting work
- **Why:** Context retention, domain expertise
- See TUTORIAL.md "Pattern 3: Specialist Roles" for details

### Role-Specific Tips

**Keep analytics separate from campaigns:**
Attribution logic is complex - dedicate one agent to tracking/attribution while another handles campaign execution.

**Use chart libraries early:**
Prompt agents with "Use Chart.js/D3.js" or "Make it look like Mixpanel" rather than building visualizations from scratch. Saves time, looks better.

**Demo-first thinking:**
Structure your agents around what you'll show: "Agent 1 builds campaigns, Agent 2 builds attribution, Agent 3 builds what investors will see."

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (adapt patterns to marketing use cases)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Marketing & Growth-Specific Challenges

**"Attribution modeling is too complex"**
- **Solution:** Start simple: "Implement last-touch attribution only"
- Or use integration agent: "Build simple attribution: credit the last marketing touchpoint before booking"
- Defer multi-touch to Q3: "Add linear attribution model that splits credit equally"

**"A/B test statistics are confusing"**
- **Solution:** Be specific in prompts: "Calculate simple conversion rate: bookings/visitors. Show which variant is higher."
- Avoid complex statistics initially: "No p-values needed for demo, just show the numbers"
- Use refinement agent: "Add statistical significance calculator using basic z-test"

**"Campaign tracking doesn't connect to bookings"**
- **Solution:** Test each service separately first with mock data
- Common issue: Campaign ID not being passed through booking flow
- Use integration agent to bridge: "When user clicks campaign link, store campaign_id in session, attribute booking to that campaign"

**"Landing pages look unprofessional"**
- **Solution:** Add to prompt: "Use modern CSS framework like Tailwind, make it look like successful travel marketing"
- Or use refinement agent: "Review these landing pages and make them look like professional marketing campaigns"
- Quick win: "Use Bootstrap with hero image, headline, CTA button, and benefits section"

**"Analytics dashboard shows no data or errors"**
- **Solution:** Use simple, self-contained mock data
- Avoid complex database queries - start with JSON arrays
- Test your demo setup 2 minutes before presenting

---

## TECH STACK SUGGESTIONS

### Option A: Python Analytics Stack (Recommended for Q1-Q2)
- **Backend:** Flask or FastAPI
- **Analytics:** Pandas for data analysis
- **Visualization:** Chart.js or Plotly
- **Database:** SQLite or JSON files
- **Why:** Python excels at analytics and data processing

### Option B: JavaScript Full Stack (If you're comfortable)
- **Backend:** Express.js
- **Frontend:** React with Chart.js
- **Database:** Postgres or SQLite
- **Why:** JavaScript everywhere, easier frontend integration

### Option C: Analytics Platform Approach
- **Framework:** Use existing analytics libraries
- **Focus:** Custom dashboards and attribution logic
- **Why:** Focus on growth strategy, not building infrastructure from scratch

**Pro tip:** Use whatever you know best. Learning a new framework + learning multi-agent = too much for 30 minutes.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research growth strategies and attribution models
- Define your service architecture
- Create vision doc with campaign flows
- **Success = clear growth strategy and plan for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on showing compelling growth metrics
- Core attribution or campaign system works
- **Success = impressive demo that shows acquisition potential**

### Q3: Integration & Features (60 min)
- Add A/B testing or multi-touch attribution
- Better campaign automation
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete end-to-end growth system
- Campaign automation and attribution
- Mobile responsive dashboards
- Professional analytics polish
- **Success = production-ready growth platform, ready to launch!**

### Q5: Survive Competition (30 min)
- Quick response to dice-driven scenario
- Crisis management or growth opportunity capture
- **Success = adapted quickly, maintained quality**

### Q6: Final Challenge (30 min)
- One more scenario response
- Final improvements or innovation
- **Success = strong finish, learned multi-agent orchestration**

---

## INTEGRATION POINTS (OPTIONAL)

You can work completely independently with mock data, or optionally integrate:

### With Booking Portal
- Embed tracking pixels on booking pages
- Attribute bookings to marketing campaigns
- Or use mock booking data shaped like their format

### With Recommendations
- Get personalized content for campaigns
- Target customer segments
- Or hardcode segment definitions

### With Pricing
- Coordinate promotional pricing for campaigns
- Test price messaging in A/B tests
- Or use mock price data

### With Notifications
- Trigger campaign emails through their service
- Or mock email sending

**Remember:** Integration is bonus points, not required. Focus on your own system first.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Attribution shows clear channel performance
- ✅ A/B tests demonstrate optimization working
- ✅ Dashboards look professional and insightful
- ✅ Multi-agent strategy is clear and effective
- ✅ You improve and add features each quarter

### Red Flags to Avoid
- ❌ Campaigns with no tracking or attribution
- ❌ Landing pages that look like 1998
- ❌ No way to measure what's working
- ❌ Analytics dashboards with no data or errors
- ❌ Same demo every quarter with no evolution

---

## QUICK START GUIDE

### Before Game Day
- Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) - Learn to think like a director
- Read [TUTORIAL.md](../TUTORIAL.md) - Multi-agent patterns
- Bookmark TUTORIAL.md "Quick Reference" for prompt templates

### Quarter 1: Research & Vision (60 min)

**First 10 minutes:**
1. Decide: What will I deliver? (Vision doc? Campaign designs? MVP?)
2. Plan your agent strategy: Which agents for which tasks?
3. Start Agent 1 (Product Manager): Begin growth strategy research

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research growth strategies and attribution models
- Agent 2: Create campaign flows and landing page wireframes
- Agent 3: Design service architecture for analytics

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
- Focus on compelling growth metrics
- Test as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to answer investor questions about CAC/LTV

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

## LEGACY MULTI-AGENT STRATEGIES

📚 **Note:** The strategies below are from the original version. For current best practices, see the "MULTI-AGENT STRATEGIES" section above and [TUTORIAL.md](../TUTORIAL.md).

### Legacy Strategy 1: Campaigns + Analytics + Pages (Recommended for Q1)
**When to use:** Building complete marketing system

```
Agent 1 (Campaign Manager):
"Build email campaign system:

Database:
- Campaigns: campaign_id, name, subject, body, sent_at, segment
- Recipients: email, user_id, campaign_id, opened, clicked, booked
- Segments: segment_id, name, criteria (business_travelers, budget_seekers)

API:
- POST /campaigns (create campaign)
- POST /campaigns/{id}/send (send to segment)
- GET /campaigns/{id}/stats (open rate, click rate, conversion)

Generate 3 sample campaigns with mock results."

Agent 2 (Landing Page Builder):
"Build landing page system:

Features:
- Create landing pages with customizable content
- Track visits, clicks, conversions
- Different variants for A/B testing
- Simple template system

Create 3 landing page templates:
- 'Spring Sale' - 20% off destinations
- 'Business Travel' - premium features
- 'Budget Traveler' - cheapest flights

API:
- GET /landing/{id} (serve page)
- POST /landing/{id}/track (track events)"

Agent 3 (Analytics Dashboard):
"Build marketing analytics dashboard:
- Campaign performance table (sent, opened, clicked, booked, ROI)
- Landing page performance (views, bounce rate, conversion)
- Funnel visualization (awareness → consideration → booking)
- Channel attribution chart
- Top performing campaigns

Use Chart.js for visualizations."
```

**Timeline:**
- Min 0-10: Agents 1 & 2 in parallel
- Min 10-22: Agent 3 builds dashboard
- Min 22-25: Test and demo

---

### Legacy Strategy 2: A/B Testing Framework (Recommended for Q2)
**When to use:** Optimizing conversion

```
Agent 1 (A/B Test Engine):
"Build A/B testing system:

For landing pages:
- Variant A (control): Original design
- Variant B (test): New headline/CTA/image
- Random assignment (50/50 split)
- Track conversions by variant

For emails:
- Variant A: Subject line 1
- Variant B: Subject line 2
- Track open rate by variant

Statistical significance calculator.
API: POST /experiments/create, GET /experiments/{id}/results"

Agent 2 (Variant Generator):
"Create landing page variants:

Variant A (control):
- Headline: 'Book Your Next Adventure'
- CTA: 'Search Flights'
- Hero image: Beach

Variant B (test):
- Headline: 'Fly Anywhere for $99'
- CTA: 'Grab This Deal'
- Hero image: City skyline

Build both as actual HTML pages.
Track which converts better."

Agent 3 (Results Analyzer):
"Analyze A/B test results:
- Calculate conversion rate by variant
- Determine statistical significance (p-value)
- Estimate revenue impact of winner
- Recommend: keep testing or declare winner

Create results dashboard showing:
- Variant performance comparison
- Confidence interval
- Recommendation"
```

---

### Legacy Strategy 3: Attribution System (Recommended for Q3)
**When to use:** Understanding what drives bookings

```
Agent 1 (Tracking System):
"Build customer touchpoint tracking:

Track every marketing interaction:
- User saw ad (channel: Google, Facebook, Email)
- User clicked ad → landed on page
- User searched flights
- User booked flight

Store customer journey:
- journey_id, user_id, touchpoints[], booking_id

API: POST /track (record touchpoint), GET /journeys/{user_id}"

Agent 2 (Attribution Model):
"Build attribution models:

Model 1 - Last Touch:
- 100% credit to last touchpoint before booking

Model 2 - First Touch:
- 100% credit to first touchpoint

Model 3 - Linear:
- Equal credit to all touchpoints

Model 4 - Time Decay:
- More recent touchpoints get more credit

Calculate attributed bookings & revenue per channel.
API: GET /attribution/{model} → returns channel performance"

Agent 3 (ROI Dashboard):
"Build marketing ROI dashboard:
- Spend by channel (mock ad spend data)
- Attributed bookings by channel
- Revenue by channel
- ROI calculation (revenue / spend)
- CAC (customer acquisition cost) by channel

Visualize: which channels are profitable?
Show recommendations: increase spend on X, decrease on Y."
```

---

### Legacy Strategy 4: Growth Automation (Recommended for Q4)
**When to use:** Scaling marketing operations

```
Agent 1 (Automated Campaigns):
"Build triggered campaign system:

Triggers:
- User searched but didn't book → send 'Complete your booking' email
- User booked → send 'Prepare for your trip' email series
- 30 days after flight → send 'We miss you' re-engagement
- Abandoned cart → send reminder with discount

Implement workflow engine.
API: POST /triggers/{event} → queues campaign"

Agent 2 (Dynamic Content):
"Build personalized content generator:

Email personalization:
- Insert user name, searched destinations
- Show relevant flight deals
- Include personalized recommendations

Landing page personalization:
- Show different hero based on user segment
- Display relevant destinations
- Adjust messaging (business vs leisure)

Use template engine with variable substitution."

Agent 3 (Performance Monitor):
"Build real-time campaign monitor:
- Alert if campaign has low open rate (< 15%)
- Alert if landing page has high bounce (> 70%)
- Suggest optimizations automatically
- Auto-pause underperforming campaigns

Create monitoring dashboard with alerts."
```

---

## LEGACY COMMON CHALLENGES & SOLUTIONS

📚 **Note:** These are preserved from the original version. For current best practices, see the "COMMON CHALLENGES & SOLUTIONS" section above.

### Challenge 1: "Don't have real user traffic"
**Solution:**
```
Agent prompt: "Generate realistic mock traffic data:
- 1000 visitors per day
- Varying by channel (40% organic, 30% paid, 20% email, 10% social)
- Realistic conversion funnel (100 visitors → 20 searches → 5 bookings)
- Different performance by channel

Create as time-series data for charts."
```

### Challenge 2: "A/B testing seems complex"
**Solution:**
```
Agent prompt: "Build simple A/B test:
- Randomly assign visitors to A or B (50/50)
- Track conversions for each
- Calculate: conversion_rate = bookings / visitors
- Show which variant performs better

No statistics needed for basic demo. Just show the numbers."
```

### Challenge 3: "Landing pages look terrible"
**Solution:**
```
Agent prompt: "Create beautiful landing page:
- Use Bootstrap or Tailwind CSS
- Include: hero image, headline, CTA button, benefits section
- Make it responsive (mobile-friendly)
- Add basic animations

Model after successful travel site landing pages."
```

### Challenge 4: "Attribution is confusing"
**Solution:**
```
Agent prompt: "Implement simple last-touch attribution:
- When user books, credit the most recent marketing touchpoint
- Example: User saw Facebook ad → clicked email → booked
  → Credit goes to: Email

Track which channel gets credit for each booking.
Sum bookings by channel. Simple."
```


---

## PARTING WISDOM

> "Marketing without measurement is just spending money. Your job is to build the instrumentation and experimentation infrastructure that turns marketing from an art into a science. Multi-agent development lets you build campaigns, landing pages, AND analytics simultaneously - use this to iterate faster than competitors."

Remember: You're not just creating ads - you're building the growth engine that will scale this airline from startup to industry leader. Every click, every conversion, every dollar of ROI counts. 📈🚀
