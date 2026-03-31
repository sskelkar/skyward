# Game Designer Feedback on Skyward
## March 2026 Review

**Reviewers:**
- D&D Gamerunner (10+ years experience)
- D&D Player (avid player perspective)
- Total War Gamer (strategy game expertise)
- Claude Expert (multi-agent orchestration specialist)

---

## Executive Summary

**Consensus:** Skyward is currently **70% workshop, 30% game** - and that's appropriate for its learning goals. However, it needs more game elements to boost engagement and memorability.

**Overall Verdict:**
- **D&D Gamerunner:** "Solid skeleton, missing meat. Needs drama, character depth, player choice."
- **D&D Player:** "Would play once as learning exercise, not repeatedly for fun."
- **Total War Gamer:** "6.5/10 as strategy game, 8.5/10 as gamified learning."
- **Claude Expert:** "Will effectively teach multi-agent orchestration. Biggest gaps: debugging and cost optimization."

**Recommended Balance:** Shift from 70/30 to **60/40 Workshop/Game** by adding just enough game elements without compromising learning.

---

## Critical Gaps (All Reviewers Agree)

### 1. **Lack of Player Agency** (BIGGEST ISSUE)
**Problem:** Directors are on rails - Q1 plan → Q2 build → Q3 maybe chaos → Q4 launch. No meaningful choices with consequences.

**Current "choices" don't matter:**
- "Build feature A or B?" (both are fine)
- "Integrate or use mocks?" (explicitly told integration is optional)

**Missing:** Strategic dilemmas with real tradeoffs and consequences.

---

### 2. **No Asymmetry Between Roles**
**Problem:** All 8 director roles play identically - just build 2-3 microservices with agents. Only difference is flavor text (booking vs pricing vs marketing).

**Compare to:**
- D&D: Wizard vs Rogue have completely different abilities and playstyles
- Total War: Different factions have unique units, mechanics, tech trees

**Current:** Booking Portal director plays exactly like Pricing director - same workflows, same patterns, same constraints.

---

### 3. **Weak Character Depth**
**Problem:** Directors are job descriptions with light flavor, not real characters with motivations, relationships, or flaws.

**Missing:**
- Personal stakes beyond work performance
- Relationships with other directors (rivalries, alliances, history)
- Individual quirks that create roleplay opportunities
- Backstory that drives decisions

---

### 4. **Weak Act II (Q3-Q4 Narrative Arc)**
**Problem:**
- Q3 chaos is *optional* (gamerunner might skip it)
- Q4 is just "polish your code" (no climax)
- No escalating antagonist (MegaAir mentioned but never becomes real threat)
- No do-or-die moment

**Strong:** Q1-Q2 with Investor Demo climax
**Weak:** Q3-Q4 lacks dramatic tension

---

### 5. **Too Much Solo Work, Not Enough Interaction**
**Problem:**
- Directors work in isolation for 45 minutes
- Integration is optional and discouraged
- No direct competition or resource sharing
- Feels like parallel productivity, not multiplayer game

---

## Recommendations by Priority

### HIGH PRIORITY (Fix These)

#### 1. **Make Q3 Chaos Mandatory**
- Don't say "optional" - gamerunner picks scenario based on group
- Chaos should feel inevitable and important
- Tie chaos to Q1-Q2 decisions (not random dice)

#### 2. **Add Asymmetric Mechanics to Roles**
Give each role unique abilities beyond flavor:
- **Booking Director:** Can integrate with 2 departments (bonus collaboration VP)
- **Pricing Director:** Gets 2x API budget but must hit cost efficiency targets
- **Support Director:** Can "rescue" one struggling director per quarter (+VP for helping)
- **Marketing Director:** Can demo twice per quarter (more delivery chances)
- **Inventory Director:** Gets extra time in Q1 for planning (complex domain)
- **Check-in Director:** Can skip Q1 research (simpler domain, jump to building)

#### 3. **Create Strategic Dilemmas with Real Consequences**

