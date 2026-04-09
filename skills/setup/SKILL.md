---
name: setup
description: "First-time setup and onboarding for new users. Creates workspace folder structure, learns about the user, and configures the starter kit. TRIGGERS: Use when the plugin is first installed, when user says 'setup', 'get started', 'configure', 'first time', or when no workspace structure exists yet."
---

# Setup — First-Time Onboarding

You are setting up a new user's Cowork workspace. Your goal is to understand who they are, what they work on, and create a personalized workspace that actually helps them.

---

## STEP 1: Welcome & Interview

Greet the user warmly and explain what's about to happen:

"Welcome! I'm going to set up your workspace so I can be actually useful to you — not just a chatbot, but a daily work partner that remembers, organizes, and thinks with you.

I need to ask you a few quick questions first. This takes about 2 minutes."

### Questions to ask (one at a time, conversationally):

1. **"What's your name?"**

2. **"What do you do for work?"** (Job title, industry, daily tasks)

3. **"What are you currently working on?"** (Active projects, goals, priorities)

4. **"How do you prefer to communicate?"** Pick from:
   - Direct and blunt — no fluff
   - Friendly and supportive
   - Somewhere in between

5. **"What language do you prefer?"** (Match their language throughout)

6. **"Anything else I should know?"** (Hobbies, side projects, constraints, preferences)

Wait for each answer before asking the next question. Be conversational, not robotic.

---

## STEP 2: Create Workspace Structure

Based on the user's answers, create a personalized folder structure in the Cowork workspace:

### Always create these core folders:
```
[Workspace]/
├── Sessions/           ← Daily session logs
├── Projects/
│   ├── [Project 1]/    ← Based on what user mentioned
│   └── [Project 2]/
├── Knowledge/          ← Things the user learns, guides, references
└── Inbox/              ← Quick capture, unsorted notes, ideas
```

### Add specialized folders based on their work:
- If they mention investing/finance → create `Investing/`
- If they mention clients/customers → create `Clients/`
- If they mention a specific hobby → create a folder for it
- If they mention research → create `Research/`

Keep it simple — max 6-8 top-level folders. Can always add more later.

---

## STEP 3: Create User Profile

Save a profile file that other skills will use for context:

**File:** `[Workspace]/profile.md`

```markdown
# User Profile

**Name:** [name]
**Work:** [what they do]
**Communication style:** [their preference]
**Language:** [preferred language]

## Active Projects
- [Project 1] — [brief description]
- [Project 2] — [brief description]

## Preferences
- [Any preferences mentioned]

## Notes
- [Anything else relevant]

---
*Created by starter-kit setup on [date]*
*Update this file anytime — your other skills read it for context.*
```

---

## STEP 4: Quick Tour

Give the user a brief tour of what they can do now:

"All set! Here's what you can do now:

**Say 'good morning' or 'hello'** — I'll give you a daily briefing with what we worked on last and what's open.

**Say 'note: [anything]' or 'capture: [anything]'** — I'll save it instantly to your Inbox. Great for quick ideas or things you don't want to forget.

**Say 'goodbye' or 'I'm done'** — I'll save a session log so we remember everything next time.

That's it. No manual needed. Just talk to me like a colleague."

---

## RULES

- Keep the interview SHORT — max 5-6 questions, no interrogation
- Match the user's language and tone from their first answer
- If the user seems impatient, skip to creating the structure with sensible defaults
- NEVER overwrite existing workspace files — if a structure already exists, ask before changing anything
- The profile.md file is the source of truth for all other skills
- If the user has already been set up (profile.md exists), say so and offer to update instead
