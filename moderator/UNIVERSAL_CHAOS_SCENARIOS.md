# Universal Chaos Scenarios
## Scenarios That Impact All 8 Directors

**Design Principle:** Each chaos scenario must give all 8 directors something specific and meaningful to work on, not just generic "make it better" tasks.

**When to use:** Gamerunner introduces one scenario in Q3 or Q4 (or both). Choose based on group dynamics and time available.

**Available Scenarios:**

1. **Competitor Launched Superior App** - Defensive response, ship competitive features fast (30-45 min)
2. **Enterprise Customer Deal** - Fortune 500 wants B2B features, prove business value (45-60 min)
3. **Regulatory Audit** - Privacy & accessibility compliance required (45-60 min)
4. **Security Breach Discovered** - Find and fix vulnerabilities before disclosure (60 min)
5. **Acquisition Due Diligence** - Tech giant wants to buy, prove production-readiness (60-90 min)
6. **Market Crash - Travel Downturn** - Economic crisis, pivot to survive (60 min)

**Roll a d6 to randomly select a scenario, or choose based on your group!**

---

## Scenario 1: "Competitor Launched a Superior App"

**Narrative Setup (Gamerunner reads aloud):**

> "Breaking news: MegaAir just launched their new booking platform. TechCrunch called it 'the future of airline booking.' They're eating our lunch. Traffic dropped 40% in the last hour. The CEO just called an emergency all-hands:
>
> 'We have ONE HOUR to ship features that differentiate us or we're dead. Each department - find what MegaAir is doing better and BEAT them. Go.'"

**Time Pressure:** 30-45 minutes to respond and demo improvements

---

### Department-Specific Challenges

#### 1. Director of Customer Booking Portal
**What MegaAir did better:**
- Their search is 3x faster
- They show real-time seat maps with social distancing indicators
- One-click rebooking for frequent travelers

**Your Challenge:**
- Optimize search performance (faster results)
- Add visual seat selection map
- Implement quick-book for returning customers

**Success Criteria:** Demonstrate speed improvement and one new UX feature

---

#### 2. Director of Flight Inventory & Scheduling
**What MegaAir did better:**
- Real-time seat availability (no stale data)
- Smart overbooking that never denies passengers
- Live schedule updates when delays happen

**Your Challenge:**
- Implement real-time inventory updates
- Add intelligent overbooking logic
- Create delay cascade prediction (if flight 101 delays, which others are affected?)

**Success Criteria:** Show real-time updates and smart overbooking in action

---

#### 3. Director of Pricing & Revenue Optimization
**What MegaAir did better:**
- Hyper-dynamic pricing (updates every 5 minutes based on demand)
- Price guarantee ("book now, if price drops we refund difference")
- Competitor price matching in real-time

**Your Challenge:**
- Implement surge pricing based on seat availability
- Add price drop protection feature
- Monitor MegaAir's prices and match/beat them

**Success Criteria:** Show dynamic pricing changing in real-time

---

#### 4. Director of Personalization & Recommendations
**What MegaAir did better:**
- AI-powered destination suggestions ("Considering your past trips...")
- Smart upsells (premium seats, lounge access)
- "Complete your trip" recommendations (hotels, cars)

**Your Challenge:**
- Build recommendation engine (even rule-based is fine)
- Add upsell suggestions during booking
- Recommend complementary services

**Success Criteria:** Show personalized suggestions for different customer types

---

#### 5. Director of Customer Service & Support
**What MegaAir did better:**
- AI chatbot that actually solves problems (not just FAQ links)
- Proactive support ("Your flight is delayed, here are rebooking options")
- Self-service refunds (no waiting for agents)

**Your Challenge:**
- Enhance chatbot to handle complex queries
- Add proactive notifications for delays/cancellations
- Build self-service refund workflow

**Success Criteria:** Demo chatbot handling a complex scenario end-to-end

---

#### 6. Director of Marketing & Growth
**What MegaAir did better:**
- Viral referral program ("Give $50, get $50")
- Social proof everywhere ("127 people booked this flight today")
- Urgency indicators ("Only 3 seats left at this price")

**Your Challenge:**
- Build referral/promo code system
- Add social proof to booking flow
- Create urgency indicators (limited seats, price expiring)

**Success Criteria:** Show growth mechanics integrated into user journey

---

#### 7. Director of Check-in & Boarding
**What MegaAir did better:**
- Mobile boarding passes with animated QR codes
- Automatic check-in 24 hours before flight
- Boarding group optimization (families together, efficient loading)

**Your Challenge:**
- Generate digital boarding passes with QR codes
- Build auto check-in feature
- Optimize boarding group assignments

**Success Criteria:** Show mobile boarding pass and auto check-in flow

---

#### 8. Director of Flight Status & Tracking
**What MegaAir did better:**
- Live flight tracking map (Google Maps style)
- Predictive delay alerts ("Weather in Dallas may delay your connection")
- Alternative flight suggestions when delays happen