**Examples:**
- **Investor choice:** "$10M funding but investors want hiring veto. Accept?" (money vs autonomy)
- **Tech debt trade:** Ship fast/messy in Q2 → +2 demo points, +1 debt token → debt tokens can trigger bugs in Q4
- **Resource allocation:** "Board allocated 2 extra hours - vote which department gets it" (negotiation)
- **Feature priority:** "Build feature A (high impact, risky) or B (safe, incremental)?" (different scoring outcomes)

#### 4. **Make Q4 Start with Crisis, Not Polish**

**Current:** Q4 is "add polish, make it production-ready"
**Better:** Q4 starts "Launch went live 10 minutes ago. Customer complaints flooding in. You have 30 min to fix it."

Each director gets a specific crisis based on earlier choices:
- Shipped fast in Q2 → critical bug surfaces
- Skipped testing → integration breaks under load
- Over-engineered → performance issues

Forces recovery, not polish. Ends with triumph, not hope.

#### 5. **Position Honestly in Marketing**

**Current:** Positioned as "D&D for engineers" or "game"
**Better:** "Multi-agent coding workshop with game elements" or "Gamified skills workshop"

Set accurate expectations. The learning is substantial and real - own what it is.

---

### MEDIUM PRIORITY (Enhance These)

#### 6. **Add Character Depth**

For each director role, add:
- **Personal goal beyond work:** "Wants VP to prove parent wrong" / "Imposter syndrome despite brilliance" / "Competitive with Pricing director"
- **Relationship web:** "Worked with X before" / "Doesn't trust Y's judgment" / "Owes Z a favor"
- **Signature quirk:** "Always over-engineers" / "Ships fast but messy" / "Perfectionist who misses deadlines"

Make character sheets 80% personality/story, 20% strategy (currently flipped).

#### 7. **Add NPC Personality Sheets for Gamerunner**

Create character guides for:
- **CEO:** Personality, motivations, how they react to success/failure
- **Lead Investor:** Risk-averse? Visionary? Impatient?
- **MegaAir CEO:** Antagonist personality (taunts, competitive moves)

Helps gamerunner stay in character and improvise consistently.

#### 8. **Make Tech Debt Mechanically Meaningful**

**Current:** Just a score penalty at the end
**Better:**
- Q2: Ship fast = +2 demo points, +1 debt token
- Q3: For each debt token, 50% chance of critical bug event
- Q4: Each remaining debt token = -1 final score

Forces real tradeoffs. Creates emergent chaos. Rewards paying down debt.

#### 9. **Add Cost Optimization Teaching** (Claude Expert recommendation)

TUTORIAL.md should teach:
- When to use Haiku (cheap) vs Sonnet vs Opus (expensive)
- How to minimize token usage in prompts
- When to stop iterating and ship "good enough"
- Budget-conscious agent strategies

Currently scoring includes "API cost efficiency" but doesn't teach optimization.

#### 10. **Add Debugging Guidance** (Claude Expert recommendation)

TUTORIAL.md should cover:
- What to do when agents produce broken code
- Systematic debugging approaches
- When to fix vs when to start over
- Common integration failures and fixes

*Note: This is already being added by background agent.*

---

### LOW PRIORITY (Nice-to-Have)

#### 11. **Add Secret Objectives**
At start of game, each director draws a card with personal goal:
- "Ship without help from others" (+5 VP if achieved)
- "Integrate with 2+ departments" (+5 VP)
- "Score max tech quality" (+5 VP)
- "Spend under $15 API" (+5 VP)

Creates diverse strategies, prevents everyone doing the same thing.

#### 12. **Add Mid-Campaign Pivot**
After investor demo, reveal: "Investors want B2B focus now, not B2C"

Directors must adapt systems (B2C booking → B2B corporate travel management). Tests flexibility, prevents coasting through Q3-Q4.

#### 13. **Add Visible Leaderboards**
Track scores after each quarter so players know where they stand. Currently scoring is opaque until the end.

Helps players strategize mid-game.

