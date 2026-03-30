# DIRECTOR OF PERSONALIZATION & RECOMMENDATIONS
## Character Sheet

---

## YOUR ROLE

You are the **Director of Personalization & Recommendations** at SkywardAI - the growth hacker who turns browsers into bookers and one-time customers into frequent flyers.

**Department:** Product - ML & Data Science
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Product

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Every user should see the flight they didn't know they wanted."**

You use data and ML to understand what customers want before they fully know themselves. Your recommendation engine is the difference between "I'm just browsing" and "I just booked a trip to Bali."

### What Drives You
- **Conversion rate:** Turn searchers into bookers
- **Personalization:** Each user sees different, relevant suggestions
- **Discovery:** Inspire travel, not just fulfill demand
- **Revenue per user:** Upsell premium seats, bags, insurance

### What Keeps You Up at Night
- Generic recommendations that feel spam-like
- Users who browse but never book
- Missing obvious patterns in user behavior
- Competitors with better recommendation engines

---

## CHARACTER FLAVOR

You're the **data scientist growth hacker** - you see patterns in data that others miss.

**Your mantras:**
- "Data reveals what users won't tell you"
- "Personalization is the difference between spam and helpfulness"
- "Every interaction is a signal"
- "Good recommendations feel like mind-reading"

**In board meetings, you say:**
- "Recommendation CTR is 23%, industry average is 12%"
- "Personalized users book 2.3x more than non-personalized"
- "Our ML model achieves 78% accuracy on flight preferences"
- "Upselling via recommendations added $800K revenue this quarter"

**Your personality:**
- Curious, data-obsessed, experimental
- Love A/B testing everything
- Excited by pattern discovery
- The person who says "let's test that hypothesis"

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Recommendation Engine API** (Agent Team A)
- Tech: Flask/FastAPI backend
- Port: 5003
- Purpose: ML models, recommendation algorithms, scoring
- Team: 1-2 ML/backend agents

**Service 2: User Profiling Service** (Agent Team B)
- Tech: Flask/FastAPI backend
- Port: 5004
- Purpose: Track behavior, store preferences, user segmentation
- Team: 1-2 data/backend agents

**Service 3: A/B Testing Dashboard** (Agent Team C)
- Tech: React/Vue/vanilla JS frontend
- Port: 3001
- Purpose: Analytics dashboard, experiment management UI
- Team: 1-2 frontend/analytics agents

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
- Research recommendation algorithms and best practices
- Analyze user segmentation strategies for travel
- Design ML approach and service architecture
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with ML architecture and user segmentation strategy
- Recommendation algorithm design with evaluation metrics
- Simple MVP (if time permits) - basic prototype

**Agent Roles to Use:**
- **Data Scientist:** Research recommendation algorithms (collaborative filtering, content-based, hybrid)
- **Product Manager:** Define personalization strategy and success metrics
- **Technical Architect:** Design service architecture for ML/data pipeline

**Example Prompt:**
```
"You are a data scientist researching recommendation systems for travel.

Analyze recommendation approaches:
1. Collaborative filtering (users like you also booked...)
2. Content-based (similar destinations)
3. Hybrid approaches
4. Cold start problem solutions

Design a recommendation strategy for:
- New users (no history)
- Returning users (rich history)
- Business vs leisure travelers

Include evaluation metrics (CTR, conversion rate, diversity)."
```

**Demo:** Present your vision doc, ML strategy, or MVP. Explain your approach and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable personalization flow (different users see different recs)
- Show clear business impact metrics
- Focus on what investors want to see: AI/ML differentiation

**Deliverable:**
- Working recommendation engine (mock data is fine)
- User segmentation with personalized results OR
- Impressive A/B testing dashboard showing ML impact

**Agent Roles to Use:**
- **ML Engineer:** Build recommendation algorithm/model
- **Data Engineer:** Create user profiling and tracking system
- **Analytics Engineer:** Build metrics dashboard

**Example Focus:**
```
Priority 1: Show clear personalization (User A sees X, User B sees Y)
Priority 2: Demonstrate ML/data sophistication
Priority 3: Metrics showing business impact (conversion lift, revenue)
```

**Demo:** Live demo of personalized recommendations to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add upselling recommendations (premium seats, baggage)
- Implement A/B testing framework
- Optional: Integrate with booking portal or inventory APIs
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced recommendation system with 2-3 new features
- A/B testing results showing winning strategies
- Better ML model or algorithm

**Gamerunner May Introduce:**
- "Cold start problem - 50% of users are new with no history!"
- "Recommendation quality complaints - improve relevance!"
- "Competitor has AI trip planning - differentiate!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end personalization flow
- Explainable AI (show why each recommendation was made)
- Real-time recommendation updates
- Comprehensive analytics dashboard
- Handle edge cases (new users, data sparsity)

