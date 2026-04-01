# GAMERUNNER GUIDE
## Skyward: Running a Silicon Valley Startup Simulator

**Welcome, Gamerunner.** You're about to guide 4-6 engineers through the chaotic, hilarious, and occasionally terrifying world of building SkywardAI - a tech startup that's either going to disrupt the airline industry or become a cautionary tale on TechCrunch.

Think less "epic fantasy quest" and more "Silicon Valley TV show meets The Office." You're not running a D&D campaign - you're simulating startup life: the all-hands meetings, the investor pitch pressure, the 2am production incidents, the existential dread when a competitor launches your exact feature.

This guide will help you create an engaging, educational, and entertainingly realistic startup experience.

---

## TABLE OF CONTENTS

1. [The Story You're Telling](#the-story-youre-telling)
2. [Pre-Game Preparation](#pre-game-preparation)
3. [Campaign Timeline](#campaign-timeline)
4. [Quarter-by-Quarter Narration](#quarter-by-quarter-narration)
5. [Scoring the Journey](#scoring-the-journey)
6. [The Dice of Fate](#the-dice-of-fate)
7. [The Final Reckoning](#the-final-reckoning)
8. [Troubleshooting Your Campaign](#troubleshooting-your-campaign)
9. [Materials & Resources](#materials--resources)

---

## THE STORY YOU'RE TELLING

### The Narrative Arc

You are narrating the **1-year journey of SkywardAI** - a scrappy airline tech startup racing to disrupt an industry. Your 4-6 players aren't just engineers writing code - they are **department directors** fighting for success, promotion, and glory.

**Act I: The Vision (Q1-Q2)**
- The company is born
- Directors must prove themselves to investors
- Tension builds toward the high-stakes Investor Demo

**Act II: The Crucible (Q3-Q4)**
- Q3 brings dice-driven chaos and disaster
- Q4 is the launch sprint where systems go live to the world
- Directors must survive crisis and deliver a production-ready platform

**Epilogue: The Ascension (Performance Review)**
- One director becomes VP of Engineering
- All others are celebrated as Senior Directors
- The tale concludes with lessons learned

### Your Role as Narrator

You're not just a facilitator - you're **every NPC in their startup simulation**:

- **The CEO** - caffeinated, optimistic, slightly unhinged ("We're going to be a unicorn!")
- **The Investors** - skeptical VCs who've seen it all ("So... how is this different from Expedia?")
- **The Customers** - real people tweeting complaints at 2am
- **The Competition** - MegaAir, the Evil Empire with infinite resources
- **The Market** - chaos incarnate, throwing random events via dice

Channel your inner Silicon Valley character. Be witty, fast-paced, and occasionally absurd. Startups are dramatic enough without pretending you're Gandalf.

---

## PRE-GAME PREPARATION

### One Week Before: Setting the Stage

Send your participants everything they need to survive startup life.

**Email to participants:**
- [ ] Character sheets - their department and role (characters/ directory)
- [ ] README.md - the rules and structure
- [ ] Tech requirements - laptop, Claude access, dev environment
- [ ] TUTORIAL.md - multi-agent orchestration guide

**Your materials:**
- [ ] Print character sheets (one per director - make them look like offer letters)
- [ ] Scoring spreadsheet (track the leaderboard)
- [ ] **Read [UNIVERSAL_CHAOS_SCENARIOS.md](UNIVERSAL_CHAOS_SCENARIOS.md)** - chaos event options
- [ ] Visible countdown timer (nothing says "startup" like artificial urgency)
- [ ] Whiteboard for company timeline
- [ ] Screen sharing setup for demos

### 30 Minutes Before: Setup

**Create the startup atmosphere:**
- Assign seats - each director gets their own workspace (separate areas if possible)
- Verify everyone can access Claude Code CLI
- Display the SkywardAI timeline on a shared screen/whiteboard
- Optional: Play lo-fi coding music during build phases
- Optional: Have snacks and energy drinks available (it's a startup, after all)

### The Tutorial: Onboarding Your Directors (30 minutes)

Before the chaos begins, teach them how to actually use Claude agents. This is their superpower for the day.

**Kick it off:**

> "Alright, Directors. Welcome to SkywardAI. You each run a department, but here's the thing - you're not writing code today. You're managing a team of Claude agents who write code for you. Think of it like being a tech lead who can instantly hire specialists.
>
> Let me show you how this works..."

**Part 1: Your First Agent (10 min)**

Show them a simple example:
```
"Build a simple Flask API with one endpoint that returns
'Hello from SkywardAI'. Run on port 5000."
```

Demonstrate:
- How to speak clearly to your agents
- How to refine their work ("Now add error handling")
- How to test what they've created

**Part 2: Coordinating Multiple Agents (10 min)**

> "But true power comes from commanding multiple agents at once. Watch as I summon two in parallel..."

Show:
```
Agent 1: "Build a database schema for flights..."
Agent 2: "Build a frontend form..."
```

Teach:
- When to run agents in parallel vs in sequence
- How to weave their outputs together
- The art of giving each agent clear purpose

**Part 3: Avoiding the Pitfalls (10 min)**

Warn them of common dangers:
- Vague instructions lead to vague results
- Never demo without testing first
- Track your agents or lose your way
- Understand what you're building, don't just copy-paste

**Optional Practice Round:**
Give them 5 minutes to summon their first agent: "Build a Hello World API"

---

## CAMPAIGN TIMELINE

### The Full Workshop (6-6.5 Hours: 10am-4pm or 4:30pm)

```
10:00 - 10:30  Tutorial: Onboarding (30 min)
10:30 - 11:30  Q1: The Vision (45-60 min, flexible)
11:30 - 12:30  Q2: The Prototype (45-60 min, flexible)
12:30 - 13:00  The Investor Gauntlet (30 min)

13:00 - 14:00  ═══ LUNCH BREAK ═══

14:00 - 15:00  Q3: Market Challenges (45-60 min, optional chaos)
15:00 - 16:00  Q4: Launch Sprint (45-60 min, optional chaos)
16:00 - 16:30  Performance Review (30 min)
```

**Timing Flexibility:**
- Quarters can be 45-60 min based on group pace
- Chaos events are OPTIONAL in Q3 and Q4 (gamerunner's discretion)
- Total time: 6-6.5 hours depending on quarter lengths

---

## QUARTER-BY-QUARTER NARRATION

### Quarter 1: The Vision (60 minutes)

**The Opening Scene**

Get everyone's attention. Then:

> "Alright, Directors. Welcome to Day 1 at SkywardAI.
>
> It's January. This company is literally a Figma mockup and a pitch deck. You six were hired yesterday - congrats on joining a pre-seed startup, hope you like ramen. The CEO just Slacked you all:
>
> **'Vision docs due in 60 minutes. Investors want to see strategy before they'll even consider a term sheet.'**
>
> She wants to know: What are you building? How will it work? Why won't this be the 47th failed airline startup?
>
> You've got options:
> - Strategic vision doc with architecture diagrams
> - Wireframes and user flows showing the product
> - Quick MVP to prove the concept isn't vaporware
>
> Fair warning: whatever you plan now, you'll have to build in Q2. Don't overpromise.
>
> Clock starts... now."

**During the Vision Phase (50 minutes)**

Walk among them like a DM checking on a party split across different rooms. Observe their strategies:

- Are they rushing to code? Remind them: *"The CEO asked for vision, not implementation. Use your planning agents - Business Analysts, UX Designers, Architects."*
- Are they unclear? Guide them: *"Picture your department six months from now. What services exist? What do customers experience?"*
- Call out time like a ticking clock: "30 minutes remain... 15 minutes... 5 minutes until the CEO arrives..."

**The Vision Presentations (5 minutes)**

> "Time! The CEO strides into the room, coffee in hand, eyes sharp. She points to each of you in turn. 30 seconds. Show me your vision."

Each director presents. React as the CEO:
- Impressed: *"Fascinating. I like where your head is."*
- Curious: *"Interesting choice. Can you deliver on that?"*
- Concerned: *"That's ambitious. Very ambitious."*

**Q1 Scoring (0-3 points):**

Score based on strategy quality, NOT code:

**3 Points - Exceptional Vision:**
- Clear, well-researched strategy
- Thoughtful architecture with concrete service breakdown
- Realistic roadmap for Q2-Q4
- Demonstrates understanding of multi-agent approach

**2 Points - Solid Planning:**
- Clear direction and basic architecture
- Feasible plan for Q2-Q4
- Shows planning effort

**1 Point - Basic/Vague:**
- Unclear strategy or overly ambitious
- Minimal planning or unrealistic expectations
- Rushed or incomplete vision

**0 Points - No Vision:**
- Nothing prepared or completely off-track

Close with:

> "Visions accepted. Now comes the hard part - building them. We have investors arriving in Q2. Don't let me down."

---

### Quarter 2: The Prototype (60 minutes)

**The Investor Summons**

> "It's April. Three months have passed since your visions were approved.
>
> This morning, the CEO burst through the door with news: Investors are coming. Not next month. Not next week.
>
> **Today. In 60 minutes.**
>
> They need to see working systems. Real code. Professional demos. Not sketches. Not promises. They want to invest $10 million in SkywardAI, but only if we prove we can build.
>
> This is your crucible, Directors. Build something that makes them believe.
>
> Focus on:
> - One or two services that actually work
> - Polish that impresses
> - A demo that tells a story
> - Something they'll remember
>
> Clock's ticking. Make it count."

**During the Build (50 minutes)**

The energy should feel urgent. Walk around with visible tension:

- "How's it going, Director? Will you be ready?"
- "The investors just confirmed - they're on their way."
- When you see good progress: *"Excellent. That's going to impress them."*
- When you see struggle: *"Need help? Don't be afraid to ask your peers."*

Call time at intervals: "40 minutes... 25 minutes... 10 MINUTES LEFT..."

**Progress Check (5 minutes)**

> "Investors are in the lobby. Quick - everyone show me where you're at. 30 seconds each. What am I about to see?"

Quick check-ins. Reassure or raise stakes as needed.

---

### The Investor Gauntlet (30 minutes)

**THIS IS YOUR ACT I CLIMAX. Make it dramatic.**

**The Setup (2 minutes)**

Dim the lights slightly. Change your demeanor. You are now the Lead Investor.

> "Good afternoon, Directors. I'm Alexandra Chen, Managing Partner at Altitude Ventures. My colleagues and I have 30 minutes. We're deciding whether to invest $10 million in SkywardAI.
>
> Each of you will present your department's progress. You have 3 minutes. Impress us, and we fund your future. Fail us, and... well, let's not think about that.
>
> We're evaluating four things: Does it work? Does it matter? Can you present it? Did you innovate?
>
> Director of Flight Search & Booking... you're first."

**The Presentations (18 minutes: 3 min × 6)**

Be a tough but fair investor:
- Interrupt with probing questions: *"How does that handle edge cases?"*
- React visibly to good demos: *"Impressive."*
- Raise eyebrows at bugs: *"And if I tried to book a flight without a date?"*
- Take notes dramatically

**The Deliberation (5 minutes)**

> "Excuse us for a moment."

Step aside. Calculate scores using the rubric. Return with gravitas.

**The Verdict (5 minutes)**

> "Directors... we've made our decision.
>
> [Announce scores one by one]
>
> Director of [Department], your work was [feedback]. Score: [X/10].
>
> [Continue for all six]
>
> We're investing. $10 million, wired today. But understand this: Year 2 expectations are higher. Much higher. Don't waste our money.
>
> Now go get lunch. You've earned it."

**→ THE FEAST (Lunch Break)**

---

### Quarter 3: Market Challenges (45-60 minutes)

**The Standard Opening**

> "Welcome back from lunch, Directors. Q3 - we're halfway through the year.
>
> It's July. SkywardAI has been live for 3 months. You've got traction, you've got customers, you've got momentum. Time to keep building on what you started in Q1-Q2.
>
> This quarter: continue executing on your roadmap. Polish existing features, add new capabilities, prepare for the final Q4 launch push.
>
> You've got 45-60 minutes. Make them count."

**OPTIONAL: The Chaos Event**

**Gamerunner Decision:** Do you want to introduce chaos this quarter?
- ✅ **Yes:** Group is doing well, can handle pressure
- ❌ **Skip:** Group is struggling or needs focus time

**If using chaos, introduce it 10-15 minutes into the quarter:**

> "Actually, Directors... something just came up. Welcome to startup reality."

**See [UNIVERSAL_CHAOS_SCENARIOS.md](UNIVERSAL_CHAOS_SCENARIOS.md) for six comprehensive scenarios.** Roll a d6 or pick one that fits your group's learning goals.

**The Scramble (if chaos introduced)**

Let them work. Add urgency every 8-10 minutes:
- "30 minutes left and Twitter is still angry..."
- "20 minutes... the CEO is asking for an update..."
- "10 MINUTES... this is it..."

**Quick Check-in (last 5 minutes)**

Quick status updates from each director. If chaos was introduced, judge how they handled it (contributes to delivery score). If no chaos, just check progress on their roadmap.

---

### Quarter 4: Launch Sprint (45-60 minutes)

**The Launch Announcement**

> "October. Launch day.
>
> The CEO bursts into the all-hands Zoom looking like she's had four espressos and zero sleep:
>
> 'Okay people, this is it. We're launching in the next hour. Real users. Real money. Real Hacker News comments tearing apart our product.
>
> Final polish time. Fix anything that would embarrass us on launch day. Make error messages that don't say "Error: undefined at line 47". Add loading states so people don't think it's broken. Handle edge cases. Make it look like adults built this.
>
> We either become a real company today or a "What Happened to..." blog post. Ship it.'
>
> This is launch day, Directors. Time to find out if you built something people actually want."

**During Launch Prep (First 25-35 minutes)**

The energy should shift from building to refining:
- "Test your error handling!"
- "What happens if someone enters garbage data?"
- "Does it look professional?"
- "Have you practiced your launch demo?"

**OPTIONAL: Last-Minute Crisis**

**Gamerunner Decision:** Want to add one final challenge?
- ✅ **Yes:** Simulate launch day stress, group handled Q3 chaos well
- ❌ **Skip:** Group needs focus time, running behind schedule

**If using chaos, introduce ~20-30 minutes into quarter:**

> "Uh, Directors... we have a situation. Handle this AND still launch on time."

**See [UNIVERSAL_CHAOS_SCENARIOS.md](UNIVERSAL_CHAOS_SCENARIOS.md)** - same six scenarios as Q3.

**Final Push (Last 10-15 minutes)**

Call time urgently: "20 minutes to launch... 10 MINUTES... 5 MINUTES..."

**The Launch Demo (last 5-10 minutes)**

Make this ceremonial. Quick demos from each director showing their final product.

**After all demos:**

> "Okay. It's 11:59pm.
>
> The CEO takes a deep breath, hovers over the 'Deploy to Production' button, and... clicks it.
>
> SkywardAI is LIVE.
>
> *[pause for effect]*
>
> 🎉 First booking just came through. Someone in Portland just bought a ticket to Seattle.
> 💰 Revenue: $347.
>
> You did it. You built a real company in one year. From Figma mockups to actual customers giving you actual money. From six random engineers to a team that can ship under pressure.
>
> Board meeting in 30 minutes. Time to see who becomes VP."

---

## SCORING THE JOURNEY

### Tracking Each Director's Path

You're not just counting points - you're measuring a hero's journey across 1 year.

### Delivery Score: The Chronicle of Shipping

After each demo (Q1-Q4), award 0-3 points based on what you witness:

**3 Points: Legendary**
- The demo flows perfectly
- Features that make you think "damn, that's clever"
- Edge cases handled
- Clearly polished with care

**2 Points: Solid**
- Core functionality works
- Happy path succeeds
- Some rough edges, but acceptable
- Meets the quarter's challenge

**1 Point: Struggling**
- Partially working
- Significant bugs or missing pieces
- Minimal progress since last quarter
- Didn't meet the scenario requirements

**0 Points: Broken**
- Nothing works
- No visible progress
- (Very rare - support them before it gets here)

**Total Delivery Score = Sum across all 4 quarters (max 12)**

### Investor Demo Rubric (Q2 Special Evaluation)

This is your Act I climax. Score each director on 4 dimensions:

**Technical Quality (3 points)**
- 3: Works perfectly, robust, handles edge cases
- 2: Works for happy path, minor bugs okay
- 1: Partially working, significant issues
- 0: Broken or non-functional

**Business Value (3 points)**
- 3: Addresses real customer pain, impressive features, clear value
- 2: Basic functionality, useful, meets requirements
- 1: Minimal features, unclear value
- 0: No clear business value

**Presentation (2 points)**
- 2: Tells a compelling story, confident, smooth demo
- 1: Functional but dry, unclear explanation
- 0: Confusing, disorganized, broken demo

**Innovation (2 points)**
- 2: Creative solution, surprising feature, technical sophistication
- 1: Solid but predictable
- 0: Generic, no originality

**Total: /10 points**

**As the Investor, give dramatic feedback:**

**8-10 points:**
> "Exceptional, Director [Name]. We're particularly impressed with [specific thing]. Consider this department a priority investment area."

**5-7 points:**
> "Good work, Director [Name]. We see potential in [aspect], but we expected stronger [missing element]. Year 2 needs to be better."

**3-4 points:**
> "We have serious concerns about [Department]. The [issue] is a red flag. Can you turn this around, or do we need to make changes?"

**0-2 points:**
> "Director [Name]... this is unacceptable. [Specific problem] must be resolved immediately or we'll need to have a very different conversation."

### Tech Debt: The Weight of Shortcuts

At game's end, evaluate each codebase for technical debt.

**Use a Code Review Agent:**
```
"Review this codebase for technical debt. Score 0-10 where:
- 8-10: Production-ready (tests, clean code, documentation, error handling)
- 4-7: Moderate debt (some tests, basic structure, some shortcuts)
- 0-3: High debt (no tests, hardcoded values, no error handling, messy)

Provide: Overall score and specific issues."
```

**Or quick manual checklist:**
- No tests? +3 debt
- Hardcoded secrets? +2 debt
- No error handling? +2 debt
- Duplicated code? +2 debt
- No documentation? +1 debt
- Poor structure? +1 debt
- Security issues? +3 debt

**Tech Debt Score = 15 - actual_debt_points** (so low debt = high score)

### API Cost: The Resource Management

Track Claude API usage per director:

**Typical spending:**
- Efficient: $10-20 (strategic agent use)
- Average: $25-40 (solid work)
- Expensive: $50+ (agent overuse)

**Cost Score:**
- ≤ $20: **10 points** (Masterful efficiency)
- $21-40: **7 points** (Good resource management)
- $41-60: **4 points** (Overspending)
- > $60: **1 point** (Wasteful)

### Collaboration: The Fellowship

Award points for working together:

**+5 points:** Helped 2+ directors significantly (>10 min each helping debug, sharing patterns)
**+3 points:** Helped 1 director substantially or shared valuable insights
**+1 point:** Good team player, responsive to questions
**0 points:** Worked alone (not penalized, just not rewarded)
**-2 points:** Actively harmful (refused help, blamed others, toxic)

### The Final Calculation

```
FINAL SCORE =
  Delivery (max 12)
  + Tech Debt (max 15)
  + API Cost (max 10)
  + Collaboration (max 5)

Maximum possible: 42 points
```

---

## THE DICE OF FATE

### Crisis Events (Optional for Q3 and/or Q4)

**All chaos scenarios are in [UNIVERSAL_CHAOS_SCENARIOS.md](UNIVERSAL_CHAOS_SCENARIOS.md).**

**When to use:** Group is performing well and can handle pressure. **When to skip:** Group is struggling or behind schedule.

**Six scenarios (roll d6 or choose):**
1. Competitor Launched Superior App (30-45 min)
2. Enterprise Customer Deal (45-60 min)
3. Regulatory Audit (45-60 min)
4. Security Breach Discovered (60 min)
5. Acquisition Due Diligence (60-90 min)
6. Market Crash - Travel Downturn (60 min)

Each gives all directors specific challenges. See the full document for narrative setup, department tasks, and gamerunner tips.

---

## THE FINAL RECKONING

### The Performance Review (30 minutes)

**This is your epilogue. Make it count.**

**Phase 1: The Calculation (10 min)**

Display scores on the board transparently. Show the formula. Let them see everything.

**Phase 2: Individual Judgment (15 min)**

Go through each director (~2 min each). Template:

> "[Director Name], Director of [Department]...
>
> **Delivery:** [X/12] - Your finest hour: Q[Y] when you [achievement].
> **Tech Debt:** [X/15] - [Code quality observation]
> **Efficiency:** [X/10] - [Cost observation]
> **Collaboration:** [+X] - [Teamwork observation]
>
> **Total: [XX/42 points]**
>
> Strengths: [2 specific things]. Areas to improve: [1-2 areas]. Thank you."

**Phase 3: The Ascension (5 min)**

Build suspense - announce top 3, then the VP winner:

> "The board has deliberated. Everyone gets promoted to Senior Director. But there can be only one VP of Engineering.
>
> In third: [Name] with [X] points. Well done.
> [Pause]
> In second: [Name] with [Y] points. Outstanding.
> [Long pause]
>
> Your new VP of Engineering... with [Z] points... Director [Winner] of [Department]!
>
> Congratulations, VP [Name]. You demonstrated [key strength].
> To everyone: you built a company from nothing. Well done."

**Phase 4: The Reflection (Optional 5-10 min)**

Bring them out of the story gently:

- What multi-agent technique surprised you most?
- What would you do differently if you ran this campaign again?
- Will you use these patterns in your real work?
- What was your favorite moment?

---

## TROUBLESHOOTING YOUR CAMPAIGN

### When Directors Struggle

**Not using multiple agents:**
Solution: "Directors, I'm requiring at least 2 agents in parallel this quarter. Show me coordination."

**Demos consistently fail:**
Solution: Pause at 20-minute mark. "Progress check - show me what you've got." Help debug. Reduce scope aggressively if needed.

**One director far behind:**
Solution: Pair them with a faster director as "mentor." Give simpler scope. Provide extra support during build time.

**Integration chaos (Q3):**
Solution: Make it optional. "Real integration is worth bonus points. Mocked integration is acceptable."

**Dice rolls feel unfair:**
Solution: "Directors, the real world is random. This tests your adaptability." Offer one re-roll token per game. Or skip chaos events entirely if group prefers.

**Running out of time:**
Solution: Run quarters at 45 min instead of 60 min. Skip chaos events in Q3/Q4. Never cut Q1-Q2 or Investor Demo.

**Group cruising too easily:**
Solution: Run quarters at 60 min, introduce chaos in both Q3 and Q4, ask tougher questions during demos.

**Claude access fails:**
Solution: Pair programming with working director. Use backup account. Last resort: pivot to planning instead of building.

**Toxic competition:**
Solution: "Remember - all of you get promoted. Only the top score becomes VP. You're competing for a promotion, not your job."

### Energy Management

**Keep energy high:**
- Play music during build time (instrumental, energizing)
- Celebrate milestones loudly (launch, successful demos)
- Use dramatic voices for NPCs (CEO, investors, customers)
- Physical movement between quarters

**Manage stress:**
- Humor when things break: "Welcome to engineering!"
- Normalize failure: "Bugs are realistic!"
- Provide snacks and caffeine
- Actually enforce the lunch break

### Narrative Techniques

**Make it feel like a real startup:**
- Use actual startup communication: Slack messages, Zoom calls, investor emails
- Create urgency through realistic scenarios: "TechCrunch just asked for comment on the outage..."
- Personalize with details: "Customer @angry_flyer just tweeted at you with 4,000 RTs..."
- Show consequences: "Your NPS score dropped 20 points..."

**Startup Story Arc:**
- Q1-Q2: Naive optimism ("We're going to disrupt everything!")
- Investor Demo: High-stakes pressure (funding or death)
- Q3: Crisis mode (welcome to reality)
- Q4: Scrappy survival (ship or die)
- Review: Who gets promoted (tech startup meritocracy... sort of)

---

## MATERIALS & RESOURCES

### Required Materials

**Physical:**
- [ ] Character sheets (printed, one per role)
- [ ] Scoring sheets (tracking spreadsheet or paper)
- [ ] One beautiful d6 die (make it special - this is the Die of Fate)
- [ ] Visible timer/clock
- [ ] Whiteboard or screen for timeline and scores
- [ ] Name tents: "Director of [Department]"

**Digital:**
- [ ] README.md (shared beforehand)
- [ ] Character sheets (characters/ directory)
- [ ] TUTORIAL.md (reference material)
- [ ] **UNIVERSAL_CHAOS_SCENARIOS.md** (chaos event options - read before workshop!)
- [ ] Scoring spreadsheet

**Optional but Recommended:**
- [ ] Music playlist for build time
- [ ] Printed crisis cards (instead of rolling)
- [ ] Victory certificates or awards
- [ ] Snacks and beverages

### Scoring Spreadsheet

```
Director      | Q1 | Q2 | Q3 | Q4 | Delivery | Tech Debt | Cost | Collab | TOTAL
--------------|----|----|----|----|----------|-----------|------|--------|-------
Alice (Search)| 2  | 3  | 2  | 3  |    10    |    12     |  7   |   +5   |  34
Bob (Booking) | 2  | 2  | 3  | 2  |     9    |    14     |  10  |   +3   |  36
Carol (Recs)  | 3  | 2  | 2  | 3  |    10    |    11     |  7   |   +1   |  29
...
```

---

## TIMING GUIDE

### Flexible Quarter Lengths (45-60 min)

**Run 60 min:** Complex features, good pace, time buffer, chaos planned
**Run 45 min:** Ahead of schedule, simple work, running behind

**Typical Distributions:**
- Relaxed: All 60 min → 4:30pm finish
- Standard: Q1-Q2 = 60 min, Q3-Q4 = 45 min → 4pm finish
- Tight: All 45-50 min → 3:45pm finish

### Chaos Event Strategy

**Double Chaos:** Q3 + Q4. Strong groups only.
**Single Chaos (Recommended):** Q3 only. Balanced challenge.
**No Chaos:** Skip all. Learning-focused groups.

**Selection guide:** Competitive group → Scenario 1, Business-minded → Scenario 2, Junior → Scenario 3 or 4, Experienced → Scenario 5, Maximum drama → Scenario 4, Strategic → Scenario 6, Random → d6 roll

See [UNIVERSAL_CHAOS_SCENARIOS.md](UNIVERSAL_CHAOS_SCENARIOS.md) for full details.

### If Running Behind

**Cut from:**
- Individual feedback in review (group only)
- Tutorial (if they know Claude)
- Chaos events (skip them)
- Reduce quarters to 45 min each

**Never cut:**
- Q1-Q2 (foundation)
- Investor Demo (climax)
- Lunch (people need it)
- Q4 Launch (emotional high)

### If Running Ahead

**Add:**
- Extended retrospectives per quarter
- Longer investor Q&A
- Group code review session
- Advanced multi-agent workshop

---

## POST-GAME FOLLOW-UP

**Immediately after:**
- Send scores and detailed feedback
- Share code repositories
- Collect feedback survey
- Exchange contacts for continued learning

**One week later:**
- "Have you used multi-agent patterns at work yet?"
- Share aggregated learnings
- Offer office hours

**One month later:**
- Skill retention survey
- Share success stories
- Iterate on game design

---

## YOUR SUCCESS METRICS

**Did you succeed as Gamerunner?**
- [ ] All directors shipped working software by Q4 launch
- [ ] Everyone tried multi-agent patterns (not just single agent)
- [ ] Energy stayed high throughout the 4 quarters
- [ ] Competition felt healthy (not toxic)
- [ ] Pacing felt right (not too rushed, not too slow)
- [ ] Post-survey: 80%+ would recommend

**Track for improvement:**
- Which quarter lengths worked best? (45 vs 60 min)
- Where did directors get stuck?
- Did chaos events add value or just stress?
- How many chaos events felt right? (0, 1, or 2)
- Was scoring clear to participants?

---

**Go forth, Gamerunner. You're not just teaching a workshop - you're giving them a compressed startup experience they'll reference for years. Make it memorable, make it fun, and maybe throw in a few "synergy" and "disruption" buzzwords for authenticity.**

🎲✈️🚀

*"Move fast and orchestrate agents." - SkywardAI motto*