#### 14. **Add Reflection Prompts**
Structured learning consolidation between quarters:
- "What multi-agent pattern worked best this quarter?"
- "What would you do differently next time?"
- "What surprised you about agent coordination?"

Drives learning retention.

#### 15. **Add Rival Director Mechanic**
Each director has a secret rival (assigned or chosen). Rival's success slightly hurts your score (not zero-sum, but competitive). Creates natural tension and roleplay.

#### 16. **Add Post-Quarter "In-Character" Reflection**
After each demo, ask: "What would your character be feeling right now?"

Reinforces roleplay, creates emotional investment.

---

## What DOES Work (Keep These)

### ✅ Learning Effectiveness (Claude Expert)

"This will actually teach multi-agent orchestration. The patterns are realistic, time pressure forces real prioritization, director mindset is the key insight."

**Participants WILL learn:**
- Parallel agent execution
- Specialist persona prompting
- Context management across agents
- Iterative refinement cycles
- Director mindset: delegate, don't code everything

**Cost:** ~$6-10 per participant = economically feasible

---

### ✅ Pacing and Structure (Total War Gamer)

"Quarterly escalation is excellent. Q1 (planning) → Q2 (high stakes) → Investor Demo (climax) → Q3 (chaos) → Q4 (finale) is near-perfect."

---

### ✅ Resource Tradeoffs (Total War Gamer)

"Time/API cost/tech debt create interesting tension. Three-resource system works."

---

### ✅ Immersive Moments (D&D Gamerunner)

"Investor demo as theater is brilliant. Changing demeanor, asking tough questions, visible countdown timers create real tension."

---

## Detailed Reviewer Feedback

### D&D Gamerunner: "Tutorial Disguised as Game"

**Strongest element:** Investor demo (stakes, theater, judgment)
**Weakest element:** Player agency (no meaningful choices)

**Key insights:**
- Character sheets are 80% strategy guide, 20% character - should be flipped
- PITCH.md sells learning, not experience - should sell drama
- Q3-Q4 narrative arc is weak (optional chaos, no escalating antagonist)
- Missing NPC depth and gamerunner improv tools
- Too much meta (showing score spreadsheets mid-game breaks immersion)

**Specific recommendations:**
- Add recurring antagonist (MegaAir CEO, lead investor getting cold feet)
- Make Q4 start with "launch failed, fix it" not "polish time"
- Add NPC personality cards (draw random investor persona each game)
- Create "if players do X, NPCs respond Y" reaction tables
- Add sensory descriptions to scripts ("CEO slams coffee mug down")

**Quote:** "This feels like a well-designed tutorial disguised as a game. It should be a compelling game that teaches as a side effect."

---

### D&D Player: "Work Simulator, Not Game"

**Would play?** "Maybe once as learning exercise. Wouldn't call friends for Skyward weekend like I would for D&D."

**Fun factor issues:**
- Quarterly demos create performance anxiety, not exciting tension
- Director roles are cosmetically different but mechanically identical
- Repetitive gameplay loop (build stuff 4 times in a row)
- Scoring is vague and invisible until the end
- Most time is solo work (45 min in terminal)

**What's missing from D&D:**
- Party dynamics and collaboration (integration is optional and discouraged)
- Varied gameplay (D&D has combat, exploration, social - Skyward is just "build stuff")
- Emotional investment beyond "did my code work"
- Unexpected moments and emergent storytelling
- Creative problem-solving together

**Suggestions:**
- Force collaboration (Pricing can't calculate without Inventory's data)
- Add player interaction (directors can invest in each other, negotiate resources)
- Create branching paths (vote on company direction after Q2)
- Add failure states and recovery (bombed demo → department gets acquired by another player)
- Shorten it (4 hours too long for repetitive structure)

**Quote:** "D&D is collaborative storytelling with meaningful choices. Skyward is parallel work simulation with cosmetic role-playing."

---

### Total War Gamer: "Missing Asymmetry and Strategic Depth"

