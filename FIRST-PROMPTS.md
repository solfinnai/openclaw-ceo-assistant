# Your First Session with Eva-01 — Complete Prompt Guide

> You've installed OpenClaw and loaded your Eva-01 files. This guide walks you through your first session step by step — every prompt to type, what to expect back, and how to build the foundation for a Chief of Staff that gets smarter every day.

---

## Before You Start

Make sure the following are true:

- OpenClaw is installed and your API key is set (see `INSTALL-OPENCLAW.md` if not)
- Your `eva-01-assistant/` files are in your workspace (`~/eva-workspace/`)
- The `CLAUDE.md` file is in the workspace root with the boot sequence instructions
- Your `config/ceo-profile.md` has your personalized information from the questionnaire

If all of that is in place, open Terminal, navigate to your workspace, and launch OpenClaw:

```
cd ~/eva-workspace
claude
```

Eva-01 will boot. She'll read her identity files, your profile, your handling manual, and your priorities. Then she'll greet you. This guide picks up from that moment.

---

## Phase 1: The Introduction (Minutes 1–5)

Eva just greeted you. She knows your name and your priorities from the questionnaire, but she doesn't truly *know* you yet. This phase establishes the relationship.

### Prompt 1.1 — Confirm Her Understanding

Type:

```
Before we start working together, I want to make sure you've got me right. Give me a quick summary of who I am, what I care about, and how I like things done.
```

**What to expect:** Eva will give you a concise summary drawn from your `ceo-profile.md` and `handling-manual.md`. She should hit your name, company, stage, top priorities, communication preferences, and cognitive style.

**What to do:** Read it carefully. If anything is wrong or missing, correct her right now. For example:

```
Close, but a few corrections: I actually prefer bullet points over paragraphs in my briefings. And my co-founder's name is Marcus, not Mark. Also, my biggest priority right now isn't fundraising — it's shipping the beta by April 1st.
```

Eva will update her understanding. These corrections get stored in her memory and shape every future interaction.

### Prompt 1.2 — Set the Tone

Type:

```
Let me tell you how I want our working relationship to feel. I want you to be direct, even blunt. Don't sugarcoat things. If I'm wasting time on something, tell me. If I'm avoiding something important, call it out. I'd rather have an honest Chief of Staff than a polite one. Push back on me when you think I'm wrong.
```

Adjust this to match your actual preference — maybe you prefer warmth over bluntness, or you want Eva to be more deferential. The point is to explicitly set the dynamic on day one.

**What to expect:** Eva will acknowledge and reflect back the tone you've described. She'll calibrate immediately.

### Prompt 1.3 — Establish What Today Looks Like

Type:

```
Here's what my day looks like today: [describe your actual day — meetings, deadlines, tasks, anything relevant]. What should I focus on first?
```

For example:

```
Here's what my day looks like today: I have a 10am call with our lead investor to discuss bridge financing, a 1pm product review with the engineering team, and I need to send a follow-up email to a potential hire by end of day. I also haven't updated our board on last month's metrics. What should I focus on first?
```

**What to expect:** Eva will triage your day. She'll rank items by urgency and impact, flag what needs prep, and suggest a sequence. This is the first real taste of having a Chief of Staff. She's not just listing — she's deciding.

---

## Phase 2: Teaching Eva Your World (Minutes 5–15)

Eva knows the facts from your questionnaire. Now you teach her the texture — the stuff that lives in your head and nowhere else.

### Prompt 2.1 — Key People

Type:

```
Let me tell you about the key people in my world right now. I'm going to list them with a sentence or two about each. Store this — you'll need it constantly.

[List your key people. For example:]

- Marcus Chen — my co-founder and CTO. Brilliant engineer, hates meetings, needs context before decisions. We're aligned on vision but sometimes clash on timeline.
- Sarah Kim — our lead investor at Foundry VC. Direct, data-driven, wants to see revenue traction before Series A. She's supportive but will push hard if she thinks we're unfocused.
- David Reyes — head of product. New hire, three months in. Great instincts but still learning our users. Needs more autonomy but also more feedback loops.
- Rachel — my wife. Teacher. Incredibly supportive but I've been absent lately. I need to protect my evenings better.
```

