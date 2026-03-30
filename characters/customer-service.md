# DIRECTOR OF CUSTOMER SERVICE & SUPPORT
## Character Sheet

---

## YOUR ROLE

You are the **Director of Customer Service & Support** at SkywardAI - the guardian of customer satisfaction and crisis resolver.

**Department:** Customer Experience - Support & Automation
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Customer Experience

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Resolve every issue on first contact. Automate everything that can be automated."**

You stand between frustrated customers and disaster. A missed flight, a wrong booking, a refund request - your systems turn these moments of crisis into opportunities to build loyalty. Your success is measured in resolution time and customer satisfaction.

### What Drives You
- **Customer satisfaction:** Every issue resolved quickly and completely
- **Automation:** Reduce repetitive work, scale support efficiently
- **Efficiency:** Fast resolution time, low cost per ticket
- **Empathy:** Customers should feel heard and helped

### What Keeps You Up at Night
- Long wait times causing customer frustration
- Support agents overwhelmed with repetitive questions
- Escalations that could have been prevented
- Customers leaving bad reviews due to poor support

---

## CHARACTER FLAVOR

You're the **empathetic problem-solver who automates support**. While other directors build features for customers who are happy, you build systems for customers who are upset. You're the customer advocate who believes the best support is invisible.

**Your mantras:**
- "Every angry customer is a retention opportunity"
- "Automate the simple, humanize the complex"
- "Fast resolution beats perfect resolution"
- "Support is a profit center, not a cost center"

**In board meetings, you say:**
- "Average resolution time: 4.2 minutes, down from 18 minutes"
- "Automation handles 67% of tickets, human agents handle 33%"
- "Customer satisfaction: 4.6/5 stars"
- "Support cost per ticket: $1.20, industry average is $5"

**Your personality:**
- Patient and systematic, efficiency-focused
- Hate seeing customers suffer
- Love building systems that scale
- The person who says "we can automate that"

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Chatbot API** (Agent Team A)
- Tech: Flask/FastAPI backend with NLP
- Port: 5001
- Purpose: Conversational AI, FAQ handling, intent classification
- Team: 1-2 backend agents

**Service 2: Ticketing System API** (Agent Team B)
- Tech: Flask/FastAPI backend
- Port: 5002
- Purpose: Ticket CRUD, categorization, routing, escalation
- Team: 1-2 backend agents

**Service 3: Knowledge Base Dashboard** (Agent Team C)
- Tech: React/Vue/vanilla JS frontend
- Port: 3000
- Purpose: Customer portal, agent dashboard, analytics
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
- Research chatbot best practices and support workflows
- Define your 2-3 service architecture (Chatbot API, Ticketing API, Dashboard)
- Create vision document with support flows and automation strategy
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with architecture diagram and support workflows
- Wireframes for chatbot UI and agent dashboard
- Simple MVP (if time permits) - basic prototype

**Agent Roles to Use:**
- **Business Analyst:** Research support processes and automation opportunities
- **UX Designer:** Design chatbot conversation flows and agent interfaces
- **AI/NLP Specialist:** Plan intent classification and NLP strategy
- **Technical Architect:** Design service architecture

**Example Prompt:**
```
"You are a Business Analyst researching customer support automation.

Analyze support ticket patterns and common customer issues.
Design automation strategy for our support system:
1. What questions should the chatbot handle?
2. What ticket categories do we need?
3. What triggers escalation to human agents?
4. What self-service workflows can we automate?

Focus on reducing resolution time and improving satisfaction."
```

**Demo:** Present your vision doc, wireframes, or MVP. Explain your strategy and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build 1-2 working services based on Q1 vision
- Create a demoable support flow (chatbot + ticketing)
- Make it look professional and efficient
- Focus on what investors want to see: scalability and automation ROI

**Deliverable:**
- Working chatbot that handles common questions
- Working ticket system with categorization OR
- Impressive demo showing automation reducing support costs

**Agent Roles to Use:**
- **Backend Developer:** Build chatbot and ticketing APIs
- **Frontend Developer:** Build customer portal and agent dashboard
- **QA Engineer:** Test the demo flow

**Example Focus:**
```
Priority 1: Show automation value (investors care about cost savings)
Priority 2: Core flow works (customer asks → bot answers OR creates ticket)
Priority 3: Handle edge cases (defer if time-limited)
```

**Demo:** Live demo of support flow to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add sentiment analysis or escalation routing
- Improve NLP accuracy and response quality
- Optional: Integrate with other directors' APIs (bookings, notifications)
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced support system with 2-3 new features
- More sophisticated automation
- Better customer experience