**Strategic depth: 6/10** - Has genuine choices (parallel vs sequential, speed vs quality) but lacks rock-paper-scissors dynamics and counter-strategies

**Asymmetry: 4/10** - Critical flaw. All roles play identically (just different flavor text). Compare to Total War where Rome vs Shogunate play completely differently.

**Win conditions: 5/10** - VP promotion feels like HR metrics, not heroic victory. Opaque scoring (don't know standing until end).

**Resource management: 7/10** - Good foundation (time/cost/debt), but resources don't interact dynamically

**Chaos/randomness: 7/10** - Excellent d6 crisis table, but chaos is too optional

**Replayability: 5/10** - Once you master patterns, core loop doesn't change. No branching paths, alternate victories, or campaign variants.

**What Total War does that Skyward doesn't:**
- Asymmetric factions with unique mechanics
- Opponent interaction (denial, blocking, counter-strategies)
- Tech trees and progressive unlocks
- Diplomacy and negotiation
- Decisive battles where everything hangs in balance
- Fog of war and hidden information
- Emergent gameplay (every campaign feels different)

**Specific recommendations:**
- Add asymmetric role mechanics (unique abilities per director)
- Add direct competition (shared resources, blocking moves)
- Add strategic decision points between quarters (tech tree, partnerships, pivots)
- Make chaos mandatory with preparation/mitigation options
- Add dramatic final battle in Q4 (all directors compete head-to-head)
- Add alternate campaigns (hard mode, chaos mode, integration mode, legacy mode)

**Quote:** "It's gamified education, not a true strategy game. From pure strategy lens 6.5/10, from gamified learning lens 8.5/10."

---

### Claude Expert: "Effective Workshop, Gaps in Debugging and Cost"

**Will it teach multi-agent orchestration?** YES, with realistic expectations.

**Achievability:** Borderline optimistic
- Q1: Achievable (research/planning)
- Q2: Tight but possible (45-60 min to build 1-2 services)
- Q3-Q4: Depends on Q2 foundation

**Agent patterns:** Match real-world best practices
- ✅ Parallel execution, specialist personas, iterative refinement, context management
- ⚠️ Missing: error recovery, prompt iteration, cost optimization

**Scope:** Reasonable but ambitious (2-3 services per director is at upper edge)

**Technical guidance:** Well-balanced (enough structure to prevent paralysis, enough flexibility for experimentation)

**Transfer to real work:** High potential
- Concepts transfer even if tool-specific mechanics don't
- Workplace may use Claude.ai web, not CLI, but orchestration principles are identical

**Cost efficiency:** $6-10 per participant = economically feasible, but tutorial doesn't teach cost optimization strategies

**Common pitfalls:** Excellent coverage of orchestration pitfalls, missing tooling/technical troubleshooting

**Balance:** 70/30 workshop/game is appropriate

**Biggest gaps:**
1. **Debugging guidance** - What to do when agents produce broken code (being addressed)
2. **Cost optimization** - When to use Haiku vs Sonnet, how to minimize tokens
3. **Technical troubleshooting** - Port conflicts, environment issues, common failures
4. **Transfer guidance** - How to apply patterns in workplace tools

**Recommendations:**
- Add "When Agents Fail: Recovery Strategies" section
- Add "Cost-Effective Agent Strategies" teaching
- Add technical troubleshooting appendix
- Add "How to apply these patterns in your workplace" guidance
- Add more real code examples (show good and bad agent outputs)

**Quote:** "The role-play and time pressure create conditions for real learning (not just reading theory). ROI is excellent: ~$40-60 in API costs for skills that can 2-3x AI-assisted development speed."

---

## Key Design Tensions

### Tension 1: Game vs Workshop

**Can't maximize both.** Must choose where to lean.

**If lean toward GAME:**
- ✅ More fun, memorable, engaging
- ❌ Risk: becomes "fun activity" with minimal learning
- ❌ Risk: competition dominates over skill development

**If lean toward WORKSHOP:**
- ✅ More learning, better skill transfer, clear objectives
- ❌ Risk: feels like dry training, engagement drops
- ❌ Risk: no pressure to deliver, theory without practice

**Current:** 70/30 Workshop/Game
**Recommended:** 60/40 Workshop/Game (add HIGH priority game elements)

---

### Tension 2: Director Autonomy vs Collaboration

**Current design:**
- Directors work independently (minimizes cognitive load, maximizes focus on multi-agent learning)
- Integration is optional (each director can demo standalone)
- Goal: "Spend time with Claude, not coordinating with teammates"

**Player feedback:**
- "Too much solo work" (D&D Player)
- "No direct competition or interaction" (Total War Gamer)
- "Missing party dynamics" (D&D Player)

**Resolution options:**
1. **Keep current** - Accept that it's solo learning with light multiplayer elements
2. **Add forced touchpoints** - Require integration at specific points (Q2 investor demo, Q4 launch)
3. **Add negotiation mechanics** - Resource voting, department dependencies (without blocking solo demos)

---

### Tension 3: Realistic Scope vs Overwhelming Complexity

**Current:** 2-3 microservices per director over 4 quarters

**Feedback:**
- Claude Expert: "At upper edge of achievable"
- Total War Gamer: "Appropriate for learning microservices patterns"
- D&D Player: "By Q4 I'll be bored with repetitive structure"

**Resolution:** Keep 2-3 services, but add variety through:
- Asymmetric role mechanics (different challenges per role)
- Strategic events that force adaptation (not just "build more features")
- Quality gates (can't launch with tech debt > 3)

---

## Open Questions for Future Consideration

1. **How much "failure" is acceptable?**
   - Should directors be able to fail demos spectacularly?
   - Should there be consequences for failure beyond low scores?
   - D&D Player suggests: "Bombed demo → department acquired by another player"

2. **How to balance solo focus (for learning) with multiplayer engagement (for fun)?**
   - Current design minimizes interaction to maximize agent-learning time
   - But reviewers want more social dynamics

3. **Should we add alternate game modes?**
   - Hard mode: 30-min quarters
   - Integration mode: Forced cross-department dependencies
   - Chaos mode: Mandatory crisis every quarter
   - Legacy mode: Start with terrible existing codebase

4. **How to make roles feel mechanically different without overcomplicating?**
   - Simple asymmetry (unique abilities) vs complex asymmetry (different scoring, different constraints)

5. **Is 4 hours the right length?**
   - D&D Player: "Too long for repetitive structure"
   - Claude Expert: "Appropriate for skills workshop"
   - Total War Gamer: "Good pacing with current arc"

6. **Should chaos be mandatory or flexible?**
   - Gamerunner: "Always include, gamerunner picks scenario"
   - Current: "Optional at gamerunner discretion"
   - Consideration: Some groups may struggle and not need extra pressure

---

## Implementation Priorities

**If you could only fix 3 things:**

1. **Add asymmetric role mechanics** - Makes roles feel different to play
2. **Make Q4 start with crisis** - Creates climactic moment
3. **Add strategic dilemmas with consequences** - Gives player agency

**If you have time for 3 more:**

4. **Make Q3 chaos mandatory** - Ensures dramatic tension
5. **Add character depth (personal goals, relationships)** - Enhances roleplay
6. **Position honestly in marketing** - Sets accurate expectations

---

## Conclusion

**Skyward is a well-designed learning workshop that uses game mechanics effectively.** The multi-agent orchestration teaching is sound, the pacing is excellent, and the economic model works.

**To enhance engagement without sacrificing learning:** Add asymmetric roles, meaningful choices, character depth, and a crisis-driven climax. Shift from 70/30 to 60/40 workshop/game.

**The central insight stands:** Using role-play, time pressure, and multi-agent orchestration under realistic constraints teaches skills that transfer to real work.

**Own what it is:** A serious skills workshop with game elements that make learning stick - not a game that happens to teach something.

---

*Document created: March 31, 2026*
*Review participants: D&D Gamerunner, D&D Player, Total War Gamer, Claude Expert*