**Your Challenge:**
- Build live status dashboard with map
- Add predictive delay detection
- Suggest alternative flights when issues detected

**Success Criteria:** Show live tracking and proactive rebooking suggestions

---

### Gamerunner Tips for Scenario 1

**Pacing:**
- Minute 0-5: Announce scenario, answer questions
- Minute 5-40: Directors work with agents to build responses
- Minute 40-50: Each director demos their competitive response (1-2 min each)

**Evaluation:**
- Did they ship something new? (not just talk about it)
- Is it a meaningful improvement? (not trivial)
- Does it differentiate from the "competition"?

**Variations:**
- Easy mode: "You have 60 minutes"
- Hard mode: "You have 30 minutes"
- Chaos mode: Announce at start of Q4, making it part of launch prep

---

## Scenario 2: "Enterprise Customer Deal - Fortune 500 Demands Features"

**Narrative Setup (Gamerunner reads aloud):**

> "INCREDIBLE NEWS: GlobalCorp - a Fortune 500 company with 50,000 employees - wants to sign a $10M contract to use SkywardAI as their exclusive corporate travel platform.
>
> Here's the catch: Their CFO wants a demo in ONE HOUR showing specific B2B features. If we nail this demo, we get the contract AND massive credibility before launch. If we don't... they go with MegaAir.
>
> The CEO just forwarded their requirements. Every department has specific must-haves. Build them NOW."

**Time Pressure:** 45-60 minutes to build B2B features and prepare demo

**Note:** Works best in Q3 (building momentum toward Q4 launch)

---

### Department-Specific Requirements

#### 1. Director of Customer Booking Portal
**GlobalCorp's Requirements:**
- Bulk booking: Book 20+ employees on same flight with one form
- Approval workflow: Manager must approve before booking
- Corporate travel policy enforcement (economy only, direct flights preferred)

**Your Challenge:**
- Build multi-passenger booking form
- Add "Request Approval" flow (even if mocked)
- Show policy rules in action (block first-class, prefer non-stops)

**Success Criteria:** Demo booking 10 employees with policy enforcement

---

#### 2. Director of Flight Inventory & Scheduling
**GlobalCorp's Requirements:**
- Block booking: Reserve 50 seats on a flight for corporate event
- Flexible hold: Hold seats for 48 hours before payment
- Corporate discount tiers (volume-based)

**Your Challenge:**
- Implement group reservation system
- Add seat hold/release logic
- Calculate volume discounts

**Success Criteria:** Show blocking 50 seats with discount applied

---

#### 3. Director of Pricing & Revenue Optimization
**GlobalCorp's Requirements:**
- Contract pricing: Fixed rates for specific routes (NYC-SF always $299)
- Budget tracking: Show monthly spend vs budget
- Cost center allocation (different departments, different budgets)

**Your Challenge:**
- Create corporate pricing rules
- Build budget tracking dashboard
- Add cost center tagging to bookings

**Success Criteria:** Show booking with contract price and budget tracking

---

#### 4. Director of Personalization & Recommendations
**GlobalCorp's Requirements:**
- Corporate preferences: Remember traveler's usual preferences (aisle seat, no layovers)
- Team travel suggestions: "Your team is going to the conference - join them?"
- Unused ticket recovery: Alert when employee has unused credits

**Your Challenge:**
- Build traveler preference profiles
- Create team trip detection
- Add unused ticket tracking

**Success Criteria:** Show personalized suggestions for corporate traveler

---

#### 5. Director of Customer Service & Support
**GlobalCorp's Requirements:**
- Dedicated support line: Corporate customers get priority
- Bulk change management: Rebook 50 people when meeting is canceled
- Travel policy help: "Why was my booking rejected?"

**Your Challenge:**
- Add priority support tier
- Build bulk rebooking tool
- Create policy explanation feature

**Success Criteria:** Show priority support and bulk operations

---

#### 6. Director of Marketing & Growth
**GlobalCorp's Requirements:**
- Corporate portal: Branded landing page for GlobalCorp employees
- Usage analytics: Show CFO how much they're saving vs competitors
- Employee enrollment: Easy onboarding for 50,000 employees

**Your Challenge:**
- Create custom corporate portal page
- Build savings analytics dashboard
- Design employee enrollment flow

**Success Criteria:** Show branded portal with ROI dashboard

---

#### 7. Director of Check-in & Boarding
**GlobalCorp's Requirements:**
- Mobile app integration: Integrate with GlobalCorp's employee app
- VIP boarding: Corporate travelers get priority boarding
- Travel receipt automation: Receipts sent directly to expense system

**Your Challenge:**
- Create API for app integration (even if mocked)
- Add priority boarding to passes
- Auto-generate expense receipts

**Success Criteria:** Show priority boarding pass with expense receipt

---

#### 8. Director of Flight Status & Tracking
**GlobalCorp's Requirements:**
- Team tracking: See where all employees are currently
- Disruption alerts: Notify travel managers when employees face delays
- Corporate dashboard: Live view of all active corporate trips

