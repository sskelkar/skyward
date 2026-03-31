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

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate service.

### Multi-Service Architecture

Your recommendation system needs multiple services working together. You'll work with your agent teams in Q1 to figure out the technical approach.

**Service 1: Recommendation Engine** (Agent Team A)
- **Purpose:** Generate personalized flight and destination recommendations
- **Key Decisions:**
  - Simple rule-based vs ML-based recommendations
  - What signals to use (search history, bookings, demographics)
  - How to score and rank recommendations
  - Cold start problem (new users with no history)
- **Integration:** Consumes user data, provides recommendations to frontend
- **Team:** 1-2 ML/backend agents

**Service 2: User Profiling** (Agent Team B)
- **Purpose:** Track user behavior, build preference models, segment users
- **Key Decisions:**
  - What user actions to track (searches, clicks, bookings)
  - How to segment users (business vs leisure, budget vs premium)
  - Privacy considerations for data collection
  - How long to retain user history
- **Integration:** Provides user data to recommendation engine
- **Team:** 1-2 data/backend agents

**Service 3: Analytics Dashboard** (Agent Team C)
- **Purpose:** Measure recommendation effectiveness, run A/B tests
- **Key Decisions:**
  - What metrics matter (CTR, conversion, revenue per user)
  - How to visualize recommendation performance
  - A/B testing framework design
  - Real-time vs batch analytics
- **Integration:** Consumes recommendation and booking data, displays insights
- **Team:** 1-2 frontend/analytics agents

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