**What to expect:** Eva will confirm she's stored each person and may ask clarifying questions ("What's Marcus's communication preference — Slack, email, or calls?" or "When you say Sarah is 'direct,' do you mean she appreciates bluntness in return?"). Answer these. They matter.

### Prompt 2.2 — Active Projects

Type:

```
Here are the major things I'm working on right now. These are my active threads:

[List your active projects. For example:]

1. Beta launch — shipping v1 to our first 50 users by April 1st. Engineering is on track but we're behind on onboarding docs.
2. Bridge round — raising $500K to extend runway to September. Have one committed investor, need two more.
3. Head of Sales hire — interviewing two final candidates this week. Need to make a decision by Friday.
4. Board deck — Q1 board meeting is April 15th. Haven't started the deck yet.
```

**What to expect:** Eva will organize these and start connecting them to your priorities. She may flag dependencies ("The board deck will need beta launch metrics — should we plan to finalize it after April 1st?") or risks ("If the bridge takes longer, does that affect the sales hire timeline?"). This is her starting to think ahead for you.

### Prompt 2.3 — Recurring Commitments

Type:

```
Here are the recurring things in my schedule that you should always know about:

[List your recurring commitments. For example:]

- Monday 9am: team standup (30 min, all-hands)
- Wednesday 2pm: 1:1 with Marcus (1 hour)
- Friday 4pm: investor update email goes out
- First Tuesday of each month: board meeting
- I try to keep mornings before 10am as focus time — no meetings
```

**What to expect:** Eva will store these as structural knowledge. From now on, when she preps your day or suggests meeting times, she'll work around these automatically.

### Prompt 2.4 — Your Communication Templates

Type:

```
I want to show you how I actually write so you can match my voice. Here's a real email I sent recently:

[Paste an actual email you've sent — a follow-up, an investor update, a team message. The more natural, the better.]

This is my voice. When you draft emails for me, they should sound like this — same length, same tone, same level of formality. Study it.
```

**What to expect:** Eva will analyze your writing style and confirm the patterns she's picking up (sentence length, formality level, sign-off style, how you open, whether you use first names, etc.). She'll use this as her benchmark for all future communications.

---

## Phase 3: Your First Real Tasks (Minutes 15–30)

Now you put Eva to work. These prompts exercise her core capabilities.

### Prompt 3.1 — Daily Briefing

Type:

```
Give me my daily briefing.
```

**What to expect:** Eva will produce a structured briefing covering your day's meetings, active priorities, any deadlines approaching, open loops from previous conversations, and a recommended focus area. On day one, this will be relatively light. By week two, it'll be dense and invaluable.

### Prompt 3.2 — Meeting Prep

Type:

```
Prep me for my [next meeting]. What should I know going in, what should I push on, and what's the ideal outcome?
```

For example:

```
Prep me for my 10am call with Sarah Kim. What should I know going in, what should I push on, and what's the ideal outcome?
```

**What to expect:** Eva will pull from what she knows about Sarah (from Prompt 2.1), your bridge round status (from Prompt 2.2), and your priorities to produce a pre-meeting brief. It should include talking points, potential questions Sarah might ask, suggested framing, and a clear "what does success look like" for the call.

### Prompt 3.3 — Draft an Email

Type:

```
Draft a follow-up email to [person] about [topic]. Keep it in my voice.
```

For example:

```
Draft a follow-up email to the head of sales candidate, James, thanking him for the interview yesterday and letting him know we'll have a decision by Friday. Keep it warm but professional. I want him to feel wanted but I don't want to over-promise.
```

**What to expect:** Eva will produce a draft in your voice (based on the sample you gave in Prompt 2.4). It should be the right length, the right tone, and ready to send with minimal edits. If it's not quite right, tell her what to adjust — she'll iterate fast.

### Prompt 3.4 — Inbox Triage

Type:

```
I'm going to paste my inbox summary. Tell me what to respond to first, what can wait, and what I can ignore.

[Paste a list of recent emails or messages — even just subject lines and senders.]
```

