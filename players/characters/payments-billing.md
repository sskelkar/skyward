# DIRECTOR OF PAYMENTS & BILLING
## Character Sheet

---

## YOUR ROLE

You are the **Director of Payments & Billing** at SkywardAI - the money handler. Every dollar that flows through the company passes through your systems.

**Department:** Finance Operations - Backend
**Team Size:** You + 2-3 agent teams (6-9 Claude agents total)
**Reporting to:** VP of Finance

📚 **New to being a director?** Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) to learn how to manage agent teams and delegate effectively.

📖 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) for patterns and prompt engineering.

---

## YOUR NORTH STAR

> **"Zero payment failures, zero revenue leakage, 100% transaction accuracy."**

You obsess over the money. Every failed payment is lost revenue. Every refund mistake costs trust. Your success is measured in payment success rates, transaction accuracy, and revenue reconciliation.

### What Drives You
- **Reliability:** Payments must work, every time, no exceptions
- **Security:** Protect customer payment data like Fort Knox
- **Speed:** Fast checkout drives conversions
- **Trust:** Customers must feel safe giving us their money

### What Keeps You Up at Night
- Payment gateway failures that block bookings
- Fraudulent transactions that cost money
- Failed refunds that create customer service nightmares
- Transaction data that doesn't reconcile

---

## CHARACTER FLAVOR

You're the **guardian of the vault**. While other directors dream about features, you worry about PCI compliance and transaction logs.

**Your mantras:**
- "Money in, money out - always balanced"
- "A failed payment is a lost customer"
- "Security first, convenience second"
- "Every cent must be accounted for"

**In board meetings, you say:**
- "Payment success rate: 98.7% - industry best is 99%"
- "Zero fraudulent transactions this quarter"
- "Refund processing time: 2 minutes average"
- "Fully PCI compliant"

**Your personality:**
- Cautious, detail-oriented, slightly paranoid
- You don't break things in production
- Trust nothing, verify everything
- Pride yourself on bulletproof systems

---

## YOUR DEPARTMENT ARCHITECTURE

As a director, you don't code - you **orchestrate teams**. You manage **2-3 agent teams**, each building a separate microservice.

### Recommended Multi-Service Architecture

**Service 1: Payment Gateway Integration**
- **Purpose:** Process credit cards, handle payment methods, integrate with payment providers
- **Key Decisions:**
  - Which payment providers to support? (Stripe, PayPal, credit cards)
  - How to handle payment failures gracefully?
  - Retry logic for transient failures?
  - How to store payment tokens securely?
- **Integration Points:** Called by Booking Portal during checkout, returns payment status
- **Team:** 1-2 backend-focused agents

**Service 2: Refund & Cancellation Processing**
- **Purpose:** Handle booking cancellations, process refunds, calculate refund amounts
- **Key Decisions:**
  - Full refund vs. partial refund rules?
  - How to handle refund failures?
  - Refund status tracking and notifications?
  - Integration with payment gateway for actual refund processing?
- **Integration Points:** Called by Customer Service, updates booking status
- **Team:** 1-2 backend-focused agents

**Service 3: Billing & Transaction History**
- **Purpose:** Invoice generation, transaction records, receipt delivery
- **Key Decisions:**
  - What details go on invoices and receipts?
  - How to store transaction history?
  - Export formats for accounting systems?
  - How to handle transaction disputes?
- **Integration Points:** Reads payment data, generates customer-facing documents
- **Team:** 1-2 backend-focused agents

**Why multiple services?**
- ✅ Each agent team has focused responsibility and clear ownership
- ✅ Services can be built in parallel, accelerating delivery
- ✅ Easy to demo incrementally (Gateway in Q1, add Refunds in Q2, etc.)
- ✅ Realistic separation of concerns - payments, refunds, and billing are distinct domains

📚 **For detailed multi-service patterns:** See [MULTI-SERVICE-GUIDE.md](../MULTI-SERVICE-GUIDE.md)

---

## WHAT YOU'LL BUILD