**Example Approach:**
```
Work with your data scientist agent to research:
- What recommendation approaches exist? (collaborative filtering, content-based, hybrid)
- What are the tradeoffs of each approach?
- How do we handle new users with no history (cold start problem)?
- What signals should we use to personalize? (search history, bookings, demographics)

Work with your product manager agent to define:
- User segmentation strategy (business vs leisure, budget vs premium)
- Success metrics (CTR, conversion rate, revenue impact)
- What "good personalization" looks like

Work with your architect agent to design:
- What services do we need and how do they interact?
- Where does recommendation logic live vs user data vs analytics?
- Integration points with other departments (optional vs required)
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
- Work with your data team to create test users with distinct behavior patterns
- Key decision: How many user archetypes do you need? (3-5 is usually enough for demos)
- Make patterns realistic: business travelers behave differently than leisure travelers

**"Cold start problem - new users have no history"**
- **Solution:** Implement fallback strategies
- Key decisions: Show popular/trending flights? Ask preferences upfront? Use demographics?
- When to switch from generic to personalized? (after 3 interactions? after first booking?)
- Common issue: Forgetting to handle the zero-data case

**"Recommendations aren't actually personalized"**
- **Solution:** Test with distinct user segments
- Create test users with very different profiles (budget vs premium, business vs leisure)
- Verify recommendations differ significantly between segments
- Key question: What % overlap is acceptable between different user types?

**"Can't measure if recommendations are working"**
- **Solution:** Define clear metrics and track them
- Key metrics to consider: CTR (clicks/impressions), conversion rate (bookings/clicks), revenue per user, recommendation diversity
- Even with mock data, demonstrate how metrics would be tracked
- Focus on metrics that show business impact

**"A/B testing is too complex"**
- **Solution:** Start with simple variant comparison
- Key decision: What variants to test? (popularity-based vs personalized? different algorithms?)
- Don't need statistical significance for demos - just show the concept
- Or skip A/B in Q1-Q2, add in Q3-Q4 when foundation is solid

---

## TECHNICAL APPROACH

**You and your agent teams will figure out the tech stack in Q1.** Focus on business value and architecture decisions, not specific technologies.

### Key Technical Decisions to Make with Your Teams

**Recommendation Approach:**
- Simple rule-based (IF business traveler THEN morning flights) vs ML-based
- Start simple and add complexity, or build ML from the start?
- How sophisticated should your algorithms be for the demo?

**Data Strategy:**
- Real user data vs synthetic/mock data for development
- What user signals to track (clicks, searches, bookings, time spent)
- User privacy and data retention policies

**Integration Strategy:**
- Standalone system with mock data, or integrate with other departments?
- Real-time recommendations vs batch processing
- API design for other services to consume your recommendations

**Measurement:**
- What metrics prove your recommendations work?
- How to demonstrate business impact in demos?
- A/B testing framework needed or not?

**Pro tip:** Start with simple rule-based recommendations Q1-Q2, add ML in Q3-Q4 when you understand the domain better. Focus on demonstrating personalization and business impact first, sophistication second.

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
2. Plan your agent strategy: Which agents for which research tasks?
3. Start your first agent team on initial research

**Minutes 10-50:**
Use agents for research and planning:
- Research recommendation approaches and tradeoffs
- Define user segmentation and personalization strategy
- Design service architecture and key decision points
- Plan metrics and evaluation approach

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy and key decisions

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision
2. Decide which 1-2 services to build first
3. Start your agent teams building in parallel

**Minutes 5-50:**
Build your investor demo:
- Agent teams build services based on Q1 architecture
- Focus on demonstrating clear personalization (User A sees X, User B sees Y)
- Show business impact metrics
- Test with different user segments

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo (show personalization, explain approach)
3. Prepare to answer questions about your recommendation strategy and technical decisions

### Quarter 3 & Beyond: Execute & Adapt

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

## APPENDIX: MULTI-AGENT ARCHITECTURE PATTERNS

### Strategy 1: Data + Model + UI (Recommended for Q1)
**When to use:** Building complete recommendation system from scratch

**Agent Team Structure:**
- **Agent 1 (Data Engineer):** User profiling service
  - What to build: User behavior tracking, preference storage, segmentation
  - Key decisions: What data to collect, how to segment users, privacy approach
  - Deliverable: Service that provides user profiles and history

- **Agent 2 (ML Engineer):** Recommendation engine
  - What to build: Recommendation algorithm/model, scoring system
  - Key decisions: Rule-based vs ML, what signals to prioritize, cold start handling
  - Deliverable: Service that generates personalized recommendations

- **Agent 3 (Frontend):** Recommendation UI
  - What to build: Display recommendations, track user interactions
  - Key decisions: How to present recommendations, what context to show, mobile vs desktop
  - Deliverable: User interface showing personalized recommendations

**Parallel execution timeline:**
- Min 0-15: All agents start building their services simultaneously
- Min 15-25: Integration and testing
- Min 25-30: Demo preparation

---

### Strategy 2: Experimentation Platform (Recommended for Q2-Q3)
**When to use:** Testing different recommendation strategies

**Agent Team Structure:**
- **Agent 1 (A/B Test Framework):** Experimentation system
  - What to build: Multiple recommendation variants, user assignment, tracking
  - Key decisions: What variants to test, how to split traffic, when to declare winner
  - Deliverable: Framework for running recommendation experiments

- **Agent 2 (Analytics):** Performance measurement
  - What to build: Metrics dashboard, variant comparison, statistical analysis
  - Key decisions: What metrics prove success, how to visualize results
  - Deliverable: Dashboard showing which recommendation approach wins

- **Agent 3 (Winner Implementation):** Production rollout
  - What to build: Production recommendation system based on winning variant
  - Key decisions: How to gradually roll out, monitoring approach
  - Deliverable: Refined recommendation service ready for launch

---

### Strategy 3: Upselling Engine (Recommended for Q3-Q4)
**When to use:** Maximizing revenue per booking

**Agent Team Structure:**
- **Agent 1 (Upsell Intelligence):** Opportunity detection
  - What to build: System that identifies upsell opportunities (seat upgrades, baggage, insurance)
  - Key decisions: What products to recommend, how to score likelihood, personalization approach
  - Deliverable: Service that suggests revenue-maximizing add-ons

- **Agent 2 (Upsell UI):** Presentation layer
  - What to build: Compelling upsell offers, personalized messaging
  - Key decisions: When to show offers, how aggressive to be, mobile vs desktop
  - Deliverable: UI components for upselling

- **Agent 3 (Revenue Analytics):** Impact measurement
  - What to build: Track upsell conversion and revenue impact
  - Key decisions: What metrics matter, how to attribute revenue, ROI calculation
  - Deliverable: Dashboard showing upsell business impact

---

### Strategy 4: Explainable Recommendations (Recommended for Q4)
**When to use:** Building trust and transparency

**Agent Team Structure:**
- **Agent 1 (Explanation Generator):** Recommendation reasoning
  - What to build: Human-readable explanations for each recommendation
  - Key decisions: Level of detail, what reasoning to expose, personalization
  - Deliverable: Service that explains why each recommendation was made

- **Agent 2 (Preference Manager):** User control
  - What to build: Interface for users to set/update preferences
  - Key decisions: What preferences to expose, how much control to give users
  - Deliverable: Preference management system

- **Agent 3 (Feedback Loop):** Quality improvement
  - What to build: User feedback collection (thumbs up/down), recommendation refinement
  - Key decisions: How to collect feedback, how to use it to improve recommendations
  - Deliverable: System that learns from user feedback