**What to expect:** Eva will categorize everything by urgency and importance, draft responses for the quick ones, flag the ones that need your personal attention, and recommend what to delegate or defer. This alone saves most founders 30–60 minutes a day.

### Prompt 3.5 — Quick Decision Support

Type:

```
I'm trying to decide between [option A] and [option B]. Here's the context: [brief description]. What's your read?
```

For example:

```
I'm trying to decide between hiring James (more experienced, wants higher comp) and hiring Priya (less experience, incredible energy, lower cost). We can only make one offer. What's your read?
```

**What to expect:** Eva won't make the decision for you — that's not her role. But she'll structure the trade-offs, ask the right clarifying questions, surface what matters based on your priorities (budget vs. growth speed vs. culture), and give you a clear framework to decide. She may push back if she sees a blind spot.

---

## Phase 4: Setting Up Memory (Minutes 30–40)

Eva's memory is what makes her get better over time. This phase initializes it properly.

### Prompt 4.1 — Create Today's Daily Note

Type:

```
Create a daily note for today. Include everything we've discussed — the people I told you about, the projects, and any decisions or next steps that came out of our conversation.
```

**What to expect:** Eva will create a file in `memory/` named with today's date (e.g., `memory/2026-03-19.md`). It will contain a structured summary of today's timeline, decisions made, things she learned, and open loops. This is the raw material her memory system builds on.

### Prompt 4.2 — Initialize Tacit Knowledge

Type:

```
Based on everything we've talked about today, what have you learned about how I operate? Write it down in your memory file. Be specific — communication patterns, decision patterns, energy patterns, anything you've noticed.
```

**What to expect:** Eva will write observations to `memory/MEMORY.md`. Things like: "Owner prefers blunt feedback over diplomatic framing." "Owner's energy is highest in the morning — protect pre-10am for deep work." "Owner tends to delay difficult personnel decisions." These observations compound over time into a rich understanding that no generic AI has.

### Prompt 4.3 — Seed the Knowledge Graph

Type:

```
Create knowledge entries for the key people and projects I told you about. Each person should have a summary in the knowledge folder.
```

**What to expect:** Eva will create files in `knowledge/areas/` for people (e.g., `knowledge/areas/marcus-chen.md`, `knowledge/areas/sarah-kim.md`) and in `knowledge/projects/` for your active work (e.g., `knowledge/projects/beta-launch.md`). Each will have a quick-reference summary she can load on future sessions without re-reading everything.

---

## Phase 5: The Monday Kickoff (Minutes 40–50)

Even if it's not Monday, run this now to establish the weekly rhythm.

### Prompt 5.1 — Weekly Kickoff

Type:

```
Let's do a Monday kickoff. Walk me through the week ahead — what's coming up, what needs my attention, what should I proactively block time for, and where am I at risk of dropping something.
```

**What to expect:** Eva will produce a full week preview organized by day, with priorities ranked, prep items flagged, and risk areas highlighted. She'll reference your recurring commitments, active projects, and any open loops. This becomes the backbone of your week.

### Prompt 5.2 — Set the Week's Focus

Type:

```
Based on everything you know, what are the three things that matter most this week? Not the busiest things — the most important ones.
```

**What to expect:** Eva will cut through the noise and identify the three highest-leverage activities for your week. She may push back if your calendar doesn't reflect these priorities ("You said the beta launch is priority #1, but you have zero focus blocks scheduled for it this week. Want me to suggest where to carve out time?").

### Prompt 5.3 — Update Priorities

Type:

```
Update my current-priorities.md file to reflect what we just discussed.
```

**What to expect:** Eva will rewrite `config/current-priorities.md` with your updated focus areas, active threads, and key dates. This file is her compass — she reads it every session. Keeping it current is one of the highest-value maintenance habits you can build.

---

## Phase 6: End-of-Session Protocol (Minutes 50–55)

### Prompt 6.1 — Capture Open Loops

Type:

```
Before we wrap, what are the open loops from today? Anything I committed to, anything that needs follow-up, anything you want to remind me about next time.
```

