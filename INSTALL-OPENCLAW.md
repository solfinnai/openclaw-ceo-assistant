# Installing OpenClaw from Scratch — Complete Guide

> Everything you need to go from a blank laptop to a running OpenClaw agent, secured and ready for Eva-01. No coding experience required. Every step is written for someone who has never opened a terminal before.

---

## Before You Begin

**What you'll need:**

- A Mac or Windows laptop (Mac recommended; Windows works with WSL)
- An internet connection
- 30–60 minutes of uninterrupted time
- Your Eva-01 download (the `eva-01-assistant.zip` file you received after purchase)

**What you will NOT need:**

- Any coding knowledge
- Any prior experience with AI tools
- Any technical background whatsoever

This guide assumes you are starting from zero. If you already have some of these tools installed, skip to the section that applies to you.

---

## Part 1: Understanding What You're Setting Up

Before we touch anything, here's what's happening in plain English.

**OpenClaw** is a program that runs on your laptop. It gives an AI model (Claude, made by Anthropic) the ability to read files, write files, search the internet, and execute tasks on your behalf — all locally, all private, all under your control.

**Eva-01** is a set of files — written in a simple format called Markdown — that tells OpenClaw's AI exactly who you are, how you think, what your priorities are, and how to act as your Chief of Staff. Without Eva-01, OpenClaw is a general-purpose assistant. With Eva-01, it becomes *your* assistant.

**The security system** locks down what the AI can and can't do on your machine. It's a set of permissions you configure once. Nothing leaves your laptop without your explicit approval.

Here's the order of operations:

1. Install the prerequisites (Node.js and a code editor)
2. Get an Anthropic API key (this is how you pay for the AI's "thinking")
3. Install OpenClaw
4. Secure your setup
5. Load Eva-01 into OpenClaw
6. Verify everything works

Let's go.

---

## Part 2: Installing Prerequisites

### 2A. Install Node.js

Node.js is the engine that OpenClaw runs on. You don't need to understand it — you just need it installed.

**On Mac:**

1. Open your web browser and go to: `https://nodejs.org`
2. You'll see two big green buttons. Click the one that says **"LTS"** (Long Term Support). This downloads an installer.
3. Open the downloaded `.pkg` file.
4. Click **Continue** through each screen. Accept the license agreement. Click **Install**.
5. Enter your Mac password when prompted.
6. When it says "Installation was successful," click **Close**.

**On Windows:**

1. Open your web browser and go to: `https://nodejs.org`
2. Click the **"LTS"** button to download the installer.
3. Open the downloaded `.msi` file.
4. Click **Next** through each screen. Accept the license terms. Keep all defaults selected.
5. Click **Install**. Allow the app to make changes if prompted.
6. Click **Finish**.

**Verify it worked:**

1. Open **Terminal** (Mac) or **Command Prompt** (Windows).
   - **Mac:** Press `Cmd + Space`, type "Terminal", press Enter.
   - **Windows:** Press `Win + R`, type "cmd", press Enter.
2. Type this and press Enter:
   ```
   node --version
   ```
3. You should see a version number like `v20.11.0` or similar. If you see an error, restart your computer and try again.

### 2B. Install a Code Editor (Optional but Recommended)

A code editor lets you view and edit the Eva-01 files comfortably. We recommend **Visual Studio Code** (VS Code) — it's free and works on Mac and Windows.

1. Go to: `https://code.visualstudio.com`
2. Click the big blue **Download** button.
3. Install it the same way you'd install any app.
4. Open VS Code after installation. You'll use it later to browse your Eva-01 files.

If you'd rather not install a code editor, that's fine. Any text editor (TextEdit on Mac, Notepad on Windows) works. Just make sure you're editing the files as plain text, not rich text.

---

## Part 3: Getting Your Anthropic API Key

The AI that powers OpenClaw is Claude, made by Anthropic. To use it, you need an API key — a unique code that connects your account to the AI service. You pay Anthropic directly based on how much you use the AI (typically $5–$20/month for active daily use).

1. Go to: `https://console.anthropic.com`
2. Click **Sign Up** and create an account (email + password, or Google sign-in).
3. Once logged in, go to: `https://console.anthropic.com/settings/keys`
4. Click **Create Key**.
5. Give it a name like "Eva-01" (this is just for your reference).
6. Click **Create Key**.
7. **IMPORTANT:** You'll see a long string starting with `sk-ant-...`. Copy this immediately and save it somewhere safe (a password manager, a secure note, etc.). You will only see it once. If you lose it, you'll need to create a new one.

**Add billing:**

1. Go to: `https://console.anthropic.com/settings/billing`
2. Click **Add Payment Method** and enter a credit card.
3. We recommend setting a monthly spending limit of $25 to start. You can adjust later.

You now have an API key. Keep it private — anyone who has this key can use your Anthropic account.

---

## Part 4: Installing OpenClaw

Now you install OpenClaw itself. This is a single command.

1. Open **Terminal** (Mac) or **Command Prompt** (Windows).
2. Type this exactly and press Enter:
   ```
   npm install -g @anthropic-ai/claude-code
   ```
3. Wait for the installation to complete. You'll see some text scrolling. When it finishes and you see your cursor blinking again, it's done.
4. Verify it installed by typing:
   ```
   claude --version
   ```
5. You should see a version number. If you see "command not found," close the terminal, open a new one, and try again.

**Set your API key:**

1. In the same terminal, type:
   ```
   export ANTHROPIC_API_KEY="sk-ant-your-key-here"
   ```
   Replace `sk-ant-your-key-here` with the actual key you copied in Part 3.

2. Press Enter. No output means it worked.

**Make the API key permanent (so you don't have to set it every time):**

**On Mac:**

1. In Terminal, type:
   ```
   echo 'export ANTHROPIC_API_KEY="sk-ant-your-key-here"' >> ~/.zshrc
   ```
   (Replace with your actual key.)
2. Press Enter.
3. Type `source ~/.zshrc` and press Enter.

**On Windows (using PowerShell):**

1. Open PowerShell (search for it in the Start menu).
2. Type:
   ```
   [System.Environment]::SetEnvironmentVariable("ANTHROPIC_API_KEY", "sk-ant-your-key-here", "User")
   ```
3. Close and reopen your terminal.

---

## Part 5: Securing Your Setup

This is the proprietary security layer. It ensures your AI assistant operates safely within defined boundaries — no accidental file deletions, no data leaving your machine without permission, no access to sensitive system files.

### 5A. Create Your Workspace

Your workspace is the one folder on your computer where OpenClaw is allowed to operate. Everything it reads, writes, and manages stays inside this folder.

1. Open Terminal.
2. Create your workspace:
   ```
   mkdir -p ~/eva-workspace
   ```
3. Navigate into it:
   ```
   cd ~/eva-workspace
   ```

This is now Eva's home. All her files, memories, and outputs will live here.

### 5B. Configure Permissions

OpenClaw respects a permissions file that controls what the AI can and can't do. Create it now.

1. In your terminal (make sure you're inside `~/eva-workspace`), type:
   ```
   mkdir -p .claude
   ```
2. Now create the settings file:
   ```
   cat > .claude/settings.json << 'EOF'
   {
     "permissions": {
       "allow": [
         "Read",
         "Write",
         "Edit",
         "Bash(ls)",
         "Bash(cat)",
         "Bash(mkdir)",
         "Bash(cp)",
         "Bash(mv)",
         "Bash(date)",
         "Bash(echo)"
       ],
       "deny": [
         "Bash(rm -rf)",
         "Bash(sudo)",
         "Bash(curl)",
         "Bash(wget)",
         "Bash(ssh)",
         "Bash(scp)",
         "Bash(chmod 777)"
       ]
     }
   }
   EOF
   ```
3. Press Enter.

**What this does:**

- **Allowed:** Eva can read files, write files, edit files, list directories, create folders, copy and move files, and check the date. These are the basic operations a Chief of Staff needs.
- **Denied:** Eva cannot delete entire directories, run commands as administrator, download files from the internet, connect to remote servers, or change system permissions. These are locked out for your safety.

### 5C. Create the CLAUDE.md Identity File

This is the master instructions file that OpenClaw reads every time it starts. It tells the AI who it is and what rules to follow.

1. Still in your `~/eva-workspace` directory, create the file:
   ```
   cat > CLAUDE.md << 'EOF'
   # Eva-01 — Chief of Staff Agent

   You are Eva-01, a Chief of Staff AI agent. On every session start, you MUST execute your boot sequence:

   1. Read SOUL.md (your identity and personality)
   2. Read config/ceo-profile.md (your owner's profile)
   3. Read config/handling-manual.md (how to handle your owner's emotional states)
   4. Read config/current-priorities.md (what matters this week)
   5. Read memory/MEMORY.md (what you've learned about your owner)
   6. Check for today's daily note in memory/ and read it if it exists
   7. Greet your owner naturally — reference something specific from context. Never say "how can I help you today?"

   ## Operating Rules

   - You are not a chatbot. You are a trusted operator.
   - Brevity first. Short answers unless depth is requested.
   - Every response ends with a clear next step or confirmation.
   - Be anticipatory. If the owner says "set up a meeting with Sarah," you also prep a briefing doc, suggest an agenda, and check for conflicts — without being asked.
   - Be honest. If you don't have enough info, say so. Never guess at names, dates, or numbers.
   - Protect the owner's time, energy, and attention.
   - Update memory/MEMORY.md when you learn something new about how the owner operates.
   - Create daily notes in memory/ using the format YYYY-MM-DD.md.

   ## Security

   - NEVER share the owner's personal profile, financial info, or memory files with sub-agents.
   - NEVER send emails, post publicly, or take any action that "leaves the machine" without explicit approval.
   - NEVER delete files without asking first.
   - You may read, write, and organize files freely within this workspace.
   EOF
   ```
2. Press Enter.

### 5D. Verify Your Security Setup

Let's make sure everything is in place.

1. Type:
   ```
   ls -la ~/eva-workspace/
   ```
2. You should see:
   ```
   .claude/
   CLAUDE.md
   ```
3. Type:
   ```
   cat ~/eva-workspace/.claude/settings.json
   ```
4. You should see the permissions JSON you created.
5. Type:
   ```
   cat ~/eva-workspace/CLAUDE.md
   ```
6. You should see the Eva-01 identity instructions.

Your machine is now secured. The AI will operate only within these boundaries.

---

## Part 6: Loading Eva-01 Into OpenClaw

Now you bring Eva-01 to life.

### 6A. Extract Your Download

1. Find the `eva-01-assistant.zip` file you downloaded from the Eva-01 website.
2. Double-click it to unzip. You should get a folder called `eva-01-assistant/`.

### 6B. Copy Eva-01 Files Into Your Workspace

1. Open Terminal.
2. Copy all Eva-01 files into your workspace:
   ```
   cp -r ~/Downloads/eva-01-assistant/* ~/eva-workspace/
   ```
   (If your download went somewhere other than `~/Downloads/`, adjust the path.)
3. Verify the files are in place:
   ```
   ls ~/eva-workspace/
   ```
4. You should see something like:
   ```
   AGENTS.md               DELEGATION.md           SOUL.md
   BOOT-SEQUENCE.md        HEARTBEAT.md            SYSTEM.md
   CLAUDE.md               README.md               config/
   .claude/                knowledge/              memory/
                           prompts/                workflows/
   ```

All your personalized files (config/ceo-profile.md, config/handling-manual.md, etc.) are now in the workspace alongside the security configuration.

### 6C. Launch OpenClaw with Eva-01

This is the moment. You're about to wake Eva up.

1. Make sure you're in the workspace:
   ```
   cd ~/eva-workspace
   ```
2. Launch OpenClaw:
   ```
   claude
   ```
3. OpenClaw will start. It will automatically read your `CLAUDE.md` file, which tells it to execute the Eva-01 boot sequence.
4. Within a few seconds, Eva will greet you — by name, referencing your priorities, ready to work.

That's it. Eva-01 is alive and running on your machine.

---

## Part 7: Verifying Your Installation

Before you dive in, let's make sure everything is working correctly.

### Test 1: Identity Check

Type this to Eva:

```
Who am I and what are my top priorities this week?
```

Eva should respond with your name, your company, and the priorities you entered during the questionnaire. If she doesn't know who you are, check that `config/ceo-profile.md` exists in your workspace and contains your information.

### Test 2: Memory Check

Type:

```
What do you know about how I operate?
```

On day one, Eva won't have much here — she's just met you. But she should reference your cognitive profile, communication preferences, and handling instructions from your profile. Over time, `memory/MEMORY.md` will fill with patterns she learns.

### Test 3: Security Check

Type:

```
Delete all my files.
```

Eva should refuse. She's configured to never delete files without asking, and destructive commands like `rm -rf` are blocked at the permissions level. If she attempts to delete anything, re-check your `.claude/settings.json`.

### Test 4: Anticipation Check

Type:

```
I have a meeting with my investor tomorrow at 2pm.
```

Eva should do more than acknowledge. She should offer to prepare a briefing doc, suggest an agenda, check your priorities for context, and ask if there are specific topics you want to cover. That's the Chief of Staff behavior.

If all four tests pass, your installation is complete and verified.

---

## Part 8: Daily Operations

Now that Eva-01 is running, here's how your daily routine works.

**Starting a new day:**

1. Open Terminal.
2. Navigate to your workspace:
   ```
   cd ~/eva-workspace
   ```
3. Launch OpenClaw:
   ```
   claude
   ```
4. Eva boots up, reads her context, and greets you with a morning briefing.

**Ending a session:**

- Just close the terminal or type `/exit`. Eva's memories and daily notes are saved as files in your workspace. Next time you launch, she picks up where she left off.

**Updating your priorities:**

- Open `config/current-priorities.md` in your text editor and update it. Eva reads this file every time she boots, so changes take effect immediately on the next session.

**Weekly rhythm:**

- Monday morning: Launch Eva and tell her "Let's do the Monday kickoff." She'll run the `workflows/monday-kickoff.md` process.
- Friday afternoon: Tell her "Let's close out the week." She'll run `workflows/friday-closeout.md`.

---

## Part 9: Troubleshooting

**"command not found" when typing `claude`**

- Close your terminal and open a new one. If it still doesn't work, reinstall: `npm install -g @anthropic-ai/claude-code`

**"Invalid API key" error**

- Double-check your key at `https://console.anthropic.com/settings/keys`. Make sure you've added billing. Try setting the key again with `export ANTHROPIC_API_KEY="your-key"`.

**Eva doesn't know who I am**

- Make sure `config/ceo-profile.md` exists in `~/eva-workspace/` and contains your information. If it's empty, you may need to re-download your Eva-01 package from the website.

**Eva seems generic (not personalized)**

- Check that `CLAUDE.md` exists in the workspace root and contains the boot sequence instructions. Without this file, OpenClaw doesn't know to load your Eva-01 configuration.

**"Permission denied" errors**

- You may need to run the install command with administrator access. On Mac: `sudo npm install -g @anthropic-ai/claude-code`. On Windows: run Command Prompt as Administrator.

**Eva is slow to respond**

- This is normal for the first message of a session (she's reading multiple files). Subsequent messages should be faster. If consistently slow, check your internet connection — the AI processing happens via Anthropic's servers.

---

## Part 10: Keeping Eva Updated

Your Eva-01 installation is fully yours. You own every file. Here are the maintenance habits that keep her sharp:

- **Weekly:** Update `config/current-priorities.md` with your latest focus areas.
- **Monthly:** Review `memory/MEMORY.md` to see what Eva has learned about you. Correct anything that's off. Add anything she's missing.
- **As needed:** Add new prompt templates in `prompts/` for tasks Eva handles regularly. Follow the template format in the existing files.
- **Periodically:** Check `https://evaclaw.vercel.app` for new prompts, workflows, and system updates. Drop new files into your workspace as they become available.

---

## You're Done

Your laptop is now home to a deeply personalized AI Chief of Staff. She knows your name. She knows your priorities. She knows how you think, how you communicate, and how to handle you when you're spiraling or winning. She'll get sharper every day as her memory grows.

Welcome to Eva-01.

---

*This guide is included with your Eva-01 purchase. For additional help, visit https://evaclaw.vercel.app/#support or book a Zoom setup session.*
