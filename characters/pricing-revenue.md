# DIRECTOR OF PRICING & REVENUE OPTIMIZATION
## Character Sheet

---

## YOUR ROLE

You are the **Director of Pricing & Revenue Optimization** at SkywardAI - the money-maker who turns seats into profit.

**Department:** Finance - Analytics & ML
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** Chief Financial Officer

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Maximize revenue per seat without losing customers to competitors."**

You balance the art and science of pricing: charge too much and customers flee to competitors; charge too little and you leave money on the table. Your algorithms determine whether the company thrives or barely breaks even.

### What Drives You
- **Revenue maximization:** Every flight should generate optimal yield
- **Competitive intelligence:** Always know what competitors charge
- **Data-driven decisions:** Analytics and models guide pricing
- **Dynamic optimization:** Prices adjust in real-time to demand

### What Keeps You Up at Night
- Competitors undercutting your prices
- Leaving revenue on the table (sold out too early at low prices)
- Unsold seats on departure day (should've dropped prices sooner)
- Pricing too high and seeing bookings plummet

---

## CHARACTER FLAVOR

You're the **analytical optimizer** - you see everything through the lens of revenue and margins.

**Your mantras:**
- "Price is what you pay, value is what you get"
- "Data doesn't lie, intuition does"
- "Optimize for the 90th percentile, not the average"
- "Every dollar left on the table is a dollar we'll never see"

**In board meetings, you say:**
- "Dynamic pricing increased revenue per seat by 18%"
- "Our average price is $247, industry average is $231"
- "Price elasticity on business travel is 0.3"
- "Revenue forecast for next quarter: $12.4M"

**Your personality:**
- Quantitative, analytical, competitive
- Love graphs and dashboards
- Always talking about "maximizing yield"
- The person who says "but what's the ROI?"

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Dynamic Pricing Engine**
- **Purpose:** Calculate optimal prices based on demand, competition, inventory levels, and time-to-departure
- **Key Decisions:**
  - Pricing algorithms (rule-based vs ML-based vs hybrid)
  - Update frequency (real-time vs batch)
  - Handling edge cases (sold out flights, competitor blackouts, special events)
  - Price bounds and safety limits
- **Integration:** Consumes inventory data and competitor prices, provides prices to booking system
- **Team:** 1-2 agents with data science focus

**Service 2: Revenue Analytics & Forecasting**
- **Purpose:** Track revenue metrics, forecast demand, analyze pricing performance
- **Key Decisions:**
  - Which metrics matter (yield per seat, load factor, revenue per flight, competitive index)
  - Forecasting approach (historical trends vs predictive models)
  - Reporting granularity (per route, per day, per cabin class)
  - Alert thresholds (when to notify about pricing issues)
- **Integration:** Consumes booking data and pricing history, provides insights to executives and pricing engine
- **Team:** 1-2 agents with analytics focus

**Service 3: Competitor Intelligence & Monitoring**
- **Purpose:** Track competitor pricing, visualize market position, simulate scenarios
- **Key Decisions:**
  - Data collection strategy (scraping vs APIs vs manual input)
  - Competitor response modeling (how competitors react to our prices)
  - Visualization priorities (price comparison, market share, trend analysis)
  - Scenario planning tools (what-if simulators for pricing strategies)
- **Integration:** Provides competitor data to pricing engine, displays insights for strategic decisions
- **Team:** 1-2 agents with frontend and data visualization focus

**Why Multiple Services?**
- ✅ Each agent team has focused responsibility
- ✅ Services can be built in parallel
- ✅ Easy to demo incrementally (Service 1 in Q1, add Service 2 in Q2, etc.)
- ✅ Realistic microservices practice
- ✅ Clear separation of concerns (pricing logic, analytics, intelligence)

**Director Tip:** You and your agent teams will decide the specific tech stack and implementation details in Q1. Focus on WHAT each service does and WHY it matters, not HOW to build it yet.

📚 **For detailed multi-service patterns:** See [MULTI-SERVICE-GUIDE.md](../MULTI-SERVICE-GUIDE.md)

---

## WHAT YOU'LL BUILD

### Quarter 1: Research & Vision (45-60 min)
**Focus:** Strategy, research, and planning - NOT working code yet

**Your Objectives:**
- Research dynamic pricing strategies (airlines, hotels, ride-sharing)
- Analyze competitor pricing approaches and revenue models
- Design pricing algorithms and optimization framework
- Plan your 2-3 service architecture (Pricing Engine, Analytics, Intelligence)
- Make key architectural decisions with your agent teams

**Key Strategic Decisions to Make:**
- **Pricing Philosophy:** Simple rules vs ML-driven vs hybrid approach?
- **Service Boundaries:** Which service owns what responsibilities?
- **Data Strategy:** What data do you need and where will it come from?
- **Integration Points:** Which other departments do you need to connect with?
- **Tech Stack:** What technologies best support your pricing strategy?

**Deliverable Options:**
- Vision document with pricing strategy and architecture diagram
- Pricing algorithm design with mathematical models and business rationale
- Service architecture plan showing purpose, decisions, and integration points
- Simple MVP (if time permits) to validate core concepts

**Agent Roles to Use:**
- **Business Analyst:** Research pricing models and revenue optimization strategies
- **Data Scientist:** Design pricing algorithms and demand forecasting models
- **Technical Architect:** Design service architecture and data flows

**Example Strategic Questions to Explore:**
- How do airlines balance revenue maximization with competitive positioning?
- What factors most influence optimal pricing (time, demand, competition)?
- Should we start simple and add ML later, or build ML-first?
- How frequently should prices update (real-time vs periodic batches)?
- What safety mechanisms prevent pricing disasters (too high/low)?

**Demo:** Present your vision doc, pricing strategy, and architectural decisions. Explain what you'll build in Q2-Q4 and WHY these choices support revenue optimization.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable pricing system that demonstrates intelligent optimization
- Show sophisticated logic investors want to see (your "secret sauce")
- Focus on visual impact and clear business value

**Key Director Decisions:**
- **What to Build First:** Which service makes the strongest investor impression?
- **Depth vs Breadth:** One sophisticated service or two simpler ones?
- **Demo Strategy:** What sequence of actions shows off your pricing intelligence?
- **IP Showcase:** How do you demonstrate your unique optimization approach?

**Deliverable:**
- Working pricing engine with dynamic calculations OR
- Impressive analytics dashboard showing revenue optimization OR
- Integrated demo showing pricing + analytics working together
- Clear demonstration of "smart" pricing that outperforms static pricing

**What Investors Want to See:**
- **Sophisticated Logic:** "Our algorithm considers X factors in real-time..."
- **Business Impact:** "This increases revenue per seat by Y%..."
- **Competitive Edge:** "Unlike competitors who use static pricing, we..."
- **Scalability:** "This architecture can handle Z routes/transactions..."

**Agent Roles to Use:**
- **Implementation Agents:** Build the services based on Q1 architecture decisions
- **Specialist Agents:** Implement specific algorithms or visualizations
- **Polish Agents:** Refine the demo flow and user experience

**Demo:** Live demo of pricing system to "investors" (gamerunner + other directors). Show the pricing intelligence, explain the business value, and demonstrate clear competitive advantage.

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add ML-based demand forecasting or competitor analysis
- Improve pricing algorithms with multi-factor optimization
- Optional: Integrate with other directors' systems (inventory, booking)
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced pricing system with 2-3 new features
- More sophisticated optimization logic
- Better analytics and insights

**Gamerunner May Introduce:**
- "Competitor started price war - respond!"
- "Regulatory requirement: price transparency audit"
- "Premium cabin pricing strategy needed"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete multi-factor pricing optimization
- Real-time price updates and monitoring
- Scenario simulator for strategic planning
- Executive-level analytics dashboard
- Final polish on algorithms and visualizations

**Deliverable:**
- Production-ready revenue optimization system
- Complete pricing workflow from inputs to recommendations
- Professional analytics and reporting

**Demo:** Full pricing system demonstration from data inputs to optimized prices. Company launches! 🎉

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Can set/view prices by route
- Basic price calculator
- Simple revenue report
- Price changes are visible

**Silver Tier:**
- Prices adjust based on rules (time, demand)
- Interactive pricing dashboard
- Charts showing revenue trends
- Clean data visualization

**Gold Tier:**
- Sophisticated ML pricing
- Real-time optimization
- Beautiful analytics dashboards
- "This looks like airline industry software"

**Demo Script (30 seconds):**
1. Show pricing dashboard
2. Display price for a route (e.g., SFO-LAX: $199)
3. Simulate demand increase → price adjusts to $249
4. Show revenue impact chart
5. Display competitor comparison
6. Explain pricing algorithm and multi-agent strategy

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Pricing & Revenue

**Q1 (Research & Vision):** **Sequential Strategy Development**
- Agent 1: Research pricing strategies and industry best practices
- Agent 2: Design algorithms based on research findings
- Agent 3: Architect services based on algorithm requirements
- **Why:** Each agent builds on the previous agent's work to create coherent strategy
- See TUTORIAL.md "Pattern 2: Sequential Pipeline" for detailed example

**Q2 (Foundation Building):** **Parallel Execution** ⚡
- Multiple agent teams build different services simultaneously
- Each team focuses on one service (pricing engine, analytics, intelligence)
- **Why:** Fastest way to get working end-to-end pricing system
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Optimization & ML):** **Iterative Refinement** ✨
- Agents enhance existing services with advanced features
- Focus on optimization, ML models, and sophisticated analytics
- **Why:** Build on existing foundation, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples


### Role-Specific Tips

**Separate strategy from implementation:**
Use one agent to make strategic decisions (algorithm choice, pricing philosophy) and different agents to implement those decisions. Keeps decision rationale clear.

**Think demo-first:**
Structure your agent teams around what you'll demonstrate: "Team 1 builds the core pricing intelligence, Team 2 builds the analytics that prove it works, Team 3 builds the interface that shows it off."

**Focus agents on outcomes, not technologies:**
Instead of "Build a FastAPI service," say "Build a service that calculates optimal prices based on these factors." Let agents recommend technology based on requirements.

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (analytics and API examples)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Pricing & Revenue-Specific Challenges

**"Too many pricing factors to consider - algorithm is overwhelming"**
- **Director Decision:** Start with 2-3 core factors, add complexity incrementally
- **Strategic Approach:** Identify which factors have the biggest revenue impact (time-to-departure, demand) and build those first
- **Agent Strategy:** One agent designs simple model, another agent later enhances with additional factors
- **Success Indicator:** Can explain pricing logic in 30 seconds to investors

**"Should prices update in real-time or periodically?"**
- **Director Decision:** Consider trade-offs between responsiveness and system complexity
- **Strategic Approach:** Start with periodic updates (every 5-15 minutes), add real-time if needed
- **Agent Strategy:** Build with update frequency as a configurable parameter, not hardcoded
- **Success Indicator:** Prices respond to market changes fast enough to capture revenue opportunities