**Deliverable:**
- Production-ready recommendation platform
- Clear business metrics showing impact
- Professional analytics dashboard

**Demo:** Full personalization flow from user profiling to personalized recommendations to conversion. Company launches! 🎉

---

### Quarter 5: Survive & Adapt (30 min)
**Focus:** Quick response to market conditions (dice-driven scenario)

**Possible Scenarios:**
- Crisis: "Recommendation quality dropped - users complaining!"
- Opportunity: "Partner wants recommendation API - build it!"
- Competition: "Competitor has ChatGPT travel advisor - match it!"

**Your Objectives:**
- Respond to gamerunner's dice roll scenario
- Build or fix quickly
- Demonstrate adaptability

**Demo:** Show how you handled the crisis/opportunity.

---

### Quarter 6: Final Challenge (30 min)
**Focus:** One more scenario, final improvements

**Possible Scenarios:**
- Innovation: "Add multi-item recommendations (flight + hotel + car)"
- Premium: "Launch AI trip planning assistant"
- Scale: "Recommendation latency too high - optimize!"

**Demo:** Final feature showcase and retrospective.

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Shows list of recommended destinations
- Basic user preference tracking
- Can explain recommendation logic
- Simple recommendations UI

**Silver Tier:**
- Personalized for different user types
- Recommendations change based on behavior
- Quality metrics tracked
- Professional recommendation widget

**Gold Tier:**
- Sophisticated ML model
- Real-time personalization
- High conversion rate demonstrated
- "This actually feels personalized"

**Demo Script (30 seconds):**
1. Show recommendation engine dashboard
2. Display recommendations for "user type A" (budget traveler)
3. Switch to "user type B" (business traveler) → different recs
4. Simulate user clicking rec → show booking
5. Display metrics (click-through rate, conversion)
6. Explain ML model and multi-agent strategy

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Recommendations

**Q1-Q2 (Foundation building):** **Parallel Execution** ⚡
- Agent 1: User profiling service (track behavior, store preferences)
- Agent 2: Recommendation engine (ML algorithms, scoring)
- Agent 3: Analytics dashboard (metrics, A/B testing)
- **Why:** Fastest way to get working end-to-end personalization
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Polish & features):** **Iterative Refinement** ✨
- Agent 1: Add new features (upselling, multi-item recs)
- Agent 2: Review and improve ML model quality
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples

**Q5+ (Complex features):** **Specialist Roles** 🎯
- ML Agent: Owns all recommendation algorithms across quarters
- Data Agent: Owns all user profiling and tracking across quarters
- Analytics Agent: Validates quality and finds optimization opportunities
- **Why:** Context retention, domain expertise
- See TUTORIAL.md "Pattern 3: Specialist Roles" for details

### Role-Specific Tips

**Keep ML separate from data engineering:**
One agent focuses on algorithms and models while another handles data collection and user profiling. Cleaner separation of concerns.

**Start simple, add complexity later:**
Begin with rule-based recommendations in Q1-Q2, add ML in Q3-Q4. Prompt agents: "Build simple rule-based system first, we'll add ML later."

**Demo-first thinking:**
Structure agents around what you'll show: "Agent 1 builds user segmentation I'll display, Agent 2 builds different recommendations per segment, Agent 3 builds metrics dashboard."

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (Example scenarios)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Recommendations-Specific Challenges

**"Don't have real user data to train on"**
- **Solution:** Generate synthetic data with realistic patterns
- Agent prompt: "Generate 100 sample users with diverse profiles, 500 search events, 200 bookings. Make patterns realistic - business travelers prefer morning flights, budget travelers prefer cheapest options."
- Quick win: Create 3-5 user archetypes with distinct behavior patterns

**"Cold start problem - new users have no history"**
- **Solution:** Implement fallback strategies
- Agent prompt: "Handle new users: 1) Show trending/popular flights, 2) Ask basic preferences upfront (business or leisure?), 3) Use demographic data, 4) Switch to personalized after 3 interactions"
- Common issue: Forgetting to handle the zero-data case

**"Recommendations aren't actually personalized"**
- **Solution:** Test with distinct user segments
- Create test users: "Budget traveler searches only economy under $200", "Business traveler only morning flights, premium seats"
- Verify recommendations differ significantly between segments
- Use agent to validate: "Check that business and leisure users get <30% overlapping recommendations"

**"Can't measure if recommendations are working"**
- **Solution:** Define clear metrics and track them
- Agent prompt: "Implement metrics: CTR (clicks/impressions), conversion rate (bookings/clicks), revenue per user, recommendation diversity score. Create dashboard showing these metrics."
- Quick win: Even with mock data, demonstrate how metrics would be tracked