**Gamerunner May Introduce:**
- "Flight cancellation created 500 tickets - handle the surge!"
- "Customers complaining chatbot is unhelpful - improve it!"
- "Add proactive support for delayed flights!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end support flow
- Handle edge cases and errors gracefully
- Multi-channel support (chat, email)
- Analytics dashboard showing support metrics
- Final automation polish

**Deliverable:**
- Production-ready support platform
- Complete customer journey works smoothly
- Professional appearance

**Demo:** Full support flow from customer question to resolution. Company launches! 🎉

---

### Quarter 5: Survive & Adapt (30 min)
**Focus:** Quick response to market conditions (dice-driven scenario)

**Possible Scenarios:**
- Crisis: "Mass cancellation - 1000 angry customers!"
- Opportunity: "Add voice support with AI assistant!"
- Competition: "Competitor has 2-minute response time - beat it!"

**Your Objectives:**
- Respond to gamerunner's dice roll scenario
- Build or fix quickly
- Demonstrate adaptability

**Demo:** Show how you handled the crisis/opportunity.

---

### Quarter 6: Final Challenge (30 min)
**Focus:** One more scenario, final improvements

**Possible Scenarios:**
- Innovation: "Add predictive support AI"
- Premium: "Launch VIP support tier"
- Scale: "Support volume 10x - optimize automation"

**Demo:** Final feature showcase and retrospective.

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- Chatbot answers basic questions
- Can submit a support ticket
- View ticket status
- Simple agent interface

**Silver Tier:**
- Smart bot that handles common requests
- Automated workflows (refunds, changes)
- Clean customer portal
- Analytics tracking

**Gold Tier:**
- Sophisticated NLP chatbot
- Seamless automation + human escalation
- Beautiful support interface
- "This feels like enterprise support software"

**Demo Script (30 seconds):**
1. Show chatbot interface in browser
2. Ask "How do I change my flight?" → bot responds with self-service link
3. Submit test ticket → show auto-categorization
4. Display agent dashboard (tickets by priority)
5. Show resolution analytics (avg time, satisfaction)
6. Explain multi-agent strategy used

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Customer Service

**Q1-Q2 (Foundation building):** **Parallel Execution** ⚡
- Agent 1: Chatbot API (NLP, intent classification, FAQ)
- Agent 2: Ticketing API (CRUD, categorization, routing)
- Agent 3: Frontend (customer portal + agent dashboard)
- **Why:** Fastest way to get working end-to-end support flow
- See TUTORIAL.md "Pattern 1: Parallel Execution" for detailed example

**Q3-Q4 (Polish & features):** **Iterative Refinement** ✨
- Agent 1: Add new feature (sentiment analysis, escalation)
- Agent 2: Review and improve NLP accuracy/code quality
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples

**Q5+ (Complex features):** **Specialist Roles** 🎯
- NLP Agent: Owns all chatbot intelligence across quarters
- Backend Agent: Owns all ticketing logic across quarters
- Frontend Agent: Owns all UI/UX work across quarters
- **Why:** Context retention, domain expertise
- See TUTORIAL.md "Pattern 3: Specialist Roles" for details

### Role-Specific Tips

**Keep chatbot separate from ticketing agents:**
Conversational AI requires different thinking than CRUD operations. One agent focuses on NLP/intent while another handles ticket management.

**Use simple keyword matching first:**
Don't overcomplicate Q1 with complex NLP. Prompt agents with "Use keyword detection for FAQ matching" and add sophistication in Q2-Q3.

**Demo-first thinking:**
Structure your agents around what you'll show: "Agent 1 builds what customers type, Agent 2 builds what agents see, Agent 3 builds what executives track."

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Practical Examples" (adapt patterns to support use cases)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Customer Service-Specific Challenges

**"Chatbot gives wrong answers or doesn't understand questions"**
- **Solution:** Start simple in Q1 - use keyword matching, not complex NLP
- Tell agent: "Build FAQ matcher using keywords: 'refund' → refund policy, 'change' → booking changes"
- Add fallback: "If confidence < 80%, create ticket instead of answering"
- In Q2, add refinement agent: "Improve chatbot accuracy based on common misunderstood questions"

**"Don't know how to build NLP classifier"**
- **Solution:** Use simple heuristics first, not machine learning
- Agent prompt: "Build keyword-based ticket classifier: if text contains ['refund', 'money back'] → category='refund'"
- For Q2+: "Use simple confidence scoring based on keyword matches"
- Alternative: "Call OpenAI API for intent classification" (if available)

**"Ticket routing logic is too complex"**
- **Solution:** Start with basic priority rules
- Agent prompt: "Auto-assign priority: High if contains ['urgent', 'angry', 'lawsuit'], Medium if contains ['change', 'help'], Low otherwise"
- Use decision tree, not complex algorithms
- Escalation agent Q3: "Add escalation triggers: negative sentiment OR VIP customer OR unresolved > 24hrs"

