---
name: quick-capture
description: "Instantly capture notes, ideas, links, and thoughts to the Inbox folder. Zero friction — just say it and it's saved. TRIGGERS: Use when user says 'note:', 'capture:', 'save this:', 'remember:', 'idea:', 'husk:', 'noter:', 'gem:', or any phrase that starts with a capture keyword followed by content. Also use when user says 'what's in my inbox', 'show inbox', 'clean up inbox', or 'organize inbox'. DO NOT fire when the capture is about the user themselves — phrases like 'remember this about me', 'save this about me', 'write this down about us' belong to the `relationship` skill, not here. Quick-capture is for external notes (tasks, ideas, links, reminders), not personal/relational content about the user."
---

# Quick Capture — Zero-Friction Note Taking

This skill lets the user dump thoughts, ideas, links, and notes instantly without thinking about where they go. Everything lands in `Inbox/` with a clear name so it's easy to find or sort later.

---

## CAPTURING A NOTE

When the user says something like "note: [content]" or "capture: [content]" or just tells you to remember something:

### 1. Determine the type
- **Quick thought / idea** → Save as a line in `Inbox/quick-notes.md`
- **Longer note (3+ sentences)** → Save as its own file in `Inbox/`
- **Link / URL** → Save in `Inbox/links.md` with context
- **Task / todo** → Save in `Inbox/tasks.md`

### 2. Save it immediately

**For quick thoughts** — append to `Inbox/quick-notes.md`:
```markdown
- [timestamp] [the note content]
```

**For longer notes** — create `Inbox/[descriptive-name].md`:
```markdown
# [Descriptive title]

**Captured:** [date and time]

[The full content]
```

**For links** — append to `Inbox/links.md`:
```markdown
- [timestamp] [URL] — [context about why this was saved]
```

**For tasks** — append to `Inbox/tasks.md`:
```markdown
- [ ] [the task] (captured [date])
```

### 3. Confirm instantly
Keep confirmation SHORT — one line max:
- "Saved to Inbox." 
- "Got it — saved as [filename]."
- "Noted."

Do NOT give a long explanation. The whole point is speed.

---

## VIEWING THE INBOX

When the user asks what's in their inbox or wants to see captured notes:

1. Read all files in `Inbox/`
2. Present a clean summary:

```
Your Inbox:

QUICK NOTES ([count]):
- [most recent notes, max 10]

LINKS ([count]):
- [recent links]

TASKS ([count]):
- [open tasks]

STANDALONE NOTES ([count]):
- [filenames with one-line summaries]

Want me to organize any of these into project folders?
```

---

## ORGANIZING THE INBOX

When the user asks to clean up or organize the inbox:

1. Read all inbox contents
2. For each item, suggest where it should go based on existing project folders
3. Present the suggestions and wait for approval before moving anything
4. Move approved items to their destination folders
5. Leave items the user isn't sure about in Inbox

**NEVER delete anything from Inbox without explicit permission.**
**NEVER move items without asking first.**

---

## RULES

- Speed is everything. Capture first, organize later.
- NEVER ask "where do you want me to save this?" — just save it to Inbox
- NEVER ask follow-up questions when capturing — save it and confirm in one line
- If the user's note is in a specific language, save it in that language
- Keep filenames descriptive but short: `idea-subscription-model.md` not `note-2026-04-09-about-potential-subscription-model-for-the-app.md`
- Always append to existing collection files (quick-notes.md, links.md, tasks.md) — never overwrite
- If Inbox/ doesn't exist, create it
- Timestamps use format: YYYY-MM-DD HH:MM