### Quarter 1: Research & Vision (45-60 min)
**Focus:** Strategy, research, and planning - NOT working code yet

**Your Objectives:**
- Research payment processing best practices (use agents to analyze)
- Define your 2-3 service architecture (Gateway, Refunds, Billing)
- Create vision document with payment flows and security approach
- Plan your technical approach and agent team structure

**Deliverable Options:**
- Vision document with architecture diagram and payment flow diagrams
- Security and compliance strategy
- Simple MVP (if time permits) - basic payment mock

**Agent Roles to Use:**
- **Business Analyst:** Research payment processing best practices
- **Security Architect:** Design secure payment handling approach
- **Technical Architect:** Design service architecture
- **Compliance Specialist:** Research PCI/security requirements

**Example Prompt:**
```
"You are a payments architect researching payment processing.

Research best practices for:
1. Payment gateway integration (Stripe, PayPal)
2. Secure token handling (PCI compliance)
3. Refund processing flows
4. Transaction reconciliation

Create architecture diagram for payment processing service."
```

**Demo:** Present your vision doc, security strategy, or MVP. Explain your approach and what you'll build in Q2.

---

### Quarter 2: Investor Demo Build (45-60 min)
**Focus:** Build something impressive to show investors

**Your Objectives:**
- Build payment gateway integration (mock is fine)
- Create working payment flow (card number → success/failure)
- Show transaction records
- Focus on security and reliability narrative

**Deliverable:**
- Working payment processing endpoint OR
- Refund processing service OR
- Invoice generation working

**Agent Roles to Use:**
- **Backend Developer:** Build payment APIs
- **Security Engineer:** Implement token handling
- **QA Engineer:** Test payment flows

**Example Focus:**
```
Priority 1: Payment flow works reliably
Priority 2: Security story is solid (even if mocked)
Priority 3: Show transaction tracking
```

**Demo:** Live demo of payment processing to "investors" (gamerunner + other directors).

---

### Quarter 3: Integration & Features (60 min)
**Focus:** Add features, integrate with other departments, handle chaos

**Your Objectives:**
- Add refund processing capabilities
- Improve error handling for payment failures
- Optional: Integrate with Booking Portal for real checkout
- Respond to gamerunner scenario (if introduced)

**Deliverable:**
- Enhanced payment system with refunds
- More robust error handling
- Better transaction tracking

**Gamerunner May Introduce:**
- "Payment gateway went down - implement fallback!"
- "Fraud detected - add fraud detection logic!"
- "Accounting needs transaction export - build it!"

**Demo:** Show new features and how you handled the scenario.

---

### Quarter 4: Launch Sprint (60 min)
**Focus:** Final polish, production-ready, launch!

**Your Objectives:**
- Complete end-to-end payment and refund flows
- Handle edge cases (expired cards, declined payments, refund failures)
- Transaction reconciliation and reporting
- Final security and compliance polish

**Deliverable:**
- Production-ready payment system
- Complete payment lifecycle works smoothly
- Comprehensive transaction tracking

**Demo:** Full payment flow from checkout to refund. Company launches! 🎉

---

## VISUAL DEMO EXAMPLES

**What "Good" Looks Like:**

**Bronze Tier:**
- POST /payment endpoint accepts card data
- Returns success/failure response
- Can process refunds
- Shows transaction record

**Silver Tier:**
- Handles edge cases gracefully (expired cards, insufficient funds)
- Secure token handling (even if mocked)
- Transaction history queryable
- Clear error messages

**Gold Tier:**
- Multiple payment methods supported
- Retry logic for failures
- Real-time transaction status
- Comprehensive logging and audit trail
- "This looks production-ready"

**Demo Script (30 seconds):**
1. Show payment endpoint accepting card data
2. Demonstrate successful payment
3. Demonstrate failed payment handling
4. Show refund processing
5. Show transaction history
6. Explain security approach

---

## MULTI-AGENT STRATEGIES

📚 **New to multi-agent orchestration?** Read [TUTORIAL.md](../TUTORIAL.md) first for comprehensive patterns, prompt templates, and detailed examples.