**Your Challenge:**
- Build corporate trip dashboard
- Add travel manager alerts
- Show real-time employee location (mocked data OK)

**Success Criteria:** Show dashboard tracking multiple corporate travelers

---

### Gamerunner Tips for Scenario 2

**Pacing:**
- Minute 0-5: Announce opportunity, share requirements
- Minute 5-50: Directors build B2B features
- Minute 50-60: Rehearse and deliver demo to "GlobalCorp CFO" (gamerunner)

**Evaluation:**
- Did they build something demoable? (not just slides)
- Is it relevant to B2B needs? (not just B2C features)
- Can they articulate business value? ("This saves GlobalCorp $X")

**Roleplaying the CFO:**
As gamerunner, play a tough but fair CFO:
- Ask business questions: "How much will this save us?"
- Challenge technical details: "Can this integrate with SAP?"
- Compare to competitors: "MegaAir offers X, do you?"

**Making it fun:**
- Award the contract to the department with best B2B features
- Or: Award partial contract (5 departments instead of all 8) based on demos
- Celebrate when directors land the deal

**Variations:**
- Easy mode: Provide more detailed requirements upfront
- Hard mode: CFO adds surprise requirements mid-demo ("Wait, we also need...")
- Collaborative: Directors must integrate features (Booking calls Pricing for contract rates)

---

## Scenario 3: "Regulatory Audit - Privacy & Accessibility"

**Narrative Setup (Gamerunner reads aloud):**

> "URGENT: The Federal Aviation Administration and the European GDPR authority just announced a surprise audit of SkywardAI. Two focus areas:
>
> 1. **Privacy Compliance:** Are we handling customer data legally?
> 2. **Accessibility:** Can disabled users actually use our platform?
>
> We have ONE HOUR to demonstrate compliance or face massive fines and shutdown. Each department - prove you're compliant and accessible. The auditors arrive in 60 minutes."

**Time Pressure:** 45-60 minutes to add compliance features

---

### Department-Specific Requirements

#### 1. Director of Customer Booking Portal
**Privacy Requirements:**
- Cookie consent banner (GDPR)
- Privacy policy link visible
- No tracking without consent

**Accessibility Requirements:**
- Keyboard navigation (no mouse required)
- Screen reader compatible labels
- Sufficient color contrast

**Your Challenge:**
- Add privacy controls
- Make booking flow keyboard-navigable
- Test with accessibility checker

**Success Criteria:** Show booking with privacy controls and keyboard-only navigation

---

#### 2. Director of Flight Inventory & Scheduling
**Privacy Requirements:**
- Anonymize customer booking data
- No PII in logs
- Secure database (no hardcoded passwords)

**Accessibility Requirements:**
- API responses include accessibility metadata
- Schedule displays support screen readers
- Alternative text for visual schedule elements

**Your Challenge:**
- Remove PII from logs and responses
- Add accessibility metadata to API
- Document API accessibility features

**Success Criteria:** Show sanitized logs and accessible API responses

---

#### 3. Director of Pricing & Revenue Optimization
**Privacy Requirements:**
- Don't use discriminatory pricing (no profiling)
- Transparent pricing (no hidden fees)
- Price history available on request

**Accessibility Requirements:**
- Price displays readable by screen readers
- High contrast mode for price comparisons
- No reliance on color alone (colorblind friendly)

**Your Challenge:**
- Add pricing transparency (show all fees upfront)
- Make price displays screen-reader friendly
- Add high contrast mode

**Success Criteria:** Show transparent pricing with accessible displays

---

#### 4. Director of Personalization & Recommendations
**Privacy Requirements:**
- Recommendations work without tracking (privacy-first)
- Clear opt-out of personalization
- No cross-site tracking

**Accessibility Requirements:**
- Recommendations available in text format
- No auto-play videos
- Skip to main content option

**Your Challenge:**
- Build privacy-preserving recommendations
- Add personalization opt-out
- Make recommendations screen-reader accessible

**Success Criteria:** Show recommendations with clear privacy controls

---

#### 5. Director of Customer Service & Support
**Privacy Requirements:**
- Support tickets encrypted
- Right to deletion (GDPR)
- Data export on request

**Accessibility Requirements:**
- Chatbot works with screen readers
- Support forms keyboard accessible
- Alternative to phone support (text-based)

**Your Challenge:**
- Add data deletion workflow
- Make chatbot accessible
- Ensure all support channels accessible

**Success Criteria:** Show accessible support and privacy controls

---

#### 6. Director of Marketing & Growth
**Privacy Requirements:**
- No email without consent
- Unsubscribe in one click
- No selling customer data to third parties

**Accessibility Requirements:**
- Marketing emails readable by screen readers
- Campaign landing pages accessible
- No flashing animations (seizure risk)

**Your Challenge:**
- Add email consent management
- Make campaigns accessible
- Remove accessibility hazards