**"A/B testing is too complex"**
- **Solution:** Start with simple variant comparison
- Agent prompt: "Create 2 variants: A) popularity-based recs, B) personalized recs. Randomly assign users. Track which performs better. Don't need statistical significance - just show the concept."
- Or skip A/B in Q1-Q2, add in Q3-Q4 when foundation is solid

---

## TECH STACK SUGGESTIONS

### Option A: Python ML Stack (Recommended)
- **Backend:** Flask or FastAPI
- **ML:** scikit-learn, pandas
- **Database:** SQLite for user data
- **Visualization:** Chart.js for analytics
- **Why:** Python excels at ML and data processing

### Option B: JavaScript Full Stack
- **Backend:** Express.js
- **ML:** TensorFlow.js or simple algorithms
- **Database:** MongoDB
- **Why:** JavaScript everywhere, quick prototyping

### Option C: Simple Rule-Based (Fast Track)
- **Backend:** Any (Flask, Express)
- **ML:** None - use IF/THEN rules
- **Database:** JSON files
- **Why:** Focus on business logic, not ML complexity

**Pro tip:** Start with simple rule-based recommendations Q1-Q2, add ML in Q3-Q4 when you understand the domain better. Learning ML + learning multi-agent = too much for 30 minutes.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research recommendation algorithms
- Define user segmentation strategy
- Create vision doc with ML approach
- **Success = clear strategy and plan for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on personalization "wow factor"
- Show different users get different recommendations
- **Success = impressive demo showing AI/ML differentiation**

### Q3: Integration & Features (60 min)
- Add 2-3 significant features (upselling, A/B testing)
- Better ML model or algorithms
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete end-to-end personalization flow
- Explainable AI (show reasoning)
- Real-time recommendations
- Professional analytics dashboard
- **Success = production-ready recommendation platform, ready to launch!**

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

### With Booking Portal
- Embed recommendation widget in their UI
- Track which recommendations lead to bookings

### With Flight Inventory
- Only recommend available flights
- Consider seat availability in scoring

### With Pricing
- Factor in dynamic prices
- Recommend high-margin flights

### With Customer Data
- Access real user profiles and history
- Or generate synthetic user data

**Remember:** Integration is bonus points, not required. Focus on your own system first.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Recommendations are clearly personalized per user segment
- ✅ Can explain why each recommendation was made
- ✅ Metrics show recommendation effectiveness (CTR, conversion)
- ✅ ML model or algorithm is sophisticated and well-designed
- ✅ Multi-agent strategy is clear and effective
- ✅ UI makes recommendations feel helpful, not spammy

### Red Flags to Avoid
- ❌ Same recommendations for every user
- ❌ Recommending sold-out or irrelevant flights
- ❌ No way to measure if recommendations work
- ❌ Overly complex ML that doesn't perform
- ❌ Creepy personalization that feels invasive
- ❌ Same demo every quarter with no evolution

---

## QUICK START GUIDE

### Before Game Day
- Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) - Learn to think like a director
- Read [TUTORIAL.md](../TUTORIAL.md) - Multi-agent patterns
- Bookmark TUTORIAL.md "Quick Reference" for prompt templates

### Quarter 1: Research & Vision (60 min)

**First 10 minutes:**
1. Decide: What will I deliver? (Vision doc? ML design? MVP?)
2. Plan your agent strategy: Which agents for which tasks?
3. Start Agent 1 (Data Scientist): Begin research on recommendation algorithms

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research recommendation algorithms and approaches
- Agent 2: Define user segmentation strategy
- Agent 3: Design ML architecture and evaluation metrics

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision
2. Decide which 1-2 services to build
3. Start Agent 1 (ML Engineer): Build recommendation engine

**Minutes 5-50:**
Build your investor demo:
- Agents build services based on Q1 architecture
- Focus on personalization and business impact
- Test with different user segments

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to answer investor questions about ML approach

### Quarters 3-6: Execute & Adapt

**Each quarter:**
1. Listen to gamerunner scenario
2. Decide: What agents do I need?
3. Build/fix quickly
4. Demo at end

**Between quarters:**
- Reflect: What worked? What didn't?
- Review TUTORIAL.md for new techniques
- Plan: How will I improve ML model next quarter?

---

## PARTING WISDOM

> "You have 30 minutes to build what normally takes 3 hours. Your secret weapon is coordinating 2-3 agents efficiently. The agent that builds the ML model doesn't have to be the agent that builds the analytics dashboard. Assembly line > single artisan."

Good luck, Director. The company's growth is in your algorithms. 🎯✨

---

