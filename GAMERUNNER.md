# GAMERUNNER GUIDE
## Skyward: Running a Silicon Valley Startup Simulator

**Welcome, Gamerunner.** You're about to guide six engineers through the chaotic, hilarious, and occasionally terrifying world of building SkywardAI - a tech startup that's either going to disrupt the airline industry or become a cautionary tale on TechCrunch.

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

You are narrating the **1-year journey of SkywardAI** - a scrappy airline tech startup racing to disrupt an industry. Your six players aren't just engineers writing code - they are **department directors** fighting for success, promotion, and glory.

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
- [ ] GAME.md - the rules and structure
- [ ] Tech requirements - laptop, Claude access, dev environment
- [ ] TUTORIAL.md - multi-agent orchestration guide

**Your materials:**
- [ ] Print character sheets (one per director - make them look like offer letters)
- [ ] Scoring spreadsheet (track the leaderboard)
- [ ] A d6 die (bonus points if it's branded with your company logo)
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

### The Full Epic (6 Hours: 10am-4pm)

```
10:00 - 10:30  Tutorial: Learning the Magic
10:30 - 11:30  Q1: The Vision - Planning the Dream (60 min)
11:30 - 12:30  Q2: The Prototype - Building for Investors (60 min)
12:30 - 13:00  The Investor Gauntlet - Judgment Day

13:00 - 14:00  ═══ THE FEAST (Lunch Break) ═══

14:00 - 14:45  Q3: The Chaos Quarter - DICE DRIVEN CRISIS (45 min)
14:45 - 15:30  Q4: The Launch Sprint - Going Live (45 min)
15:30 - 16:00  The Reckoning - Scores Revealed, VP Crowned
```

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

**No scoring in Q1** - just set the tone. Close with:

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

### Quarter 3: The Chaos Quarter (45 minutes)

**The Random Disaster Generator**

Pull out your d6. Hold it up.

> "Hope you enjoyed lunch, Directors. Because we're about to simulate what every startup inevitably experiences: something going catastrophically wrong.
>
> It's July. SkywardAI has been live for 3 months. Customers are actually using your stuff. Revenue is happening. You're thinking maybe you'll make it.
>
> And then...
>
> *[dramatic pause]*
>
> ...the universe reminds you that startups are chaos engines. Let's see what breaks today."

**Roll the die in front of everyone. Read the result with appropriate startup panic energy.**

**Roll 1: CRITICAL BUG**

> "3 AM. Your phone explodes with alerts. A critical bug in the [roll randomly for department] system caused a cascading failure. Every. Single. Booking. From the past hour. Corrupted.
>
> Twitter is melting down. #SkywardAIFail is trending. The CEO is on a red-eye flight home and she's calling every 5 minutes demanding updates.
>
> 45 minutes. Fix it. Or we're finished."

**Roll 2: COMPETITOR ATTACK**

> "Breaking news alert on your phone. MegaAir - our biggest competitor - just launched [invent a feature]. TechCrunch's headline: 'SkywardAI Already Falling Behind.'
>
> The CEO's text: 'Find me in the office. NOW.'
>
> 45 minutes to respond. Ship something better, or explain to the board why we're losing."

**Roll 3: REGULATORY AUDIT**

> "Letter in the mail. Government seal. 'Department of Transportation - Data Privacy Audit Notice.'
>
> Translation: Government lawyers are arriving in 45 minutes to inspect our GDPR compliance and accessibility features. If we fail? $500,000 fine and front-page news.
>
> Move. NOW."

**Roll 4: INFLUENCER MELTDOWN**

> "Slack notification. Then another. Then fifty more.
>
> @TechReviewerGuru (5M followers) just posted: 'THREAD: My NIGHTMARE experience with @SkywardAI. This so-called "tech-forward" airline is a dumpster fire. 1/47'
>
> They're live-streaming. On Twitch. Showing every bug. Every error message. Every broken feature. Chat is already making memes.
>
> 45 minutes to ship fixes, apologize publicly, or pivot to damage control before this becomes a Harvard Business School case study on what NOT to do."

**Roll 5: ACQUI-HIRE RAID**

> "Your phone buzzes. It's your best backend engineer: 'Hey, can we talk? MegaAir just offered me 2x salary, equity, and a Director title. They're making offers to the whole team.'
>
> Then another engineer messages. Then another.
>
> MegaAir isn't trying to compete with you. They're trying to hire away your entire engineering org. If you lose 3+ engineers, the company is toast.
>
> 45 minutes. Build something so impressive that your team remembers why they joined a scrappy startup instead of Big Corporate. Or watch your company dissolve."

**Roll 6: PARTNERSHIP OPPORTUNITY**

> "Call from Expedia. They want to integrate with SkywardAI. If we can provide a working API that connects [roll for 2 random departments] within 45 minutes, we get a $2M partnership deal.
>
> Clock's ticking. This is your moonshot."

**The Scramble (38 minutes)**

Let them work. Add urgency every 8-10 minutes:
- "30 minutes left and Twitter is still angry..."
- "20 minutes... the CEO is asking for an update..."
- "10 MINUTES... this is it..."

**The Aftermath (5 minutes)**

Quick demos. Judge harshly but fairly. Apply scoring based on how they handled the crisis.

---

### Quarter 4: The Launch Sprint (45 minutes)

**The Launch Announcement**

> "October. Launch day.
>
> The CEO bursts into the all-hands Zoom looking like she's had four espressos and zero sleep:
>
> 'Okay people, this is it. In 45 minutes, we're flipping the switch. Real users. Real money. Real Hacker News comments tearing apart our product.
>
> You've got 45 minutes for final polish. Fix anything that would embarrass us on launch day. Make error messages that don't say "Error: undefined at line 47". Add loading states so people don't think it's broken. Handle edge cases. Make it look like adults built this.
>
> In 45 minutes, we either become a real company or a "What Happened to..." blog post. Ship it.'
>
> This is launch day, Directors. Time to find out if you built something people actually want."

**During Launch Prep (38 minutes)**

The energy should shift from building to refining:
- "Test your error handling!"
- "What happens if someone enters garbage data?"
- "Does it look professional?"
- "Have you practiced your launch demo?"

Call time at intervals: "30 minutes... 20 minutes... 10 MINUTES... 5 MINUTES..."

**The Launch Demo (5 minutes)**

Make this ceremonial. Quick demos from each director.

After all demos:

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

### The Crisis Table (Q3 Only)

At the start of Q3, roll 1d6 publicly. The die determines which crisis strikes the company during the Chaos Quarter.

**As Gamerunner, adapt these to what directors actually built.** If the Booking director built an amazing system, maybe their system fails in the crisis. Make it personal and dramatic.

### Optional: Chaos Modifiers

For extra drama, add random events:

**Good Fortune (advantage):**
- "Your intern just committed perfect code" → +5 min extra time
- "Competitor's site went down" → Crisis pressure reduced
- "CEO surprise visit" → Chance for bonus point

**Ill Fortune (disadvantage):**
- "Laptop crashed" → Lose first 5 minutes
- "Claude API slowdown" → Agents work 2x slower
- "Coffee machine broken" → Just for flavor/laughs

---

## THE FINAL RECKONING

### The Performance Review (30 minutes)

**This is your epilogue. Make it count.**

**Phase 1: The Calculation (10 min)**

Display scores on the board transparently. Show the formula. Let them see everything.

**Phase 2: Individual Judgment (15 min)**

Go through each director. Use this template, but speak it dramatically:

> "[Director Name], Director of [Department]...
>
> Your journey began 1 year ago with a vision. Let's see how that vision became reality.
>
> **Delivery:** [X/12 points]. You consistently [pattern]. Your finest hour was Q[Y] when you [achievement]. [Observation about struggles or triumphs]
>
> **Technical Debt:** [X/15 points]. [Code quality observation - did they take shortcuts or build it right?]
>
> **Resource Efficiency:** [X/10 points]. You spent [amount] on API costs, showing [efficiency observation].
>
> **Collaboration:** [bonus]. [Teamwork observation]
>
> **Total Score: [XX/42 points]**
>
> What you did well: [2-3 specific things]
> What to improve: [1-2 areas]
>
> Thank you for your service to SkywardAI."

**Phase 3: The Ascension (5 min)**

Build maximum suspense:

> "Directors... the board has deliberated on your futures.
>
> This was not an easy decision. All of you have shown excellence. All of you will be promoted to Senior Director effective immediately.
>
> But there can be only one VP of Engineering.
>
> [Pause]
>
> In third place, with [X] points: Director [Name]. Well done.
>
> [Pause]
>
> In second place, with [Y] points: Director [Name]. Outstanding work.
>
> [Long pause. Let tension build.]
>
> And your new VP of Engineering...
>
> With [Z] points...
>
> Director [Winner's Name] of [Department]!
>
> [Applause]
>
> Congratulations, VP [Name]. You demonstrated [key strength that set them apart].
>
> To everyone else: you are all Senior Directors of SkywardAI. You built a company from nothing. That's no small feat.
>
> Well done, all of you."

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
Solution: "Directors, the real world is random. This tests your adaptability." Offer one re-roll token per game.

**Running out of time:**
Solution: Reduce Q3-Q4 to 30-40 min each if desperate. Never cut Q1-Q2 or Investor Demo.

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
- [ ] GAME.md (shared beforehand)
- [ ] Character sheets (characters/ directory)
- [ ] TUTORIAL.md (reference material)
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

### If Running Behind

**Cut from:**
- Individual feedback in review (group only)
- Tutorial (if they know Claude)
- Q3-Q4 (reduce slightly if desperate)

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
- [ ] Post-survey: 80%+ would recommend

**Track for improvement:**
- Which quarters ran long?
- Where did directors get stuck?
- Which crises landed well vs fell flat?
- Was scoring clear to participants?

---

**Go forth, Gamerunner. You're not just teaching a workshop - you're giving them a compressed startup experience they'll reference for years. Make it memorable, make it fun, and maybe throw in a few "synergy" and "disruption" buzzwords for authenticity.**

🎲✈️🚀

*"Move fast and orchestrate agents." - SkywardAI motto*