### Recommended Patterns for Payments & Billing

**Q1-Q2 (Foundation building):** **Sequential Pipeline** 🔗
- Agent 1: Design payment flow and security model
- Agent 2: Build payment gateway integration using Agent 1's design
- Agent 3: Build refund processing based on gateway
- **Why:** Payment systems have dependencies - security model → gateway → refunds
- See TUTORIAL.md "Pattern 2: Sequential Pipeline" for detailed example

**Q3-Q4 (Polish & features):** **Iterative Refinement** ✨
- Agent 1: Add new feature (fraud detection, multi-currency)
- Agent 2: Review and improve security/code quality
- **Why:** Build on existing work, incremental improvement
- See TUTORIAL.md "Pattern 4: Iterative Refinement" for examples

### Director-Level Strategy Tips

**Security-first thinking:**
Give agents clear security requirements upfront: "Never store raw card numbers" or "Use tokenization for all payment data." Direction beats cleanup.

**Error handling is critical:**
Ask agents to think through failure scenarios: "What happens when payment gateway times out?" or "How do we handle duplicate charges?"

**Test edge cases explicitly:**
Structure your agent teams around failure modes: "Test with expired card, declined card, network timeout." Work through the failure paths.

**Focus on reliability, not speed:**
Ask "Will this work 100 times out of 100?" not "Can we ship this faster?" Your agent teams optimize for correctness in payment systems.

**For prompts and examples:** See TUTORIAL.md sections:
- "Prompt Engineering for Agents" (templates)
- "Debugging Agent Outputs" (for payment flow bugs)
- "Quick Reference" (cheat sheets)

---

## COMMON CHALLENGES & SOLUTIONS

💡 **For general challenges** (agents producing broken code, context management, etc.), see [TUTORIAL.md](../TUTORIAL.md) "Common Pitfalls & Solutions" section.

### Payments & Billing-Specific Challenges

**"Payment always succeeds - no error handling"**
- **Solution:** Be explicit in prompts: "Handle these failure cases: expired card, declined, insufficient funds, network timeout"
- Use testing agent: "Test this payment endpoint with various failure scenarios"
- Director mindset: "What can go wrong, and how do we handle it gracefully?"

**"How do I handle real payment gateways?"**
- **Solution:** Use mock/test mode for Stripe or PayPal APIs
- Or build your own mock gateway that returns success/failure based on card number
- Director mindset: "Demo needs to work, not process real money"

**"Refund processing breaks when payment is missing"**
- **Solution:** Test data setup - ensure test payments exist before refund testing
- Use integration agent: "Set up test scenario: create payment → process refund"
- Director mindset: "What's the happy path data setup needed?"

**"Transaction history is messy or incomplete"**
- **Solution:** Define schema clearly: "Store: transaction_id, amount, status, timestamp, card_last4"
- Use refinement agent: "Clean up transaction storage and make it queryable"
- Director mindset: "What questions will accounting ask about transactions?"

**"Security concerns - storing sensitive data"**
- **Solution:** Be explicit: "Never store full card numbers, only tokens and last 4 digits"
- Ask security-focused agent: "Review payment handling for security issues"
- Director mindset: "Would I trust this system with my own credit card?"

---

## TECHNICAL APPROACH

As a director, you'll work with your agent teams to determine the technical approach. Here are the key decisions to consider:

### Key Technical Decisions

**Payment Gateway Strategy:**
- Use real gateway (Stripe/PayPal test mode) vs. mock gateway?
- How to handle API keys and credentials securely?
- Synchronous vs. asynchronous payment processing?

**Data Storage:**
- What payment data must be stored? (tokens, amounts, status)
- How to ensure PCI compliance (never store full card numbers)?
- Database vs. file-based for transaction history?

**Error Handling:**
- What failure scenarios to handle? (timeouts, declines, fraud)
- Retry logic for transient failures?
- How to communicate errors to users?

**Refund Strategy:**
- Full vs. partial refunds?
- Automated vs. manual approval process?
- How to handle refund failures?

