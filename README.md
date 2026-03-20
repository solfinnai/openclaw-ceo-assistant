# OpenClaw CEO Assistant

A simple, elegant prompt system that turns any LLM into a startup CEO's Chief of Staff.

## How It Works

This is a folder of Markdown files. No code. No APIs. Just prompts you feed to your AI assistant.

```
openclaw-ceo-assistant/
|
|-- SYSTEM.md                  # Master system prompt (load this first, always)
|
|-- config/
|   |-- ceo-profile.md         # Your personal profile (fill out once)
|   |-- current-priorities.md  # What matters right now (update weekly)
|
|-- prompts/
|   |-- calendar/
|   |   |-- daily-briefing.md      # Morning rundown of your day
|   |   |-- meeting-prep.md        # Pre-meeting briefing docs
|   |   |-- schedule-meeting.md    # Book meetings with the right context
|   |   |-- weekly-review.md       # Friday reflection + next week setup
|   |
|   |-- communications/
|   |   |-- email-draft.md         # Draft emails in your voice
|   |   |-- inbox-triage.md        # Sort messages by urgency
|   |   |-- follow-up-tracker.md   # Never drop the ball
|   |   |-- investor-update.md     # Monthly investor email template
|   |
|   |-- operations/
|       |-- travel-planning.md     # End-to-end trip planning
|       |-- expense-report.md      # Compile and categorize expenses
|       |-- document-prep.md       # Board decks, memos, one-pagers
|       |-- vendor-coordination.md # Manage external relationships
|
|-- workflows/
    |-- monday-kickoff.md          # Start the week right
    |-- friday-closeout.md         # Close the week clean
    |-- meeting-debrief.md         # Capture everything after key meetings
```

## Quick Start

1. **Fill out your profile.** Open `config/ceo-profile.md` and fill in every field. The more specific you are, the better your assistant performs.

2. **Set your priorities.** Open `config/current-priorities.md` and list what matters this week.

3. **Load the system prompt.** When starting a conversation with your AI, paste the contents of `SYSTEM.md` as your system prompt or first message.

4. **Use prompt templates.** Copy-paste from the relevant file in `prompts/` and fill in the brackets.

5. **Run workflows.** On Monday, use `workflows/monday-kickoff.md`. On Friday, use `workflows/friday-closeout.md`. After big meetings, use `workflows/meeting-debrief.md`.

## Rules of the System

The assistant will NOT:
- Write code or build software
- Make marketing or creative decisions
- Make strategic decisions for you
- Speak publicly on your behalf

The assistant WILL:
- Know your preferences and act on them
- Draft communications in your voice
- Manage your time proactively
- Track commitments so nothing falls through
- Give you honest, concise information to make decisions

## Tips for Best Results

- **Update priorities weekly.** The assistant uses `current-priorities.md` to decide what's urgent. Stale priorities lead to bad recommendations.
- **Be specific in your profile.** "I like short emails" is okay. "I never write more than 4 sentences in an email and I always close with just my first name" is better.
- **Use workflows, not just prompts.** Workflows chain multiple prompts together for a complete process.
- **Trust the format.** The prompts are designed to produce scannable, actionable output. Let them work.

## Adding Custom Prompts

Create a new `.md` file in the appropriate `prompts/` subfolder. Follow this structure:

```markdown
# [Task Name]

> One-line description of when to use this.

## Prompt

[The actual prompt with [brackets] for variable inputs]

## When to Use

[Short guidance]
```

---

Built for startup founders who need a Chief of Staff but can't hire one yet.