**"Hard to demo automation ROI"**
- **Solution:** Generate realistic mock data showing impact
- Agent prompt: "Create analytics showing: Before (100 tickets/day, 18 min avg resolution) vs After (chatbot handles 67%, 4.2 min avg resolution)"
- Show cost savings: "$5/ticket before → $1.20/ticket after automation"
- Visual charts make impact clear to investors

**"Response quality varies too much"**
- **Solution:** Use templates for common scenarios
- Agent prompt: "Create response templates for: refund requests, booking changes, flight status, complaints"
- Add tone guidelines: "Use empathetic language, acknowledge frustration, offer solutions"
- QA agent in Q3: "Review responses for tone and completeness"

---

## TECH STACK SUGGESTIONS

### Option A: Simple & Fast (Recommended for Q1-Q2)
- **Backend:** Flask (Python) or Express (Node.js)
- **Chatbot:** Keyword matching or simple pattern matching
- **Database:** SQLite for tickets
- **Frontend:** Vanilla HTML/CSS/JavaScript
- **Why:** Minimal setup, agents know these well

### Option B: Modern Stack (If you're comfortable)
- **Backend:** FastAPI or Express
- **Chatbot:** OpenAI API or simple NLP library
- **Database:** Postgres or SQLite
- **Frontend:** React or Vue
- **Why:** More realistic, better UX capabilities

### Option C: AI-Enhanced
- **Backend:** Flask/FastAPI
- **NLP:** OpenAI API for intent classification
- **Database:** SQLite
- **Frontend:** React
- **Why:** Sophisticated chatbot with minimal NLP expertise

**Pro tip:** Use whatever you know best. Learning a new framework + learning multi-agent = too much for 30 minutes.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research support automation best practices
- Define your service architecture
- Create vision doc with support flows and automation strategy
- **Success = clear strategy and plan for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build 1-2 working services
- Focus on automation ROI and cost savings
- Core support flow works (chatbot + ticketing)
- **Success = impressive demo showing scalability and efficiency**

### Q3: Integration & Features (60 min)
- Add 2-3 significant features (sentiment, escalation, analytics)
- Better NLP accuracy and routing logic
- Optional integration with other departments
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete end-to-end support flow
- Edge case handling
- Multi-channel support
- Professional analytics dashboard
- **Success = production-ready support platform, ready to launch!**

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
- Fetch booking details in chatbot responses
- Link tickets to specific bookings
- Or use mock booking data

### With Notifications
- Send ticket confirmation emails
- Alert customers when issues are resolved
- Or show "notification sent" message

### With Inventory
- Check flight status for customer questions
- Process booking changes in tickets
- Or hardcode flight data

### With Pricing
- Calculate change fees for modifications
- Display refund amounts
- Or use mock pricing data

**Remember:** Integration is bonus points, not required. Focus on your own system first.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Chatbot handles common questions effectively
- ✅ Ticket system categorizes and routes intelligently
- ✅ Automation demonstrably reduces workload and costs
- ✅ Multi-agent strategy is clear and effective
- ✅ You improve and add features each quarter
- ✅ Support metrics show efficiency and satisfaction

### Red Flags to Avoid
- ❌ Chatbot that frustrates users with wrong answers
- ❌ Tickets with no categorization or priority
- ❌ No self-service options or automation
- ❌ Can't demonstrate support ROI metrics
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
3. Start Agent 1 (Business Analyst): Begin support process research

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research chatbot best practices and support automation
- Agent 2: Design conversation flows and automation strategy
- Agent 3: Design service architecture

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision
2. Decide which 1-2 services to build
3. Start Agent 1 (Backend): Build chatbot API

**Minutes 5-50:**
Build your investor demo:
- Agents build services based on Q1 architecture
- Focus on automation ROI and cost savings
- Test as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to show automation metrics

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

> "You have 30 minutes to build what normally takes 3 hours. Your secret weapon is coordinating 2-3 agents efficiently. The agent that builds the chatbot doesn't have to be the agent that polishes it. The agent that handles tickets doesn't have to be the agent that analyzes them. Assembly line beats single artisan."

Good luck, Director. Every frustrated customer is counting on you to make things right. 🎧💙

---

## ARCHIVED CONTENT (Old Multi-Agent Strategies)

The following sections contain the original detailed multi-agent strategy examples. While still valid approaches, the new format above provides a more structured quarter-by-quarter progression. These are preserved for reference.

### Strategy 1: Bot + Ticketing + Dashboard (Original Q1 Approach)
**When to use:** Building complete support system