## APPENDIX: DETAILED MULTI-AGENT STRATEGIES

### Strategy 1: Data + Model + UI (Recommended for Q1)
**When to use:** Building complete recommendation system

```
Agent 1 (Data Engineer):
"Generate synthetic user behavior data:
- 100 sample users with profiles (age, income, travel_frequency)
- 500 search events (user_id, searched_route, date, booked: yes/no)
- 200 booking events (user_id, route, price, seat_class)

Create user segmentation:
- Budget travelers: price sensitive, economy only
- Business travelers: time sensitive, premium preferred
- Leisure travelers: flexible dates, destination focused

Store in SQLite, create API:
- GET /users/{id}/profile
- GET /users/{id}/history
- POST /users/{id}/events (track behavior)"

Agent 2 (ML Engineer):
"Build recommendation engine using Agent 1's data:

Algorithm 1: Collaborative Filtering
- Find similar users based on booking history
- Recommend what similar users booked

Algorithm 2: Content-Based
- For business travelers → recommend business-heavy routes
- For leisure → recommend tourist destinations
- For budget → recommend cheapest options

API:
- POST /recommend (user_id) → returns top 5 flight recommendations
- Each recommendation has score and reason"

Agent 3 (Frontend):
"Build recommendation widget using Agent 2's API:
- 'Recommended for You' section
- Display 5 flight recommendations with prices
- Show reason (e.g., 'Popular with business travelers like you')
- Click to view details
- Track clicks for analytics

Use simple HTML/CSS/JavaScript."
```

**Timeline:**
- Min 0-10: Agent 1 generates data
- Min 10-20: Agent 2 builds model
- Min 20-25: Agent 3 creates UI

---

### Strategy 2: Experimentation Platform (Recommended for Q2-Q3)
**When to use:** Testing different recommendation strategies

```
Agent 1 (A/B Test Framework):
"Build A/B testing system for recommendations:
- Variant A: Popularity-based (most booked flights)
- Variant B: Personalized ML-based
- Variant C: Cheapest flights

Randomly assign users to variants.
Track: clicks, bookings, revenue per variant.

API:
- GET /recommend/{user_id} (returns rec based on variant)
- GET /experiments/results (shows performance by variant)"

Agent 2 (Analytics):
"Analyze A/B test results:
- Click-through rate by variant
- Conversion rate by variant
- Revenue per user by variant
- Statistical significance calculator

Create dashboard showing which variant performs best."

Agent 3 (Winner Implementation):
"Take the winning variant from Agent 2's analysis.
Implement it as the production recommendation system.
Add refinements based on learnings.
Create final analytics dashboard."
```

---

### Strategy 3: Upselling Engine (Recommended for Q3-Q4)
**When to use:** Maximizing revenue per booking

```
Agent 1 (Upsell Detector):
"Build upselling opportunity detector:

For each booking, calculate:
- Likelihood to upgrade seat (based on user income, past behavior)
- Likelihood to buy baggage (based on trip length, destination)
- Likelihood to buy insurance (based on price, international vs domestic)

Score each opportunity 0-100.

API: POST /upsell/opportunities (booking_data) → returns ranked upsell suggestions"

Agent 2 (Upsell UI):
"Create upsell components:
- Premium seat upgrade offer (show benefit, price difference)
- Baggage add-on widget
- Insurance recommendation
- Bundle deals

Personalize messaging based on user segment.
Example: 'Business travelers like you choose premium seats 73% of the time'"

Agent 3 (Revenue Analytics):
"Track upsell performance:
- Upsell conversion rate
- Average order value increase
- Revenue attribution by upsell type
- User segment response rates

Create executive dashboard showing upsell impact."
```

---

### Strategy 4: Explainable Recommendations (Recommended for Q4)
**When to use:** Need transparency and trust

```
Agent 1 (Reason Generator):
"For each recommendation, generate human-readable explanation:

Examples:
- 'Popular with business travelers from your company'
- 'You searched for beach destinations - Cancun is trending'
- 'Based on your budget preference, this flight is 30% cheaper'
- 'You previously booked similar routes in spring'

Create explanation templates for each recommendation type.
API adds 'reason' field to each recommendation."

Agent 2 (Preference Learning):
"Build explicit preference collector:
- Ask users: prefer window or aisle?
- Ask: usually travel for business or leisure?
- Ask: prefer direct flights or cheapest option?

Store preferences, use in recommendations.
Show how preferences affect recommendations."

Agent 3 (Recommendation Dashboard):
"Create user-facing dashboard:
- 'Why am I seeing this?' explanation
- Preference manager (update your preferences)
- Recommendation quality feedback (thumbs up/down)
- Alternative recommendations

Make the algorithm transparent and trustworthy."
```
