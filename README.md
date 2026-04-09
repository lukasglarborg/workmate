# Workmate

Your personal AI workmate. Morning briefings, session memory, and instant note capture — ready in 60 seconds.

---

## What is this?

Workmate turns Claude into a daily work partner that actually remembers what you're working on. No setup, no code, no configuration — just install and say hello.

It's built for **regular people**, not developers. If you can send a text message, you can use Workmate.

## What you get

### 🌅 Daily Briefings
Say "good morning" and get a quick rundown of what you worked on yesterday, what's still open, and what needs attention. Like a colleague who actually remembers everything.

### 🧠 Session Memory
Everything you work on is logged automatically. Next time you open Claude, it knows exactly where you left off. No more "what were we doing again?"

### ⚡ Quick Capture
Say "note: call the electrician Friday" and it's saved instantly. Ideas, tasks, links, reminders — just say it and it's captured. Zero friction.

### 👋 Personal Setup
On first use, Workmate asks you a few questions and configures itself around you — your work, your language, your communication style.

## Install

### In Cowork (Claude Desktop App)
1. Go to **Plugins**
2. Search for **Workmate** or add via GitHub: `lukasglarborg/workmate`
3. Say **"hello"** — Workmate introduces itself and sets up your workspace

### In Claude Code (Terminal)
```bash
claude --plugin-dir path/to/workmate
```

## How to use it

You don't need to learn commands or remember keywords. Just talk normally:

| You say | What happens |
|---------|-------------|
| "Good morning" / "Hey" / "Hej" | Daily briefing with yesterday's recap and open tasks |
| "Note: remember to send invoice" | Saved instantly to your Inbox |
| "What were we working on?" | Summary of recent sessions |
| "I'm done" / "Goodbye" / "Vi ses" | Session saved, everything logged |

Works in **English** and **Danish** out of the box. Other languages adapt automatically during setup.

## What's inside

```
workmate/
├── .claude-plugin/
│   └── plugin.json
└── skills/
    ├── setup/          ← First-time onboarding (runs once)
    ├── daily-driver/   ← Morning briefings & session logging
    ├── memory/         ← Project memory across sessions
    └── quick-capture/  ← Instant note-taking to Inbox
```

## Want more?

Workmate is the free core. A **full starter kit** with 40 skills is available — including auto-organization, weekly reviews, research, budget planning, invoice generation, website building, and much more.

→ [Get the full Starter Kit](https://glarborg.gumroad.com/workmate)

## Who is this for?

Anyone who wants to get the most out of Claude — without being a tech expert. Workmate gives you a ready-made system that just works, so you can focus on your actual work.

## Questions?

Open an issue or start a discussion.
