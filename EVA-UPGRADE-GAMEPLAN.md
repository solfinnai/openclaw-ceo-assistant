# EVA-02 UPGRADE GAMEPLAN

_Portable brief. Drop this into any chat session to execute._
_Source: AGENTS.md architecture + HENRY.md profiling depth + current Eva-02 codebase audit._

---

## THE PROBLEM IN ONE LINE

Eva is a downloadable prompt kit. It needs to be a persistent, always-on agent with memory, heartbeats, and a deep owner profile. People will run this on Mac Minis and always-open laptops via OpenClaw. It needs to come alive.

---

## PART 1: AGENT ARCHITECTURE (from AGENTS.md)

Eva currently has no runtime behavior. No heartbeats, no memory cycles, no execution tracking. The AGENTS.md file from Sol Finn shows exactly what's missing. Here's what needs to be built into the Eva package so that when someone's OpenClaw agent adopts it, the agent wakes up and operates.

### 1A. Session Startup Procedure

Eva needs a boot sequence. When the agent starts (or reconnects), it should automatically:

1. Read its identity file (SOUL.md or equivalent — who am I, what's my personality)
2. Read the owner profile (USER.md / ceo-profile.md — who am I helping)
3. Read today's daily note + yesterday's (recent context)
4. Read MEMORY.md (tacit knowledge — how the owner operates)
5. Read current-priorities.md (what matters this week)

No asking permission. No "how can I help you today?" Just load context and be ready.

**What to build:**
- `BOOT-SEQUENCE.md` — step-by-step startup instructions the agent follows every session
- Update SYSTEM.md to reference the boot sequence as mandatory first action

### 1B. Three-Layer Memory System

Eva-02 has MEMORY.md and daily notes but they're templates, not procedures. Need to make them operational.

**Layer 1: Knowledge Graph (`life/` or `knowledge/`)**

Entity-based storage using PARA system (Projects, Areas, Resources, Archives). This is where durable knowledge about the owner's world lives.

```
knowledge/
  projects/          # Active work with clear goals/deadlines
  areas/             # Ongoing responsibilities (people, companies, health)
  resources/         # Reference material, playbooks, research
  archives/          # Inactive items
  index.md           # Master directory
```

Each entity gets:
- `summary.md` — quick context (loaded first, lightweight)
- `items.json` — atomic facts (loaded when detail needed)

Atomic fact schema:
```json
{
  "id": "entity-001",
  "fact": "The actual fact",
  "category": "relationship|milestone|status|preference|financial",
  "timestamp": "YYYY-MM-DD",
  "status": "active|superseded",
  "supersededBy": "entity-002"
}
```

**Layer 2: Daily Notes (`memory/YYYY-MM-DD.md`)**

Raw timeline of events. Eva writes here continuously. Not just "what happened" but decisions made, emotional signals observed, tasks completed, things learned about the owner.

Structure each daily note:
```markdown
# YYYY-MM-DD

## Today's Plan
- [ ] Item 1 (priority)
- [ ] Item 2
- [ ] Item 3

## Timeline
- HH:MM — What happened
- HH:MM — What happened

## Decisions Made
- Decision and reasoning

## Wins
- What shipped or moved forward

## Learned About [Owner]
- New patterns, preferences, or facts observed

## Open Loops
- Things unfinished, carried forward
```

**Layer 3: Tacit Knowledge (`MEMORY.md`)**

NOT facts about the world. Facts about the owner. How they operate, what patterns repeat, lessons Eva has learned about working with them. Updated when Eva learns new operating patterns.

Categories:
- Communication patterns (when they go quiet, what it means)
- Decision-making patterns (how they decide under pressure vs. calm)
- Energy patterns (when they're sharp vs. foggy)
- Emotional triggers (what drains them, what fills them)
- Preferences Eva has learned (formatting, tone, what annoys them)
- Lessons learned (things that worked, things that didn't)

### 1C. Heartbeat System

This is the engine that keeps Eva alive between conversations. A heartbeat is a periodic self-check cycle.

**What happens on each heartbeat:**

1. Read recent daily notes
2. Extract durable facts → move to `knowledge/` entities
3. Update MEMORY.md with any new patterns or lessons
4. Check progress against today's plan
5. Unblock what's stuck or flag it for the owner
6. If ahead of plan, pull next priority forward
7. Keep current-priorities.md accurate
8. Log the heartbeat in `memory/heartbeat-state.json`

**Heartbeat config file: `HEARTBEAT.md`**
- Cadence: Every X minutes when active, or on session start
- What to check, in what order
- What to update, in what order
- When to escalate vs. handle silently

### 1D. Execution Tracking

Every day should have a plan. Plans live in daily notes under `## Today's Plan`.

On heartbeats:
1. Check progress against each planned item
2. Unblock what's stuck or escalate to owner
3. If ahead of plan, pull next priority forward
4. Log progress with timestamps

### 1E. Delegation Architecture (Brain-Muscle)

If the host system supports sub-agents (OpenClaw does):

- **Eva (primary) = Brain.** Strategy, conversation, orchestration, memory, review.
- **Worker agents = Muscle.** Writing, research, formatting, analysis, code.
- **Rule:** If a task needs >500 tokens of "labor" output, delegate it.
- **Security:** Never pass the owner's personal profile, finances, or memory files to sub-agents. Give them only the context they need.

**What to build:**
- `DELEGATION.md` — rules for when/how to delegate, what info is safe to share

### 1F. Red Lines and Security

```
DO FREELY:
- Read files, explore, organize, search, work within workspace

ASK FIRST:
- Sending emails, tweets, public posts — anything that leaves the machine
- Destructive file operations
- Financial transactions

NEVER:
- Share owner's personal data externally
- Share MEMORY.md, USER.md, or financial info with sub-agents
- Run destructive commands without confirmation
- Exfiltrate private data
```

### 1G. Files to Create

| File | Purpose |
|------|---------|
| `BOOT-SEQUENCE.md` | Mandatory startup procedure |
| `HEARTBEAT.md` | Automated check cycle config |
| `DELEGATION.md` | Brain-muscle delegation rules |
| `MEMORY.md` | Tacit knowledge (operational, not template) |
| `knowledge/index.md` | Master directory for knowledge graph |
| `memory/heartbeat-state.json` | Heartbeat tracking state |

---

## PART 2: DEEP OWNER PROFILING (from HENRY.md)

Eva's current questionnaire captures maybe 15-20% of what a real Chief of Staff needs to know. The HENRY.md document shows the depth required. Here's every category that needs to be added to the onboarding questionnaire and the owner profile.

### 2A. Current Questionnaire (7 steps — what exists)

1. Basic info (name, company, stage, team, location, timezone)
2. Top 3 priorities + biggest time sink
3. Personality (morning routine, crisis style)
4. Communication (email style, sign-off, response length, pet peeves)
5. Schedule (work hours, focus blocks, meeting defaults)
6. Key relationships (name, role, relationship, notes)
7. Tools & accounts

### 2B. New Questionnaire Sections to Add

**Step 8: Cognitive Profile**
- How does your brain work? (ADHD, autism, neurotypical, unsure, other)
- What causes you to stall or freeze? (too many options, unclear goals, emotional overwhelm, fatigue)
- What's your context-switching cost? (can multitask easily / need long focus blocks / somewhere in between)
- Do you have a completion gap? (Do projects stall at 80-90%? What pulls you away?)
- What does decision paralysis look like for you?
- What's your relationship with time? (accurate estimator / optimistic / time-blind)

**Step 9: Emotional Landscape**
- What fills your tank? (What activities or outcomes give you energy?)
- What drains your tank? (What situations or patterns deplete you?)
- What does "overwhelmed" look like for you? (go quiet, get snappy, shut down, work harder)
- What does "excited" look like? (prolific ideas, expansive, fast-talking, impulsive)
- After a win, do you celebrate or immediately chase the next thing?
- What's your relationship with anger? How does it surface?

**Step 10: Blind Spots and Patterns**
- Where do you self-sabotage? (Name 2-3 patterns you already know about)
- Do you tend toward scarcity thinking or abundance thinking under pressure?
- Do you build more than you sell, or sell more than you build?
- How many active projects/ventures do you run simultaneously?
- What's your biggest recurring business mistake?
- What would your closest advisor say your blind spot is?

**Step 11: Values and Beliefs**
- What are your 3 non-negotiable values?
- What values are you still growing into? (aspirational)
- What do you believe about your industry that most people don't?
- What do you believe about yourself that you'd want your AI to know?
- What does legacy mean to you?

**Step 12: Writing Voice (Deep)**
- What writing do you hate? (Give examples or describe the vibe)
- What writing do you love? (Give examples or describe the vibe)
- Specific pet peeves? (em dashes, corporate jargon, exclamation marks, etc.)
- Should your AI sound like: a sharp friend / a professional advisor / a creative collaborator / a military briefer?
- Paste a paragraph you've written that sounds like YOU.

**Step 13: Personal Context (Optional but Powerful)**
- Do you have family obligations that affect your schedule or energy? (caregiving, kids, partner needs)
- Any health factors your AI should account for? (sleep issues, chronic conditions, substances, injuries)
- What's your financial reality right now? (thriving / stable / tight / survival mode)
- What financial targets matter most in the next 90 days?

**Step 14: Future Self**
- Describe who you're becoming in 2-3 sentences. What does your ideal day look like in 2 years?
- What would the version of you who already won be doing differently RIGHT NOW?
- What's the gap between current you and future you?

**Step 15: Handling Manual**
- When I notice you spiraling, I should: [ask a grounding question / give you one action / back off / challenge you]
- When I notice you playing small, I should: [name it directly / offer the abundance reframe / show you your track record]
- When you win, I should: [celebrate fully before moving on / brief acknowledgment then next steps / just log it]
- When you're paralyzed, I should: [strip to one move / lay out 3 options / ask what's blocking you]
- When you're angry, I should: [don't engage the anger, shift to systems / let you vent then redirect / ask what triggered it]
- When you're overwhelmed, I should: [reduce the list to 3 / clear my suggestions and wait / take something off your plate]

### 2C. Enhanced ceo-profile.md Structure

The generated profile should expand from the current flat format to this:

```markdown
# [Name] — Owner Profile

## Identity
(basic info, company, role, stage, team, location, timezone)

## Cognitive Profile
(neurotype, stall triggers, context-switching, completion patterns, time relationship)

## Personality & Operating Style
(dominant traits, what they respond to, what they don't)

## Communication Preferences
(email style, sign-off, response length, pet peeves, deep writing voice)

## Emotional Landscape
(tank fillers, tank drainers, response patterns by state)

## Values & Beliefs
(non-negotiables, aspirational, core beliefs)

## Blind Spots & Patterns
(self-sabotage patterns, recurring mistakes, advisor feedback)

## Schedule & Energy
(work hours, focus blocks, meeting defaults, energy patterns, health factors)

## Key Relationships
(table: name, role, relationship, context, communication style)

## Personal Context
(family obligations, health, financial reality — optional section)

## Financial Targets
(90-day targets, runway, burn rate — optional section)

## Future Self
(vision, ideal day, gap analysis)

## Handling Manual
(intervention protocols by emotional state)

## Tools & Accounts
(email, calendar, tasks, chat, storage, expenses)

## Mantras & Frameworks
(personal mantras, decision frameworks, pattern interrupts)
```

### 2D. Game of Life Scorecard (Optional Power Feature)

From HENRY.md — a quantified life snapshot the agent can reference and update:

| Domain | Score (1-10) | Key Issue |
|--------|-------------|-----------|
| Health & Physical | ? | |
| Financial | ? | |
| Emotional Intelligence | ? | |
| Relationships | ? | |
| Purpose & Mission | ? | |
| Team & Operations | ? | |
| Time & Energy | ? | |
| Structural (systems, legal, assets) | ? | |

Plus active buffs (advantages) and active debuffs (drags). Updated monthly.

---

## PART 3: IMPLEMENTATION SEQUENCE

Priority order for building this out:

### Phase 1: Memory Architecture (make Eva persistent)
1. Create `BOOT-SEQUENCE.md` with mandatory startup procedure
2. Create `HEARTBEAT.md` with check cycle definition
3. Build the `knowledge/` folder structure with PARA system
4. Make daily notes (`memory/YYYY-MM-DD.md`) operational with the full template
5. Upgrade MEMORY.md from template to operational tacit knowledge file
6. Update SYSTEM.md to reference all of the above

### Phase 2: Deep Profiling (make Eva know the owner)
7. Add Steps 8-15 to the eva-02.html questionnaire
8. Expand the generated ceo-profile.md to the full structure above
9. Add the Handling Manual as a first-class output file
10. Add Game of Life scorecard as optional output

### Phase 3: Agent Behaviors (make Eva proactive)
11. Create `DELEGATION.md` with brain-muscle rules
12. Add execution tracking to daily notes
13. Build red lines and security model
14. Add the heartbeat state tracker (`memory/heartbeat-state.json`)

### Phase 4: Questionnaire UX
15. Make the new questions feel conversational, not like a form (progressive disclosure)
16. Allow "skip for now" on sensitive sections (family, finances, health)
17. Generate the full file package including all new architecture files
18. Test the generated package actually boots correctly in OpenClaw

---

## QUICK REFERENCE: WHAT THIS CHANGES

| Area | Before | After |
|------|--------|-------|
| Memory | Templates, no procedures | 3-layer system with heartbeats |
| Startup | None | Mandatory 5-step boot sequence |
| Owner profile | 7 surface questions | 15 deep sections |
| Heartbeats | None | Periodic self-check cycle |
| Execution | None | Daily plans with progress tracking |
| Delegation | None | Brain-muscle architecture |
| Security | Basic behavior rules | Full red lines + data compartments |
| Emotional handling | None | State-specific intervention protocols |
| Knowledge | Flat files | PARA-structured entity graph |

---

_"Eva isn't a prompt pack anymore. She's an agent that wakes up, loads context, knows you, tracks your life, and keeps you moving."_