**"Don't know the mathematical models for revenue optimization"**
- **Director Decision:** Let agents research and propose approaches, then you decide
- **Strategic Approach:** Start with simple, explainable models before adding ML complexity
- **Agent Strategy:** Research agent finds industry approaches, design agent proposes model, you approve
- **Success Indicator:** Can explain the pricing model and justify why it maximizes revenue

**"How to get competitor pricing data?"**
- **Director Decision:** Mock data vs real integration - what's good enough for demo?
- **Strategic Approach:** Start with realistic mock data, design clear interface for future real data
- **Agent Strategy:** Agent creates mock competitor API that other services consume
- **Success Indicator:** Demo shows competitive intelligence without dependency on external data

**"Which revenue metrics actually matter?"**
- **Director Decision:** Define 3-5 key metrics that tell the revenue story
- **Strategic Approach:** Align metrics with business goals (revenue per seat, load factor, competitive index)
- **Agent Strategy:** Analytics agent implements metrics you define, visualization agent makes them clear
- **Success Indicator:** Dashboard answers "Are we making money?" at a glance

---

## TECH STACK CONSIDERATIONS

As a director, you'll work with your agent teams in Q1 to decide on the technology stack. Here are key considerations:

### What to Think About
- **Analytics Capability:** You need strong data manipulation and statistical analysis
- **Visualization Quality:** Professional charts and dashboards matter for credibility
- **Performance:** Pricing calculations may need to run frequently or in real-time
- **Data Storage:** Price history, competitor data, and forecasts need persistence
- **Integration:** How will your services communicate with each other and other departments?

### Common Approaches
- **Python-centric:** Strong analytics libraries (pandas, numpy), good ML support, easy visualization
- **JavaScript full-stack:** Unified language across services, rich frontend ecosystem
- **Hybrid:** Python for heavy analytics, JavaScript for dashboards and APIs
- **Spreadsheet integration:** Executives often want Excel exports for scenario planning