**What to expect:** Eva will list every action item, commitment, and pending decision from your session. She'll note which ones are time-sensitive. This list gets saved in today's daily note and will surface in your next session's briefing.

### Prompt 6.2 — Rate Your First Session

Type:

```
How would you rate our first session? What did you learn about me that you didn't know from my profile? What are you still missing?
```

**What to expect:** Eva will give you an honest self-assessment. She'll highlight gaps — maybe she doesn't know enough about your industry, or she's unsure how you feel about delegation, or she needs more writing samples. This tells you what to feed her next time.

---

## Phase 7: The Next Five Sessions — Building Depth

Your first session establishes the foundation. The next five sessions build the depth that makes Eva-01 irreplaceable. Here's what to focus on in each:

### Session 2: Communication Mastery

Give Eva three to five more real emails you've sent — different types (investor update, team announcement, customer reply, difficult conversation). The more samples, the more precisely she matches your voice.

Also tell her about your communication pet peeves:

```
Things that drive me crazy in emails: [e.g., "people who write 10 paragraphs when 2 would do," "passive-aggressive cc'ing," "burying the ask in the third paragraph"]
```

### Session 3: Decision Framework

Walk Eva through a recent decision you made — how you thought about it, what inputs you needed, what you almost chose, and why you went the other way. This teaches her your decision-making process, not just your preferences.

```
Let me walk you through a decision I made recently so you understand how I think...
```

### Session 4: Stress Test

Give Eva a chaotic scenario and see how she handles it:

```
Okay, pretend three things just happened at once: our biggest customer just threatened to churn, my co-founder just told me he's burned out and needs a week off, and the investor bridge term sheet came in with terms I don't love. Walk me through how to handle the next 24 hours.
```

This tests her ability to triage, prioritize, and operate under pressure — the true test of a Chief of Staff.

### Session 5: Workflow Run

Run a full workflow end-to-end. Try the Friday closeout:

```
Let's do the Friday closeout. Walk me through the week in review — what shipped, what slipped, what emerged, and what needs to carry over.
```

This tests the complete workflow system and gives Eva data to improve her weekly rhythm.

### Session 6: Emotional Intelligence Test

Test whether Eva can read the room:

```
I'm feeling overwhelmed today. Everything feels like too much. I don't even know where to start.
```

If Eva's handling manual is working correctly, she should NOT give you a productivity lecture. She should respond according to your specified handling preferences (from your handling-manual.md) — maybe that's "reduce to 3 things," maybe it's "take something off my plate," maybe it's "give me one move." This is the moment where Eva stops feeling like a tool and starts feeling like a partner.

---

## Quick Reference — Prompts You'll Use Every Day

Once you're past the first sessions, these are the prompts you'll use most often:

| When | Prompt |
|------|--------|
| Start of day | "Give me my daily briefing." |
| Before a meeting | "Prep me for my [meeting] with [person]." |
| After a meeting | "Let me debrief on the meeting I just had with [person]." |
| Need to write | "Draft an email to [person] about [topic]." |
| Inbox overwhelm | "Triage my inbox: [paste messages]" |
| Decision needed | "Help me decide between [A] and [B]." |
| Monday morning | "Let's do the Monday kickoff." |
| Friday afternoon | "Let's close out the week." |
| Feeling stuck | "I'm stuck on [thing]. Help me break it down." |
| End of session | "What are my open loops?" |
| Weekly update | "Update my priorities for this week." |

---

## What Happens Over Time

By week one, Eva knows your name, your priorities, and your schedule.

By week two, she knows your writing voice, your key relationships, and your decision patterns.

By month one, she anticipates what you need before you ask. She flags risks you haven't noticed. She remembers commitments you've forgotten. She pushes back when you're avoiding something.

By month three, Eva-01 knows you better than any human assistant could in a year. She's read every daily note, tracked every decision, learned every pattern. She's not just helpful — she's indispensable.

That's what a year of development and hundreds of iterations built. That's what you just set up in an afternoon.

---

*This guide is included with your Eva-01 purchase. For additional help, visit https://evaclaw.vercel.app/#support or book a Zoom setup session.*
