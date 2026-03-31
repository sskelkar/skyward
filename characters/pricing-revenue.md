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

**Service 1: Pricing Engine API** (Agent Team A)
- Tech: FastAPI/Flask backend
- Port: 5003
- Purpose: Dynamic pricing calculations, price optimization algorithms
- Team: 1-2 backend agents (data science focus)

**Service 2: Revenue Analytics API** (Agent Team B)
- Tech: FastAPI/Flask backend
- Port: 5004
- Purpose: Revenue metrics, forecasting, competitor analysis
- Team: 1-2 analytics agents

**Service 3: Competitor Monitor Dashboard** (Agent Team C)
- Tech: React/Vue/vanilla JS frontend
- Port: 3001
- Purpose: Price visualization, competitor tracking, scenario simulator
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
- Research dynamic pricing strategies (airlines, hotels, ride-sharing)
- Analyze competitor pricing approaches and revenue models
- Design pricing algorithms and optimization framework
- Plan your 2-3 service architecture (Pricing Engine, Analytics, Dashboard)

**Deliverable Options:**
- Vision document with pricing strategy and architecture diagram
- Pricing algorithm design with mathematical models
- Simple MVP (if time permits) - basic pricing calculator

**Agent Roles to Use:**
- **Business Analyst:** Research pricing models and revenue optimization strategies
- **Data Scientist:** Design pricing algorithms and demand forecasting models
- **Technical Architect:** Design service architecture and data flows

**Example Prompt:**
```
"You are a data scientist specializing in airline revenue management.

Research dynamic pricing strategies used by major airlines.
Design a pricing algorithm that considers:
1. Time to departure (advance purchase curves)
2. Current demand (booking pace)
3. Competitor prices
4. Seasonality and events

Create a mathematical model with formulas and parameters."
```

**Demo:** Present your vision doc, pricing models, or MVP. Explain your strategy and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable pricing system (with intelligent price adjustments)
- Build revenue dashboard with professional visualizations
- Focus on what investors want to see: sophisticated optimization

**Deliverable:**
- Working pricing engine with dynamic calculations OR
- Impressive analytics dashboard showing revenue optimization
- Clear demonstration of "smart" pricing in action

**Agent Roles to Use:**
- **Backend Developer:** Build pricing and analytics APIs
- **Data Scientist:** Implement pricing algorithms
- **Frontend Developer:** Build polished dashboard

**Example Focus:**
```
Priority 1: Show sophisticated pricing logic (investors want to see IP)
Priority 2: Beautiful visualizations (charts, graphs, metrics)
Priority 3: Real-time optimization demo
```

**Demo:** Live demo of pricing system to "investors" (gamerunner + other directors).

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

**Q1-Q2 (Foundation building):** **Parallel Execution** ⚡
- Agent 1: Pricing Engine API (dynamic pricing calculations)
- Agent 2: Analytics API (revenue metrics and forecasting)
- Agent 3: Dashboard (visualizations and monitoring)
- **Why:** Fastest way to get working end-to-end pricing system
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Optimization & ML):** **Iterative Refinement** ✨
- Agent 1: Add ML forecasting or competitor intelligence
- Agent 2: Review and optimize algorithms
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples


### Role-Specific Tips

**Separate algorithm design from implementation:**
One agent designs the pricing model (mathematical formulas), another implements it in code. Keeps logic clear.

**Use data visualization libraries early:**
Prompt agents with "Use Chart.js/Plotly" rather than building charts from scratch. Professional visualizations matter for credibility.

**Demo-first thinking:**
Structure your agents around what you'll show: "Agent 1 builds the pricing brain, Agent 2 builds the analytics eyes, Agent 3 builds the executive interface."

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (analytics and API examples)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Pricing & Revenue-Specific Challenges

**"Pricing algorithm complexity - too many factors"**
- **Solution:** Start simple, add complexity incrementally
- Use refinement agent: "Review this pricing formula and simplify it"
- Agent prompt: "Break down multi-factor pricing into modular functions"
- Test each factor separately before combining

**"Real-time price updates causing race conditions"**
- **Solution:** Implement proper locking or queue-based updates
- Agent prompt: "Add request queuing to prevent concurrent pricing updates"
- Or simplify: "Batch price updates every 5 minutes instead of real-time"
- Use caching to reduce calculation overhead

**"Revenue optimization - don't know the math"**
- **Solution:** Let agents handle the mathematics
- Agent prompt: "Explain revenue optimization for airlines, then implement the formula"
- Focus on business logic, let agent translate to code
- Use simple models first (linear), add sophistication later

**"Competitor price data integration issues"**
- **Solution:** Start with mock data, standardize the interface
- Agent prompt: "Create mock competitor API that returns realistic price data"
- Design clean interface: `GET /competitors/{airline}/prices/{route}`
- Real integration can come later after interface is proven

**"Dashboard showing wrong metrics or confusing data"**
- **Solution:** Define metrics clearly upfront
- Agent prompt: "Here are the exact revenue metrics I need calculated: [list]. Build API for each."
- Validate calculations with known test data
- Use visualization agent: "Make this revenue chart clearer and more intuitive"

---

## TECH STACK SUGGESTIONS

### Option A: Python Analytics Stack (Recommended)
- **Backend:** Flask or FastAPI
- **ML/Analytics:** pandas, numpy, scikit-learn
- **Visualization:** Chart.js (frontend) or Plotly
- **Database:** SQLite for price history
- **Why:** Python is perfect for analytics and ML

### Option B: JavaScript Full Stack
- **Backend:** Express.js
- **Analytics:** Simple-statistics library
- **Visualization:** Chart.js or D3.js
- **Database:** MongoDB or SQLite
- **Why:** JavaScript everywhere

### Option C: Spreadsheet-First
- **Engine:** Python backend
- **Interface:** Export to Excel/CSV, visualize there
- **Why:** Quick prototyping, executives love Excel

**Pro tip:** Use pandas for data manipulation - agents are great at generating pandas code.

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
3. Start Agent 1 (Researcher or Data Scientist): Begin research/algorithm design

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research dynamic pricing strategies
- Agent 2: Design pricing algorithms based on research
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
- Focus on sophisticated algorithms and visualizations
- Test as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to answer investor questions

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

> "You have 30 minutes to build what normally takes weeks of data science work. Your secret weapon is coordinating 2-3 agent teams efficiently. The agent that designs the algorithm doesn't have to be the agent that implements it. The agent that calculates revenue doesn't have to be the agent that visualizes it. Specialization > generalization."

Good luck, Director. The company's profitability is in your hands. 💰📈