```
Agent 1 (Chatbot Builder):
"Build a customer support chatbot:

FAQ capabilities:
- 'How do I check in?' → link to check-in page
- 'How do I cancel?' → explain cancellation policy
- 'Where is my confirmation?' → check booking status
- 'How to change my flight?' → self-service instructions

Use simple keyword matching or LLM API if available.
If question not understood → offer to create ticket.

Build as chat interface (web UI) with Flask backend.
Store conversation history."

Agent 2 (Ticket System):
"Build support ticket system:

Database schema:
- Tickets: ticket_id, customer_id, subject, description, status, priority, created_at
- Messages: message_id, ticket_id, sender, content, timestamp

API:
- POST /tickets (create new)
- GET /tickets/{id} (view ticket)
- POST /tickets/{id}/messages (add reply)
- PUT /tickets/{id}/status (update status)

Include sample tickets for demo."

Agent 3 (Agent Dashboard):
"Build support agent dashboard using Agent 2's API:
- Ticket list (filter by status, priority)
- Ticket detail view with conversation
- Quick actions (mark resolved, escalate)
- Stats: open tickets, avg resolution time, today's volume

Use simple HTML table + forms. Color-code by priority."
```

**Timeline:**
- Min 0-10: Agent 1 builds chatbot
- Min 10-20: Agent 2 builds ticketing
- Min 20-25: Agent 3 builds dashboard

---

### Strategy 2: Smart Automation (Recommended for Q2)
**When to use:** Adding intelligence to support

```
Agent 1 (NLP Classifier):
"Build ticket classification system:

Categories:
- Refund request
- Booking change
- Flight status question
- Technical issue
- Complaint

Use keyword detection or simple ML classifier.
Auto-assign priority:
- High: refund, complaint, urgent words
- Medium: booking change
- Low: informational

Auto-route to appropriate queue.
API: POST /classify (ticket text) → returns category, priority"

Agent 2 (Self-Service Automation):
"Build automated actions based on Agent 1's classification:

If 'refund request' detected:
- Auto-check eligibility (refundable fare?)
- If eligible → process refund automatically
- If not → explain policy, offer alternatives

If 'booking change':
- Show available change options
- Calculate fee
- Provide self-service change link

If 'flight status':
- Look up flight, return current status
- No ticket needed

Reduce ticket volume by 50% via automation."

Agent 3 (Analytics):
"Build support analytics dashboard:
- Ticket volume over time (Chart.js)
- Category breakdown (pie chart)
- Resolution time distribution
- Automation rate (% auto-resolved)
- Customer satisfaction (mock ratings)

Show ROI of automation."
```

---

### Strategy 3: Sentiment & Escalation (Recommended for Q3)
**When to use:** Handling complex support scenarios

```
Agent 1 (Sentiment Analyzer):
"Build sentiment detection for support conversations:

Analyze customer messages for:
- Angry/frustrated: words like 'terrible', 'angry', 'lawsuit', caps
- Neutral: normal questions
- Happy: 'thank you', 'great', 'appreciate'

Score: -1 (angry) to +1 (happy)

If negative sentiment + high-priority issue → auto-escalate
API: POST /analyze-sentiment (text) → returns score, escalation_needed"

Agent 2 (Escalation System):
"Build smart escalation routing:

Escalation triggers:
- Negative sentiment
- VIP customer (high lifetime value)
- Legal keywords
- Unresolved for > 24 hours
- Customer requests manager

Escalation actions:
- Route to senior agent queue
- Notify manager
- Flag for urgent attention
- Auto-apologize + offer compensation

Create escalation workflow UI."

Agent 3 (Quality Monitoring):
"Build quality assurance system:
- Random ticket sampling
- Check: response time, resolution quality, tone
- Score each interaction (1-10)
- Identify training needs
- Create QA dashboard

Mock the QA process for demo."
```

---

### Strategy 4: Proactive Support (Recommended for Q4)
**When to use:** Preventing issues before they happen

```
Agent 1 (Issue Predictor):
"Build proactive support detector:

Monitor for issues:
- Flight delayed → notify affected passengers
- Booking without check-in 24hrs before → remind
- Weather alert on route → warn customers
- System error → reach out to affected users

Create alert system that triggers notifications.
API: POST /proactive-alert (scenario) → creates outreach"

Agent 2 (Communication Engine):
"Build multi-channel notification system:
- Email templates (delay, cancellation, reminder)
- SMS alerts
- In-app notifications
- Chatbot proactive messages

Personalize based on:
- Urgency of issue
- Customer preference
- Channel availability

Generate sample notifications for demo."

Agent 3 (Impact Dashboard):
"Track proactive support effectiveness:
- Issues prevented (vs reactive tickets created)
- Customer satisfaction for proactive vs reactive
- Notification open/click rates
- Cost savings from prevention

Create executive dashboard showing value."
```

