# GAMERUNNER GUIDE
## Terminal Velocity: Running a Multi-Agent Coding Workshop

This guide contains everything you need to facilitate Terminal Velocity - scoring rubrics, dice mechanics, evaluation criteria, and facilitation tips.

---

## TABLE OF CONTENTS

1. [Pre-Game Setup](#pre-game-setup)
2. [Timeline & Structure](#timeline--structure)
3. [Turn-by-Turn Facilitation](#turn-by-turn-facilitation)
4. [Scoring & Evaluation](#scoring--evaluation)
5. [Randomness & Dice Mechanics](#randomness--dice-mechanics)
6. [Performance Review](#performance-review)
7. [Troubleshooting](#troubleshooting)
8. [Materials Checklist](#materials-checklist)

---

## PRE-GAME SETUP

### 1 Week Before Workshop

**Send to participants:**
- [ ] Character sheets (characters/ directory)
- [ ] GAME.md overview
- [ ] Tech requirements (Claude access, laptop with dev environment)
- [ ] Pre-reading: MULTI-SERVICE-GUIDE.md

**Prepare materials:**
- [ ] Print character sheets (1 per role)
- [ ] Print scoring sheets (track metrics per director)
- [ ] Prepare dice (1d6 for randomness)
- [ ] Set up demo timer/clock (visible to all)
- [ ] Prepare whiteboard/screen for company timeline
- [ ] Test screen sharing setup for demos

### 30 Minutes Before Workshop

**Environment Setup:**
- [ ] Assign seating (directors at separate tables/areas)
- [ ] Verify everyone has Claude access
- [ ] Test screen sharing for demos
- [ ] Display company timeline on whiteboard
- [ ] Prepare music playlist for build time (optional)

### Tutorial Session (30 minutes before game starts)

Run a hands-on Claude tutorial:

**Part 1: Basic Agent Use (10 min)**
```
Demo Prompt: "Build a simple Flask API with one endpoint
that returns 'Hello from SkywardAI'. Run on port 5000."

Show:
- How to phrase clear prompts
- How to iterate ("Now add error handling")
- How to test agent output
```

**Part 2: Multi-Agent Basics (10 min)**
```
Demo: Start 2 agents in parallel

Agent 1: "Build a simple database schema for flights..."
Agent 2: "Build a simple frontend form..."

Show:
- Managing multiple conversations
- When to use parallel vs sequential
- How to integrate outputs
```

**Part 3: Common Pitfalls (10 min)**
- Vague prompts → vague results
- Not testing before demo
- Losing track of which agent is which
- Copy-pasting without understanding

**Practice Round (Optional):**
Give everyone 5 minutes to build "Hello World" API with agents

---

## TIMELINE & STRUCTURE

### Full Day Format (7 hours total)

```
09:00 - 09:30  Tutorial (Claude basics)
09:30 - 10:30  Q1: Foundation (60 min)
10:30 - 11:30  Q2: Features (60 min)
11:30 - 12:00  Investor Demo & Feedback (30 min)

12:00 - 13:00  LUNCH BREAK

13:00 - 14:00  Q3: Integration (60 min)
14:00 - 15:00  Q4: Launch Prep (60 min)
15:00 - 15:30  Q5: Crisis (30 min, dice roll)
15:30 - 16:00  Q6: Chaos (30 min, dice roll)
16:00 - 16:30  Performance Review & VP Promotion
```

### Quarter Time Allocations

**Q1 (60 minutes) - Research & Vision:**
- 5 min: Introduction (explain Q1 is planning, not coding)
- 50 min: Research and planning with agents
- 5 min: Vision presentation (30 sec per director)

**Q2 (60 minutes) - Investor Demo Build:**
- 5 min: Scenario introduction
- 50 min: Build with agents
- 5 min: Quick progress check

**Investor Demo (30 minutes after Q2):**
- 2 min: Setup and instructions
- 18 min: Presentations (3 min each × 6 directors)
- 10 min: Investor feedback and scoring

**Q3-Q4 (60 minutes each):**
- 5 min: Scenario introduction
- 45 min: Build with agents
- 10 min: Demo & feedback (1-2 min per director)

**Q5-Q6 (30 minutes each):**
- 2 min: Dice roll + scenario reveal
- 23 min: Emergency response with agents
- 5 min: Demo & assessment

---

## TURN-BY-TURN FACILITATION

### Quarter 1: Research & Vision (60 min)

**Objective:** Directors plan their strategy, NOT build working code yet

**IMPORTANT:** Q1 is about research, planning, and vision. Directors should use agents for strategic work (research, requirements, wireframes, architecture), not coding. Some may choose to build a simple MVP, but most should focus on planning.

**Scenario Intro (5 min):**
> "Welcome to SkywardAI, directors. Before we build, we need to plan. You have 60 minutes to research, strategize, and create a vision for your department.
>
> Your deliverable options:
> - Vision document with architecture and wireframes
> - Detailed wireframes and user flows
> - Simple MVP prototype (if you want to code)
>
> In Q2, you'll build for investors based on this vision. Use this time wisely to plan your approach."

**Key Messages:**
- "Don't rush to code - use agents to research and plan"
- "Think about 2-3 services you'll build in Q2-Q4"
- "Create wireframes, architecture diagrams, vision docs"
- "If you build an MVP, keep it VERY simple"

**During Planning Time (50 min):**
- Circulate and check: Are they using the right agents? (PM, BA, UX, Architect)
- Watch for: Jumping to coding too early
- Encourage: "Use a Business Analyst agent to define requirements first"
- Remind at 30 min, 15 min, 5 min marks
- Look for: Vision docs forming, wireframes being created

**Vision Presentations (5 min total):**
- Each director: 30 seconds to present their vision
- Show wireframes, architecture, or MVP
- Explain strategy for Q2-Q4
- **No scoring in Q1** - just feedback and encouragement
- Feedback: "Clear vision!" / "Good architecture!" / "Solid plan for Q2"

**Common Issues Q1:**
- Rushing to code instead of planning
  - Fix: "Use Q1 to plan, Q2 to build"
- Not using research/planning agents
  - Fix: "Try a PM agent to define your vision first"
- Unclear deliverables
  - Fix: "Show us a vision doc or wireframes"

**What Success Looks Like Q1:**
- Director has clear plan for their 2-3 services
- Wireframes or architecture diagrams created
- Vision for Q2-Q4 is articulated
- They understand which agents to use for building in Q2

---

### Quarter 2: Investor Demo Build (60 min)

**Objective:** Build something impressive to show investors in 30 minutes

**IMPORTANT:** This is the first major build quarter. Directors should execute on their Q1 vision and build 1-2 working services that demo well.

**Scenario Intro (5 min):**
> "Investors are coming in 60 minutes. They need to see working systems, not plans. Build 1-2 services from your Q1 vision that demonstrate real value. Make it look good - investors care about polish.
>
> Focus on:
> - Working core functionality
> - Professional appearance
> - Clear value proposition
> - Impressive demo"

**Key Messages:**
- "Execute on your Q1 plan"
- "Build what investors want to see"
- "Polish matters - make it look production-ready"
- "Core flow working > many features broken"

**During Build Time (50 min):**
- Directors should be using Backend/Frontend dev agents now
- Watch for: Over-complicating, trying to build too much
- Encourage: "Focus on one impressive flow that works"
- Remind at 30 min, 15 min, 5 min marks
- Check: Are they testing their demo flow?

**Progress Check (5 min):**
- Quick 30-second check-ins (not full demos)
- "What are you demoing to investors?"
- "Does your core flow work?"
- **No scoring yet** - that happens in Investor Demo

**Common Issues Q2:**
- Building too many features, nothing works
  - Fix: "Pick your best feature, make it perfect"
- Not testing before investor demo
  - Fix: "Test your demo flow NOW"
- Ignoring Q1 vision, starting from scratch
  - Fix: "Use your Q1 architecture as a guide"

**What Success Looks Like Q2:**
- 1-2 services are working
- Core user flow is demoable
- UI looks professional
- Director is confident about investor demo

**Next:** Investor Demo (see section below)

---

### Investor Demo (30 min at end of Q2)

**This is the mid-game climax - make it dramatic!**

**Setup (2 min):**
> "The investors are here. Each director will present their department's progress. You have 3 minutes each. Impress them, or our funding disappears."

**Presentations (18 min = 3 min × 6 directors):**
Each director presents:
1. What they built (demo)
2. Key features
3. Tech approach (multi-agent strategy used)

**Investor Deliberation (5 min):**
- You (as investors) evaluate using rubric below
- Calculate scores
- Prepare feedback

**Feedback (5 min):**
- Announce scores publicly
- Provide narrative feedback per director
- Set expectations for Year 2

**→ LUNCH BREAK**

---

### Quarter 3: Integration (60 min)

**Scenario Intro (5 min):**
> "Post-lunch, refreshed. The investors want to see this become a real company. Your systems need to work together. Build at least one integration point with another director's service."

**During Build Time (45 min):**
- Encourage (but don't force) real API integration
- Mock integration is acceptable
- Watch for: networking issues, CORS, port conflicts

**Demo (10 min):**
- 1-2 min per director
- Show integration points
- Track delivery score

---

### Quarter 4: Launch Prep (60 min)

**Scenario Intro (5 min):**
> "Launch day is in 60 minutes. Polish your systems. This is the last chance before we go live. Make it production-ready."

**During Build Time (45 min):**
- Directors focus on polish, bug fixes, UX improvements
- Encourage: error handling, edge cases, visual refinement

**Demo (10 min):**
- Full 2 min per director
- This is the "launch demo" - make it ceremonial
- **Track delivery score**
- **Announce: Company has launched!** 🎉

**Transition:**
> "Congratulations, SkywardAI is live! But the real challenges are just beginning..."

---

### Quarter 5: Crisis (30 min - DICE DRIVEN)

**Dice Roll (2 min):**
- Roll 1d6 publicly
- Announce crisis from table below
- Directors react in real-time

**Crisis Response (23 min):**
- Directors scramble to address crisis
- This should feel urgent, chaotic
- Play ticking clock sound (optional)

**Assessment (5 min):**
- Quick demo: did they solve it?
- **Track delivery score** (penalty if unresolved)

---

### Quarter 6: Final Chaos (30 min - DICE DRIVEN)

**Dice Roll (2 min):**
- Roll 1d6 again
- Announce second crisis
- Emphasize: "This is your last quarter to prove yourselves"

**Final Push (23 min):**
- Directors give it their all
- Watch for: creative solutions, collaboration

**Final Demo (5 min):**
- Last chance to impress
- **Track delivery score**

---

### Performance Review (30 min)

**Calculate Final Scores (10 min):**
- Use formula from scoring section
- Tally: Delivery + Tech Debt + API Cost + Collaboration

**Awards Ceremony (10 min):**
- Announce scores one by one (build suspense)
- Give feedback per director
- Special awards: Most Innovative, Most Efficient, Best Team Player

**VP Promotion Announcement (5 min):**
> "The board has made their decision. The new VP of Engineering is... [winner]!"

**Retrospective (5 min):**
- What did you learn about multi-agent orchestration?
- What would you do differently?
- Will you use this at work?

---

## SCORING & EVALUATION

### Delivery Score (Tracked Each Quarter)

**After each demo, rate 1-3:**

**3 Points: Exceptional**
- Demo works flawlessly
- Impressive features or UX
- Handles edge cases
- Innovation evident
- Clearly spent time polishing

**2 Points: Good**
- Demo works for happy path
- Core functionality present
- Some rough edges acceptable
- Meets requirements

**1 Point: Needs Work**
- Partially working
- Significant bugs or missing features
- Minimal progress since last quarter
- Doesn't meet scenario goals

**0 Points: Not Demo-able**
- Nothing works
- No visible progress
- (Rare - provide heavy support before this happens)

**Cumulative Delivery Score = Sum of all quarters (max 18 points if all 6 demos are exceptional)**

---

### Investor Demo Rubric (Q2 Mid-Game Evaluation)

**Score each director on 4 dimensions (10 points total):**

**1. Technical Quality (3 points)**
- 3: Works perfectly, handles edge cases, robust
- 2: Works for happy path, minor bugs acceptable
- 1: Partially working, significant issues
- 0: Broken or not functional

**2. Business Value (3 points)**
- 3: Addresses core customer need, impressive features, clear value prop
- 2: Basic functionality, meets requirements, useful
- 1: Minimal features, unclear value
- 0: No clear business value

**3. Presentation (2 points)**
- 2: Clear, confident, tells a compelling story, good demo flow
- 1: Functional but dry, unclear explanation
- 0: Confusing, disorganized, or broken demo

**4. Innovation (2 points)**
- 2: Creative solution, surprising feature, technical sophistication
- 1: Solid but predictable, follows obvious patterns
- 0: Generic, no originality

**Total: /10 points per director**

**Narrative Feedback Templates:**

**8-10 points:**
> "Exceptional work, [Director]. The investors are very impressed with [specific feature]. We're doubling down on your department."

**5-7 points:**
> "Good progress, [Director]. We see potential in [aspect], but we expected more [missing element]. Show us stronger results in Year 2."

**3-4 points:**
> "We have concerns about [department]. The [specific issue] needs immediate attention. Can you turn this around?"

**0-2 points:**
> "This is unacceptable, [Director]. [Specific problem] must be resolved or we'll need to make changes."

---

### Tech Debt Scoring

**Measure at end of game (after Q6):**

**Method: Agent Code Review**

For each director, use Claude to review their codebase:

```
Prompt: "Review this codebase for technical debt.
Evaluate on a 0-10 scale where:
- 0-3: High debt (no tests, hardcoded values, no error handling, poor structure)
- 4-7: Moderate debt (some tests, basic structure, some shortcuts taken)
- 8-10: Low debt (comprehensive tests, clean code, production-ready, well-documented)

Code: [paste all services here]

Provide:
1. Overall score (0-10)
2. Specific debt issues found
3. What would need fixing for production
"
```

**Quick Manual Checklist (if agent review not feasible):**
```
No tests? +3 debt
Hardcoded secrets/config? +2 debt
No error handling? +2 debt
Code duplication? +2 debt
No documentation? +1 debt
Poor naming/structure? +1 debt
Security issues? +3 debt

Total Debt Score = Sum of penalties (max ~15)
```

**Tech Debt Final Score = 15 - actual_debt**
(So low debt = high score)

---

### API Cost Tracking

**Track Claude API usage per director:**

**Method 1: Manual Logging**
- Directors self-report estimated agent conversations
- Estimate: $0.50 per complex agent task
- Track on scoring sheet

**Method 2: Actual API Costs (if using API keys)**
- Check actual costs via Anthropic console
- Attribute to directors based on logged conversations

**Typical Costs:**
- Efficient: $10-20 for full game
- Average: $25-40 for full game
- Expensive: $50+ for full game

**Cost Score Calculation:**
```
If cost <= $20: Cost Score = 10
If cost $21-40: Cost Score = 7
If cost $41-60: Cost Score = 4
If cost > $60: Cost Score = 1
```

---

### Collaboration Bonus

**Award points for collaborative behavior:**

**+5 points:** Helped 2+ directors significantly (spent >10 min debugging their issues, shared code/patterns)

**+3 points:** Helped 1 director or shared valuable insights in group discussions

**+1 point:** Good team player, responsive to questions

**0 points:** Worked in isolation, didn't collaborate

**-2 points:** Negative behavior (refused to help, blamed others, etc.)

**Track during game:** Note when directors help each other

---

### Final Score Formula

```
FINAL SCORE =
  (Delivery Score)
  + (Tech Debt Score)
  + (Cost Score)
  + (Collaboration Bonus)

Maximum possible: 18 + 15 + 10 + 5 = 48 points
```

**Example:**

**Director A:**
- Delivery: Q1(2) + Q2(3) + Q3(2) + Q4(3) + Q5(2) + Q6(3) = 15
- Tech Debt: 12 (moderate, some shortcuts)
- Cost: 7 ($35 spent)
- Collaboration: +5 (helped 2 directors)
- **TOTAL: 39 points**

**Director B:**
- Delivery: 2 + 2 + 2 + 2 + 1 + 2 = 11
- Tech Debt: 14 (low debt, very clean)
- Cost: 10 ($18 spent - very efficient)
- Collaboration: +3 (helped 1 director)
- **TOTAL: 38 points**

**Director A wins!** (prioritized delivery over perfection)

---

## RANDOMNESS & DICE MECHANICS

### Crisis Table (Q5-Q6)

**At start of Q5 and Q6, roll 1d6:**

**Roll: 1 - CRITICAL BUG**
```
Scenario: "PRODUCTION OUTAGE! A critical bug in [random department's]
system caused a cascading failure. All customer bookings from the
past hour are corrupted.

Challenge: Emergency hotfix required within 30 minutes.
Penalty: -2 delivery score if not resolved
Opportunity: +1 delivery score if you help fix it (even if not your bug)
"
```

**Roll: 2 - COMPETITOR ATTACK**
```
Scenario: "MegaAir just launched [specific feature] that we promised
for next quarter. Tech press is saying we're behind.

Challenge: Ship a competitive feature NOW, or pivot to something better.
Penalty: -1 delivery score if you ignore this
Opportunity: +2 delivery score if you ship something innovative that leapfrogs them
"
```

**Roll: 3 - REGULATORY AUDIT**
```
Scenario: "Government regulators announced a surprise audit on data
privacy and accessibility. We have 30 minutes to demonstrate compliance
or face a $500K fine and PR disaster.

Challenge: Implement basic GDPR/accessibility features
Penalty: -2 delivery score for non-compliance
Opportunity: +1 collaboration bonus if departments work together on compliance
"
```

**Roll: 4 - VIRAL TRAFFIC SPIKE**
```
Scenario: "A celebrity with 10M followers just tweeted 'Finally, an
airline that doesn't suck!' linking to our site. Traffic is 50x normal.
Systems are buckling.

Challenge: Implement caching, optimization, or graceful degradation
Penalty: -1 delivery score if systems crash visibly
Opportunity: +2 delivery score if you handle it elegantly
"
```

**Roll: 5 - BUDGET CRISIS**
```
Scenario: "VC funding round fell through. Emergency cost-cutting measures.
Your API budget for this quarter is CUT IN HALF.

Challenge: Build with 50% fewer agent tasks (or spend your own allocation)
Penalty: -3 cost score if you exceed budget anyway
Opportunity: +2 cost score if you deliver well under budget
"
```

**Roll: 6 - PARTNERSHIP OPPORTUNITY**
```
Scenario: "Expedia wants to integrate with us! If we can provide
a working API that [2 random departments] integrate with within 30 minutes,
we get a $2M partnership deal.

Challenge: Cross-department real-time integration required
Penalty: None (this is pure upside)
Opportunity: +3 collaboration bonus if successful, +2 delivery score each
"
```

**Gamerunner Note:** Adapt scenarios to what directors have actually built. Make it personal and specific.

---

### Chaos Modifiers (Optional)

For extra drama in Q5-Q6, add random modifiers:

**Advantage Rolls (good luck):**
- "Your intern just pushed perfect code" → +5 min extra time
- "Competitor's site went down" → Ignore competitor pressure
- "Investor surprise visit" → +1 bonus point if demo impresses

**Disadvantage Rolls (bad luck):**
- "Your laptop crashed" → Lose first 5 minutes recovering
- "Claude API slowdown" → Agents respond 2x slower
- "Coffee machine broken" → -1 morale (just for flavor)

---

## PERFORMANCE REVIEW

### Conducting the Review (30 min at end)

**Phase 1: Score Calculation (10 min)**
- Tally all scores on whiteboard/screen
- Show formula transparently
- Directors can see everyone's breakdown

**Phase 2: Individual Feedback (15 min)**

Go through each director one by one:

**Feedback Template:**
```
"[Director Name], Director of [Department]:

Your delivery score was [X/18]. You consistently [pattern observed].
Your best quarter was Q[Y] when you [specific achievement].

Your tech debt score was [X/15]. [Specific code quality observation].

Your cost efficiency was [X/10]. You spent [amount] on API costs,
which shows [efficiency/over-use].

Collaboration: [observation about teamwork]

Your total score: [XX/48]

What you did well: [2-3 specific things]
What to improve: [1-2 specific things]
"
```

**Phase 3: VP Announcement (5 min)**

Build suspense:
```
"The board has deliberated. This was a close race.

In third place with [X] points: [Director C]
In second place with [X] points: [Director B]

And your new VP of Engineering, with [X] points: [Director A]!

Congratulations, [Director A]. You demonstrated [key strength].
Everyone else: outstanding work. You're all promoted to Senior Directors.
"
```

**Phase 4: Group Reflection (Optional 10 min)**
- Most surprising multi-agent technique learned?
- What would you do differently knowing what you know now?
- Will you use multi-agent patterns at work?

---

## TROUBLESHOOTING

### Common Issues & Solutions

**Issue: Directors not using multiple agents**
**Solution:** In Q2, explicitly require: "Use at least 2 agents in parallel this quarter"

**Issue: Demos consistently fail (nothing works)**
**Solution:**
- Pause at 20-min mark, check in with each director
- Help debug, don't let them flounder
- Reduce scope aggressively

**Issue: One director way behind others**
**Solution:**
- Pair them with a faster director as "mentor"
- Give them simpler scope for current quarter
- Offer extra help during build time

**Issue: Integration breaks everything (Q3)**
**Solution:**
- Make integration optional, not required
- Suggest mocking instead of real API calls
- Provide simple integration example

**Issue: Dice rolls feel unfair**
**Solution:**
- Emphasize: randomness is learning opportunity
- Allow directors to negotiate crisis response
- Offer "re-roll" token once per game

**Issue: Running out of time**
**Solution:**
- Cut Q5-Q6 to 20 minutes each if needed
- Skip or shorten performance review
- Priority: ensure Q1-Q4 have full time

**Issue: Someone's Claude API access fails**
**Solution:**
- Have backup: pair programming with working director
- Use alternative account
- Worst case: pivot their demo to "planning" rather than building

**Issue: Competitive tension becomes toxic**
**Solution:**
- Remind: everyone is on same team (company success)
- Emphasize: all directors get promoted, only one to VP
- Celebrate collaborative moments publicly

---

## FACILITATION BEST PRACTICES

### Energy Management

**Keep energy high:**
- Play music during build time
- Celebrate milestones loudly (launch, investor demo success)
- Use dramatic language for scenarios
- Physical movement (stand, walk around) between quarters

**Manage stress:**
- Humor when things break ("Welcome to software engineering!")
- Normalize failure (agents produce bugs, that's realistic)
- Provide snacks/caffeine
- Enforce lunch break

### Narrative Techniques

**Make scenarios feel real:**
- Use NPC voices: CEO, investors, angry customers
- Create urgency: "The CEO is on the phone, she sounds stressed..."
- Personalize: "A customer named Sarah just tweeted that..."

**Build story arc:**
- Q1-Q2: Hopeful startup energy
- Investor Demo: First big test
- Q3-Q4: Growing confidence
- Q5-Q6: Chaos and resilience
- Review: Recognition and celebration

### Engagement Tactics

**Prevent checking out:**
- Call on specific directors during discussions
- Highlight interesting agent techniques publicly
- Create peer pressure (positive): "Wow, [Director X] just used 3 parallel agents!"

**Encourage collaboration:**
- When someone asks for help: "Great question, [Director Y], can you help?"
- Reward it: "I saw [Director X] help [Director Y] - that's +3 collaboration points"

**Handle competition healthily:**
- Frame as professional growth, not elimination
- "You're competing for a promotion, not your job"
- Celebrate runners-up: "Silver and bronze medalists are still olympians"

---

## MATERIALS CHECKLIST

### Required Materials

**Physical:**
- [ ] Character sheets (printed, 1 per role)
- [ ] Scoring sheets (tracking spreadsheet or paper)
- [ ] 1d6 die
- [ ] Timer/clock (visible to all)
- [ ] Whiteboard or large screen for timeline/scores
- [ ] Name tags or table cards (Director titles)

**Digital:**
- [ ] GAME.md (shared with participants)
- [ ] Character sheets (characters/ directory)
- [ ] MULTI-SERVICE-GUIDE.md (reference)
- [ ] Scoring spreadsheet (template below)

**Optional:**
- [ ] Music playlist for build time
- [ ] Printed crisis cards (instead of rolling dice)
- [ ] Awards/certificates for winners
- [ ] Claude API monitoring dashboard

### Scoring Spreadsheet Template

```
Director | Q1 | Q2 | Q3 | Q4 | Q5 | Q6 | Delivery | Inv Demo | Tech Debt | Cost | Collab | TOTAL
---------|----|----|----|----|----|----|----------|----------|-----------|------|--------|------
Alice    | 2  | 3  | 2  | 3  | 2  | 3  |    15    |    8     |    12     |  7   |   +5   |  47
Bob      | 2  | 2  | 3  | 2  | 2  | 2  |    13    |    7     |    14     |  10  |   +3   |  47
Carol    | 3  | 2  | 2  | 2  | 1  | 3  |    13    |    6     |    11     |  7   |   +1   |  38
...
```

---

## TIMING GUIDE

### If Running Behind

**Cut from:**
- Individual feedback in performance review (do group only)
- Q5-Q6 (reduce to 20 min each)
- Tutorial (assume people know Claude basics)

**Never cut:**
- Q1-Q2 (learning foundation)
- Investor demo (key milestone)
- Lunch break (people need it)
- Q4 launch (emotional high point)

### If Ahead of Schedule

**Add:**
- Longer retrospectives per quarter
- Extended investor demo Q&A
- Group code review session
- Advanced multi-agent workshop

---

## POST-GAME FOLLOW-UP

**Immediately After:**
- [ ] Send scores and feedback to all participants
- [ ] Share final code repositories
- [ ] Collect feedback survey
- [ ] Exchange contact info (for continued learning)

**1 Week Later:**
- [ ] Check-in email: "Have you used multi-agent patterns at work?"
- [ ] Share aggregated learnings
- [ ] Offer office hours for questions

**1 Month Later:**
- [ ] Follow-up survey on skill retention
- [ ] Share success stories
- [ ] Iterate on game design based on feedback

---

## SUCCESS METRICS (FOR YOU AS GAMERUNNER)

**Did it work?**
- [ ] All directors shipped working software by Q4
- [ ] Participants tried multi-agent patterns (not just single agent)
- [ ] Energy stayed high throughout (no mass checkout)
- [ ] Competitive element felt healthy (not toxic)
- [ ] Post-survey: 80%+ would recommend to colleagues

**What to improve?**
- Track: which quarters ran long?
- Track: where did directors get stuck?
- Track: which crises worked well vs fell flat?
- Track: scoring clarity (did it make sense to participants?)

---

**Good luck, Gamerunner! You're teaching engineers a skill that will shape the future of software development. Make it memorable.** 🎯✈️