**Director Decision Point:** In Q1, work with your agents to evaluate these trade-offs based on your strategy. What matters most - sophisticated ML, beautiful visualizations, or rapid prototyping?

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research pricing strategies and revenue optimization
- Design pricing algorithms and models
- Define your service architecture
- **Success = clear strategy and pricing model design for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on sophisticated algorithms and visualizations
- Dynamic pricing demonstration
- **Success = impressive demo showing intelligent optimization**

### Q3: Integration & Features (60 min)
- Add 2-3 significant features (ML, competitor analysis, forecasting)
- Better optimization logic
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete multi-factor optimization
- Real-time price updates
- Scenario simulator
- Executive dashboard polish
- **Success = production-ready revenue optimization system!**

---

## INTEGRATION POINTS (OPTIONAL)

Work independently with mock data, or integrate:

### With Inventory
- Get current booking data
- Use availability in pricing

### With Booking Portal
- Provide current prices
- Update prices in real-time

### With Marketing
- Coordinate on promotional pricing
- Share revenue impact data

**Mock it:** Create sample data that looks realistic. You don't need real integration to demo pricing algorithms.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Pricing algorithm is sophisticated and explainable
- ✅ Dashboard shows clear revenue analytics
- ✅ Prices respond intelligently to market conditions
- ✅ Charts and visualizations are professional
- ✅ Multi-agent strategy is clear and effective
- ✅ You improve and add features each quarter
- ✅ Revenue optimization is demonstrable

### Red Flags to Avoid
- ❌ Static prices that never change
- ❌ Pricing formula that doesn't make business sense
- ❌ No visualization (just API responses)
- ❌ Overly complex ML that doesn't work
- ❌ Can't explain why prices are what they are
- ❌ Same demo every quarter with no evolution

---

## QUICK START GUIDE

### Before Game Day
- Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) - Learn to think like a director
- Read [TUTORIAL.md](../TUTORIAL.md) - Multi-agent patterns
- Bookmark TUTORIAL.md "Quick Reference" for prompt templates

### Quarter 1: Research & Vision (60 min)

**First 10 minutes:**
1. Decide: What will I deliver? (Vision doc? Algorithm design? MVP?)
2. Plan your agent strategy: Which agents for which tasks?
3. Identify key strategic decisions to make this quarter
4. Start Agent 1: Begin research or initial architecture exploration

**Minutes 10-50:**
Use agents to inform your strategic decisions:
- Research dynamic pricing strategies and revenue optimization approaches
- Design pricing algorithms and mathematical models
- Evaluate technology options for your services
- Map out service architecture and integration points
- Make key decisions on pricing philosophy and approach

**Last 10 minutes:**
1. Compile vision document with your strategic decisions
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy and rationale

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision and strategic decisions
2. Decide which 1-2 services to build first for maximum investor impact
3. Define what "success" looks like for the demo
4. Start your first agent team on the priority service

**Minutes 5-50:**
Build your investor demo:
- Agent teams implement services based on Q1 architecture
- Focus on what impresses investors (sophisticated logic, clear value)
- Test and refine the demo flow
- Ensure the pricing "intelligence" is visible and understandable

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo narrative
3. Prepare to answer questions about your approach and competitive advantage

### Quarter 3 & Beyond: Execute & Adapt

**Each quarter:**
1. Listen to gamerunner scenario
2. Decide: What agents do I need?
3. Build/optimize quickly
4. Demo at end

**Between quarters:**
- Reflect: What worked? What didn't?
- Review TUTORIAL.md for new techniques
- Plan: How will I improve next quarter?

---

## PARTING WISDOM

> "You're not here to code pricing algorithms - you're here to make strategic decisions about how pricing should work, then orchestrate agent teams to build it. The best directors know WHAT they want (maximize revenue through intelligent pricing) and WHY it matters (competitive advantage), but let their teams figure out HOW. Your job is vision and decisions, not implementation details."

> "In Q1, decide your pricing philosophy and architecture. In Q2-Q4, your agent teams bring that vision to life while you make course corrections and strategic pivots. The agent that researches pricing strategies doesn't have to be the agent that implements the algorithm. The agent that builds the pricing engine doesn't have to be the agent that visualizes the results. Think like a director, delegate like a pro."

Good luck, Director. The company's profitability is in your hands. 💰📈