**Success Criteria:** Show compliant email system and accessible campaigns

---

#### 7. Director of Check-in & Boarding
**Privacy Requirements:**
- Boarding passes don't leak PII in QR code
- Secure transmission of check-in data
- No unnecessary data collection

**Accessibility Requirements:**
- Large print boarding pass option
- Audio check-in for visually impaired
- Wheelchair assistance request system

**Your Challenge:**
- Secure QR code generation
- Add large print mode
- Build accessibility request feature

**Success Criteria:** Show secure, accessible check-in flow

---

#### 8. Director of Flight Status & Tracking
**Privacy Requirements:**
- Don't track location without consent
- Anonymous flight status lookup
- No sharing flight data with third parties

**Accessibility Requirements:**
- Status updates available via SMS/email (not just visual)
- Map alternative for blind users (text descriptions)
- Alerts compatible with assistive devices

**Your Challenge:**
- Add anonymous status lookup
- Create text-based flight tracking
- Make alerts accessible

**Success Criteria:** Show privacy-preserving, accessible flight tracking

---

### Gamerunner Tips for Scenario 3

**Pacing:**
- Minute 0-5: Announce audit, explain requirements
- Minute 5-50: Directors add compliance features
- Minute 50-60: Rapid-fire compliance demos

**Evaluation:**
- Did they add at least one privacy feature?
- Did they add at least one accessibility feature?
- Can they explain WHY these matter?

**Educational value:**
- This scenario teaches real-world requirements
- Privacy and accessibility are often afterthoughts - this forces them upfront
- Good for participants who will build production systems

**Variations:**
- Focus only on privacy OR only on accessibility (not both)
- Pair directors to help each other test accessibility
- Bring in actual screen reader to demonstrate

---

## Scenario 4: "Security Breach Discovered"

**Narrative Setup (Gamerunner reads aloud):**

> "RED ALERT. 2:47 AM. Your phones are exploding with Slack notifications.
>
> Security team just discovered evidence of unauthorized access attempts across our systems. We don't know if data was stolen. We don't know the scope. What we DO know is that in 6 hours, we're legally required to report this to regulators.
>
> The CEO's message is blunt: 'Security audit. Every system. NOW. Find the vulnerabilities, patch them, and PROVE to me no customer data was compromised. We have 60 minutes before I have to call our lawyers and decide whether to disclose a breach.
>
> If we find and fix this fast, we report "attempted breach, no data loss." If we can't prove security... we're looking at a catastrophic data breach disclosure.'
>
> This is every startup's nightmare. Find the holes. Fix them. Document everything."

**Time Pressure:** 60 minutes to audit, fix, and prove security

---

### Department-Specific Security Challenges

#### 1. Director of Customer Booking Portal
**Security Concerns:**
- SQL injection vulnerability in search form
- Passwords transmitted in plain text
- No CSRF protection on booking submission
- Customer data visible in browser console logs

**Your Challenge:**
- Find and fix SQL injection (parameterized queries)
- Encrypt password transmission (HTTPS, hashing)
- Add CSRF tokens
- Remove sensitive data from client-side logging

**Success Criteria:** Show penetration test passing (SQL injection fails, secure password handling)

---

#### 2. Director of Flight Inventory & Scheduling
**Security Concerns:**
- API has no authentication (anyone can access)
- Admin endpoints exposed publicly
- Database credentials hardcoded in source code
- No rate limiting (vulnerable to DOS)

**Your Challenge:**
- Add API authentication (tokens/keys)
- Protect admin endpoints (auth required)
- Move credentials to environment variables
- Implement rate limiting

**Success Criteria:** Demonstrate authenticated API access and protected admin endpoints

---

#### 3. Director of Pricing & Revenue Optimization
**Security Concerns:**
- Pricing algorithm exposed in JavaScript (competitors can see it)
- No validation on price changes (can set negative prices)
- Sensitive financial data logged to public files
- No audit trail of price changes

**Your Challenge:**
- Move pricing logic to backend (hide algorithm)
- Add price validation (min/max bounds)
- Encrypt or remove sensitive logs
- Add audit logging for price changes

**Success Criteria:** Show pricing logic is server-side and validated

---

#### 4. Director of Personalization & Recommendations
**Security Concerns:**
- User tracking cookies without consent (GDPR violation)
- Recommendations leak data about other users
- No data retention policy (keeping data forever)
- PII stored in recommendation logs

**Your Challenge:**
- Add cookie consent mechanism
- Ensure recommendations don't leak user data
- Implement data retention policy
- Anonymize logs (remove PII)

**Success Criteria:** Show privacy-preserving recommendations and consent management

---

#### 5. Director of Customer Service & Support
**Security Concerns:**
- Support tickets readable by any customer (authorization bug)
- Chatbot stores conversation history insecurely
- Password reset tokens never expire
- Customer refund amounts editable in URL

**Your Challenge:**
- Add authorization checks (users see only their tickets)
- Encrypt chat history storage
- Add token expiration (15-min window)
- Validate refund amounts server-side