### Director-Level Guidance

**For Q1-Q2:** Start with mock payment processing. Focus on the flow, not real integration. Use test card numbers that return success/failure.

**For Q3-Q4:** Consider real gateway integration if time permits, or add more sophisticated mocking (fraud detection, multiple payment methods).

**Pro tip:** Use Stripe test mode - it's free, realistic, and doesn't require real money. Your agents can integrate with real APIs in test mode.

---

## QUARTER-BY-QUARTER GOALS

### Q1: Vision & Strategy (45-60 min)
- Research payment processing best practices
- Define your service architecture
- Create vision doc with payment flows and security approach
- **Success = clear strategy and security-first plan for Q2-Q4**

### Q2: Investor Demo (45-60 min)
- Build payment gateway integration
- Focus on reliability and security narrative
- Core payment flow works
- **Success = impressive demo showing solid payment foundation**

### Q3: Integration & Features (60 min)
- Add refund processing
- Better error handling
- Optional integration with Booking Portal
- Respond to gamerunner scenario
- **Success = enhanced system, scenario handled well**

### Q4: Launch Ready (60 min)
- Complete payment and refund flows
- Edge case handling
- Transaction reconciliation
- Professional polish
- **Success = production-ready payment system, ready to launch!**

---

## INTEGRATION POINTS (OPTIONAL)

You can work completely independently with mock data, or optionally integrate:

### With Booking Portal
- Provide payment endpoint they call during checkout
- Or mock their payment calls

### With Customer Service
- Provide refund endpoint for cancellations
- Or mock refund requests

### With Analytics
- Provide transaction data for reporting
- Or mock transaction exports

### With Notifications
- Trigger payment confirmation emails
- Or mock notification calls

**Remember:** Integration is bonus points, not required. Focus on your own system first.

---

## SUCCESS METRICS

### What Makes You Successful
- ✅ Payment processing works reliably in every demo
- ✅ Error cases handled gracefully
- ✅ Security story is clear and credible
- ✅ You improve and add features each quarter
- ✅ Transaction data is accurate and queryable

### Red Flags to Avoid
- ❌ Payments that always succeed (no error handling)
- ❌ Storing full credit card numbers (security nightmare)
- ❌ Broken refund flows
- ❌ Demos that require "imagine payment works"
- ❌ No transaction tracking or audit trail

---

## QUICK START GUIDE

### Before Game Day
- Read [DIRECTOR-GUIDE.md](../DIRECTOR-GUIDE.md) - Learn to think like a director
- Read [TUTORIAL.md](../TUTORIAL.md) - Multi-agent patterns
- Bookmark TUTORIAL.md "Quick Reference" for prompt templates

### Quarter 1: Research & Vision (60 min)

**First 10 minutes:**
1. Decide: What will I deliver? (Vision doc? Security strategy? MVP?)
2. Plan your agent strategy: Which agents for which tasks?
3. Start Agent 1 (Security Architect): Begin security/architecture work

**Minutes 10-50:**
Use agents for research and planning:
- Agent 1: Research payment processing best practices
- Agent 2: Design secure architecture
- Agent 3: Create payment flow diagrams

**Last 10 minutes:**
1. Compile vision document or polish MVP
2. Practice your vision presentation (3 min)
3. Prepare to explain your Q2-Q4 strategy

### Quarter 2: Investor Demo Build (60 min)

**First 5 minutes:**
1. Review your Q1 vision
2. Decide which service to build first
3. Start Agent 1 (Backend): Build payment gateway

**Minutes 5-50:**
Build your investor demo:
- Agents build services based on Q1 architecture
- Focus on reliability and security story
- Test as you go

**Last 10 minutes:**
1. Integration and testing
2. Practice your investor demo
3. Prepare to answer security questions

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

> "Payments are the heartbeat of the business. If you can't take money, you don't have a business. Make it bulletproof, make it secure, make it boring. Boring payments are successful payments."

Good luck, Director. The company's revenue stream is in your hands. 💳✨