**Success Criteria:** Demonstrate customers can't access each other's data

---

#### 6. Director of Marketing & Growth
**Security Concerns:**
- Email addresses leaked in unsubscribe URLs
- Analytics tracking PII without anonymization
- Campaign system vulnerable to email injection
- No protection against scraping user data

**Your Challenge:**
- Anonymize unsubscribe links (use tokens)
- Strip PII from analytics
- Sanitize email inputs (prevent injection)
- Add rate limiting to prevent scraping

**Success Criteria:** Show anonymized analytics and secure email system

---

#### 7. Director of Check-in & Boarding
**Security Concerns:**
- QR codes contain unencrypted passenger data
- Boarding passes accessible without authentication
- No verification that user owns the ticket they're checking in
- Mobile app API has no encryption

**Your Challenge:**
- Encrypt data in QR codes (or use reference IDs)
- Require authentication for boarding pass access
- Verify ticket ownership before check-in
- Enforce HTTPS on all API calls

**Success Criteria:** Show encrypted QR codes and authenticated access

---

#### 8. Director of Flight Status & Tracking
**Security Concerns:**
- Flight status API reveals passenger manifests
- Real-time tracking exposes aircraft position to anyone
- No protection against status data manipulation
- Delay notifications contain sensitive operational data

**Your Challenge:**
- Remove passenger data from public API
- Restrict tracking data access (authenticated only)
- Add data integrity checks (prevent tampering)
- Sanitize notifications (remove internal info)

**Success Criteria:** Show public API doesn't leak sensitive data

---

### Gamerunner Tips for Scenario 4

**Pacing:**
- Minute 0-5: Announce breach discovery, explain urgency
- Minute 5-50: Directors audit and patch vulnerabilities
- Minute 50-60: Security review demos

**Evaluation:**
- Did they identify at least 2 vulnerabilities?
- Did they actually fix them? (show before/after)
- Can they explain the security risk?

**Making it realistic:**
- Drop hints about common vulnerabilities during tutorial
- Mention real breaches (Equifax, Target) for context
- Emphasize that security is not optional in production

**Educational value:**
- Teaches OWASP Top 10 concepts
- Forces thinking about threat models
- Introduces security best practices

**Variations:**
- Easy mode: Give specific vulnerabilities to find
- Hard mode: "Find ALL vulnerabilities, we're counting"
- Collaborative: Allow directors to help each other security audit

---

## Scenario 5: "Acquisition Interest - Tech Giant Due Diligence"

**Narrative Setup (Gamerunner reads aloud):**

> "CONFIDENTIAL. This stays in the room.
>
> The CEO just got off a call with Google. They want to acquire SkywardAI for $500 million.
>
> Here's the situation: Their technical due diligence team arrives in 90 MINUTES. They're going to grill each of you on your systems. They'll ask: Is this production-ready? Is it scalable? Is the code quality acceptable? Would Google engineers want to maintain this?
>
> If we pass due diligence, we're all about to get very rich. If we fail... the offer disappears and we go back to chasing Series B funding.
>
> The CEO's directive: 'Make your systems look like they were built by a tier-1 engineering team. Documentation, tests, clean code, scalability story. You have 90 minutes to prove SkywardAI is worth half a billion dollars.'
>
> This is your exit. Don't blow it."

**Time Pressure:** 60-90 minutes to prepare for technical due diligence

---

### Department-Specific Due Diligence Requirements

#### 1. Director of Customer Booking Portal
**What Google will ask:**
- "Show us your test coverage" (do you have tests?)
- "How does this scale to 10M users?" (performance strategy)
- "Walk us through the architecture" (can you explain it?)
- "Show us error handling" (what happens when things break?)

**Your Challenge:**
- Add test coverage (at least critical path tests)
- Document scaling strategy (caching, load balancing, CDN)
- Create architecture diagram
- Demonstrate comprehensive error handling

**Success Criteria:** Present professional docs and answer scaling questions confidently

---

#### 2. Director of Flight Inventory & Scheduling
**What Google will ask:**
- "How do you prevent race conditions on seat inventory?"
- "What's your data consistency strategy?"
- "Show us your monitoring and alerting"
- "How do you handle peak traffic (holidays)?"

**Your Challenge:**
- Explain/implement locking mechanism for seat bookings
- Document consistency guarantees
- Add basic monitoring/health checks
- Write scaling plan for 100x traffic

**Success Criteria:** Show you've thought through production concerns

---

#### 3. Director of Pricing & Revenue Optimization
**What Google will ask:**
- "What's the algorithmic complexity of your pricing engine?"
- "How do you A/B test pricing changes?"
- "Show us your pricing data pipeline"
- "What's your ML strategy?" (even if you're not using ML yet)

**Your Challenge:**
- Document algorithm and complexity analysis
- Design A/B testing framework (even if not implemented)
- Create data flow diagram
- Write ML roadmap (future vision)

**Success Criteria:** Demonstrate technical sophistication and vision

---

#### 4. Director of Personalization & Recommendations
**What Google will ask:**
- "What's your recommendation algorithm?"
- "How do you measure recommendation quality?"
- "Show us your data science infrastructure"
- "How do you handle cold start problem?"

**Your Challenge:**
- Document recommendation approach (rule-based or ML)
- Define success metrics (CTR, conversion)
- Show data pipeline architecture
- Explain cold start strategy

**Success Criteria:** Sound like you know what you're doing (even with simple rules)

---

#### 5. Director of Customer Service & Support
**What Google will ask:**
- "How do you scale support to 1M users?"
- "What's your chatbot's NLP strategy?"
- "Show us your ticket routing logic"
- "How do you measure support quality?"

**Your Challenge:**
- Write scaling plan (self-service, automation)
- Document chatbot logic (even if simple)
- Explain ticket prioritization
- Define support KPIs (response time, CSAT)

**Success Criteria:** Prove you've thought about scale and quality

---

#### 6. Director of Marketing & Growth
**What Google will ask:**
- "Show us your growth model" (CAC, LTV, unit economics)
- "How do you attribute conversions?"
- "What's your A/B testing framework?"
- "Explain your marketing data warehouse"

**Your Challenge:**
- Create growth model with metrics
- Document attribution logic
- Design A/B testing approach
- Show analytics architecture

**Success Criteria:** Speak Google's language (data-driven growth)

---

#### 7. Director of Check-in & Boarding
**What Google will ask:**
- "How do you handle offline mobile check-in?"
- "What's your QR code collision strategy?"
- "Show us boarding optimization algorithm"
- "How does this integrate with airport systems?"

**Your Challenge:**
- Design offline-first strategy
- Explain QR code uniqueness guarantees
- Document boarding logic
- Show integration architecture (even if mocked)

**Success Criteria:** Demonstrate systems thinking and production readiness

---

#### 8. Director of Flight Status & Tracking
**What Google will ask:**
- "How real-time is your tracking?" (latency SLAs)
- "What's your data source strategy?"
- "Show us your mapping and geolocation logic"
- "How do you handle stale data?"

**Your Challenge:**
- Define latency SLAs (update every 30s, 1min?)
- Document data sources and refresh strategy
- Explain geolocation implementation
- Add staleness detection and fallbacks

**Success Criteria:** Show production-grade thinking about real-time systems

---

### Gamerunner Tips for Scenario 5

**Pacing:**
- Minute 0-10: Announce acquisition, build excitement
- Minute 10-70: Directors prepare documentation and demos
- Minute 70-90: Technical due diligence presentations

**Evaluation:**
- Quality of documentation (architecture diagrams, scaling plans)
- Ability to answer tough technical questions
- Professional presentation skills
- Evidence of production-ready thinking

**Roleplaying Google Engineers:**
As gamerunner, play tough but fair Google tech leads:
- Ask probing questions: "What happens when Redis goes down?"
- Challenge assumptions: "Why Flask not FastAPI?"
- Appreciate good engineering: "Excellent use of caching here"
- Point out gaps: "I don't see any tests..."

**Making it fun:**
- Award "acquisition bonus points" for exceptional presentations
- Let directors ask each other tough questions (peer review)
- Celebrate the acquisition at the end (everyone gets rich!)

**Educational value:**
- Teaches what "production-ready" actually means
- Forces documentation and system design thinking
- Introduces concepts like SLAs, monitoring, scaling
- Simulates real technical interviews

**Variations:**
- Easy mode: Provide documentation templates
- Hard mode: Google engineers are very skeptical, hard to impress
- Collaborative: Directors can help document each other's systems
- Realistic: Some systems pass, some fail due diligence (creates stakes)

---

## Scenario 6: "Market Crash - Travel Industry Downturn"

**Narrative Setup (Gamerunner reads aloud):**

> "EMERGENCY BOARD MEETING. 6:00 AM.
>
> The CEO's voice is shaking: 'I'll cut to the chase. A global crisis just hit. Travel bookings collapsed 80% overnight. Airlines are grounding fleets. Hotels are closing. The entire travel industry is in freefall.
>
> Our burn rate gives us 60 days of runway. Investors are panicking. The board is talking about shutdown.
>
> But here's what I told them: We adapt or we die. We have ONE HOUR to pivot this company. Each department - figure out how to survive in a world where nobody's flying.
>
> Ideas I'm hearing: Virtual travel experiences. Travel credits for future. Refund automation. Budget travel focus. Staycations. I don't care what you build - just make sure we're still relevant when this crisis ends.
>
> Prove we can survive this. Go.'"

**Time Pressure:** 60 minutes to pivot and demonstrate survival strategy

**Note:** This is an economic/market crisis, not a technical crisis. Success = business adaptation, not just code.

---

### Department-Specific Survival Challenges

#### 1. Director of Customer Booking Portal
**Market Reality:**
- 80% drop in flight searches
- Customers want refunds, not new bookings
- Fear of travel, need confidence-building

**Your Survival Challenge:**
- Add "Book Now, Travel Later" feature (flexible dates, no penalty changes)
- Prominent refund/credit request flow
- Safety assurance messaging ("We'll be here when you're ready to fly again")
- Pivot to staycation/domestic travel focus

**Success Criteria:** Show adapted booking flow emphasizing flexibility and safety

---

#### 2. Director of Flight Inventory & Scheduling
**Market Reality:**
- Airlines canceling 70% of routes
- Massive inventory shrinkage
- Need to optimize scarce capacity

**Your Survival Challenge:**
- Focus on essential routes only (medical, cargo, repatriation)
- Add "notify me when this route returns" feature
- Create capacity optimization for reduced schedules
- Partner inventory display (buses, trains as alternatives)

**Success Criteria:** Show optimized schedule for crisis mode + alternative transport

---

#### 3. Director of Pricing & Revenue Optimization
**Market Reality:**
- Price wars as airlines desperate for revenue
- Budget-conscious customers only
- Need to maximize revenue from minimal bookings

**Your Survival Challenge:**
- Ultra-budget pricing tier (no-frills fares)
- Travel credit incentives (book now, use later discounts)
- Price freeze guarantees ("Lock this price for next year")
- Loyalty bonus system (reward customers who still book)

**Success Criteria:** Show crisis pricing strategy with multiple affordability options

---

#### 4. Director of Personalization & Recommendations
**Market Reality:**
- Nobody wants flight recommendations right now
- Need to keep users engaged without pressuring to book
- Future travel inspiration, not immediate sales

**Your Survival Challenge:**
- Pivot to "Dream Trip Planner" (wishlist for post-crisis travel)
- Virtual travel content (360° destination videos, travel blogs)
- "When travel returns" notification system
- Gift card recommendations (support the industry now, travel later)

**Success Criteria:** Show engagement strategy that doesn't push booking

---

#### 5. Director of Customer Service & Support
**Market Reality:**
- Support ticket volume up 500% (refund requests, cancellations, panic)
- Staff may be reduced
- Need to handle crisis with empathy

**Your Survival Challenge:**
- Self-service refund/credit automation (reduce support load)
- Crisis FAQ chatbot ("What are my options?")
- Empathy-first messaging templates
- Bulk cancellation tools (handle many requests fast)

**Success Criteria:** Show automated crisis support with empathetic tone

---

#### 6. Director of Marketing & Growth
**Market Reality:**
- Marketing budget slashed 90%
- Can't advertise "Book flights!" in a crisis
- Need to maintain brand without insensitive messaging

**Your Survival Challenge:**
- Pivot to community support messaging ("We're here for you")
- User-generated content (share favorite travel memories)
- Travel credits promotional campaign (invest in future travel)
- Partner with health/safety organizations (build trust)

**Success Criteria:** Show crisis-appropriate marketing that builds loyalty, not bookings

---

#### 7. Director of Check-in & Boarding
**Market Reality:**
- Minimal flights operating
- Health screening requirements
- Contactless everything

**Your Survival Challenge:**
- Health questionnaire integration
- Contactless check-in (QR codes, mobile-only)
- Social distancing seat assignment
- Travel health status tracking

**Success Criteria:** Show health-safe check-in process

---

#### 8. Director of Flight Status & Tracking
**Market Reality:**
- Mass cancellations, constant schedule changes
- Customers anxious about flight viability
- Repatriation flight tracking critical

**Your Survival Challenge:**
- Cancellation probability predictor ("95% chance this flight operates")
- Alternative flight finder (automatic rebooking suggestions)
- Travel advisory integration (government restrictions, quarantines)
- Emergency flight alerts (last flights home)

**Success Criteria:** Show proactive crisis communication and rebooking

---

### Gamerunner Tips for Scenario 6

**Pacing:**
- Minute 0-5: Announce crisis, let gravity sink in
- Minute 5-50: Directors pivot and build survival features
- Minute 50-60: Pitch survival strategies to board (gamerunner)

**Evaluation:**
- Did they adapt to crisis reality? (not just business as usual)
- Do solutions show empathy and understanding?
- Is the pivot believable for the crisis?
- Would customers trust this company in a downturn?

**Roleplaying the Board:**
As gamerunner, play concerned investors:
- Challenge weak pivots: "People aren't flying - why would they buy travel credits?"
- Appreciate empathy: "This messaging feels right for the moment"
- Ask tough questions: "How does this generate revenue?"
- Recognize creativity: "Virtual travel experiences - that's thinking outside the box"

**Making it realistic:**
- Reference real crisis events (COVID, 9/11, financial crashes)
- Emphasize empathy over optimization
- Reward solutions that balance survival with humanity
- Discuss ethical considerations (layoffs, pricing during crisis)

**Educational value:**
- Teaches crisis management and business resilience
- Forces strategic thinking beyond technical execution
- Introduces concept of product-market fit shifts
- Discusses ethical leadership in hard times

**Emotional notes:**
- This scenario can be heavy - some participants lived through COVID travel crisis
- Balance realism with optimism ("we'll survive this together")
- Celebrate creative pivots and adaptation
- End with hope: "The industry always recovers"

**Variations:**
- Easy mode: Provide specific pivot ideas upfront
- Hard mode: 90% booking drop, 30-day runway (more desperate)
- Collaborative: Departments must coordinate survival strategy
- Realistic: Some pivots fail, have to try again (iteration)

**Post-scenario debrief:**
- Discuss real company responses to travel crises
- What worked? What felt forced?
- How did it feel to pivot under pressure?
- Lessons for real-world crisis management

---

## Scenario Selection Guide

**Use Scenario 1 (Competitor Attack) when:**
- Group is competitive and energetic
- You want maximum drama and engagement
- Q3 or Q4 timing
- Want to teach product differentiation and rapid response

**Use Scenario 2 (Enterprise Deal) when:**
- Q3 timing (builds momentum toward launch)
- Want to teach B2B thinking and business value
- Group is less comfortable with pure pressure (this is an opportunity, not crisis)
- Want directors to practice "selling" their work

**Use Scenario 3 (Regulatory Audit) when:**
- Want to teach real-world requirements (privacy, accessibility)
- Group includes junior engineers (high educational value)
- Time is flexible (can be 45-60 min)
- Want less pressure, more thoughtful feature-building

**Use Scenario 4 (Security Breach) when:**
- Want to teach security best practices and threat modeling
- Q3 or Q4 timing (works either way)
- Group needs to learn OWASP Top 10 concepts
- Want high-stakes pressure with clear technical focus
- Engineers will build production systems (practical skill)

**Use Scenario 5 (Acquisition Due Diligence) when:**
- Q4 timing (perfect as final challenge before launch)
- Want to teach "production-ready" thinking (tests, docs, scaling)
- Group is performing well (this is aspirational/positive pressure)
- Want to emphasize system design and technical communication
- Engineers will interview at tech giants (teaches what they look for)

**Use Scenario 6 (Market Crash) when:**
- Want to teach crisis management and business resilience
- Q3 or Q4 timing (works as major disruption)
- Group needs to think beyond technical execution (strategic business thinking)
- Want to discuss ethical leadership and empathy in crisis
- Realistic pressure (economic downturns happen in real companies)

---

## Mixing Scenarios

**Option 1: Use one scenario across both Q3 and Q4**
- Q3: Enterprise customer expresses interest
- Q4: Enterprise customer returns with final requirements before signing

**Option 2: Use different scenarios in Q3 and Q4**
- Q3: Enterprise deal (positive pressure, feature building)
- Q4: Competitor attack (defensive pressure, rapid response)
- Q3: Security breach (find and fix vulnerabilities)
- Q4: Acquisition due diligence (prove you're production-ready)

**Option 3: Escalating narrative**
- Q3: Regulatory audit (build compliance features)
- Q4: Security breach (prove compliance under pressure)
- Q3: Competitor attack (ship competitive features)
- Q4: Acquisition interest (Google wants to buy because you beat competitor)

**Option 4: Educational arc (recommended for junior engineers)**
- Q3: Regulatory audit (learn compliance and accessibility)
- Q4: Security breach (learn security best practices)

**Option 5: Pressure arc (recommended for experienced engineers)**
- Q3: Competitor attack or Enterprise deal
- Q4: Acquisition due diligence (ultimate pressure - prove you're worth $500M)

**Option 6: Crisis survival arc**
- Q3: Market crash (economic crisis, pivot to survive)
- Q4: Acquisition due diligence (recovery - prove you survived and thrived)

**Option 7: Chaos arc (roll dice for both)**
- Q3: Roll d6 for random scenario
- Q4: Roll d6 again for different random scenario
- Maximum unpredictability and variety

**Option 8: Let directors vote**
- After Q2 investor demo, reveal all 6 scenario options
- Directors vote on which challenges they want for Q3 and Q4
- Gives player agency

---

## Creating Your Own Scenarios

**Universal Scenario Template:**

1. **Create compelling narrative** (CEO announcement, breaking news, crisis)
2. **Define 8 department-specific challenges** (one per director role)
3. **Set clear success criteria** per department
4. **Choose time pressure** (30-60 minutes)
5. **Plan demo format** (how will directors show their response?)

**Requirements:**
- Every director must have something meaningful to do
- Challenges should be achievable in time limit
- Success criteria should be demoable (visual, working software)

---

*Document created: March 31, 2026*
*Last updated: March 31, 2026*
*Design principle: Every chaos scenario must engage all 8 directors with specific, actionable challenges*
*Total scenarios: 6 (Competitor Attack, Enterprise Deal, Regulatory Audit, Security Breach, Acquisition Due Diligence, Market Crash)*
*Use a d6 to randomly select, or choose based on group needs!*
