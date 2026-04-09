---
name: memory
description: "Automatic context and memory management for workspace folders. Creates and maintains memory.md files in project folders so Claude always has context about what happened before. TRIGGERS: Use when Claude starts working in a project folder, when user mentions a specific project or folder, when user says 'what were we doing with X', 'status on X', 'what happened with X', or when finishing work in a project folder. Also use when user says 'remember this', 'save this context', or 'update memory'."
---

# Memory — Persistent Context for Projects

This skill ensures every important folder in the workspace has its own memory — a `memory.md` file that tracks what happened, what's open, and what decisions were made. The goal: Claude always has full context no matter which project is being worked on, and nothing is lost between sessions.

---

## WHEN THIS SKILL ACTIVATES

### Starting work in a project folder
When the user mentions a project, a folder, or asks to work on something:

1. **Check if the folder has a memory.md**
2. **If yes**: Read it silently and use it as context. Briefly mention what you remember: "Last time we worked on this, [brief summary]. Status: [current status]."
3. **If no**: Create one (see "Creating memory.md" below).

### Finishing work in a folder
When work in a folder is done (user switches topic, says goodbye, or work is complete):

1. **Update memory.md** with what was done
2. Keep it concise and useful for next time

### Folders that DON'T get memory files
- `Inbox/` — temporary holding area, too chaotic for context files
- `Sessions/` — has its own structure (daily logs)

---

## CREATING MEMORY.MD

When a project folder doesn't have memory.md, create one:

```markdown
# [Folder name] — Memory

## Status
[Current status in 1-3 sentences — what's the state of this project right now?]

## Recent Activity
| Date | What happened |
|------|--------------|
| [date] | [brief description] |

## Open Tasks
- [ ] [task 1]
- [ ] [task 2]

## Decisions
[Important decisions that were made, so we don't revisit them]

## Notes
[Anything else worth remembering]

---
*Maintained automatically by starter-kit memory skill*
```

---

## UPDATING MEMORY.MD

When finishing work in a folder:

### 1. Status section
Overwrite with the current status. This section is always "live" — it reflects where things stand right now.

### 2. Recent Activity
Add a new row at the TOP of the table with today's date and a brief description.
- **Keep max 15 entries** — delete the oldest if the list gets too long
- Be specific: "Added payment integration with Stripe" beats "Worked on the app"

### 3. Open Tasks
- Mark completed tasks with [x]
- Add new tasks that came up
- Remove tasks that are no longer relevant

### 4. Decisions
Only add decisions important enough to remember:
- Technology choices ("Using vanilla JS, not React")
- Strategic decisions ("Focusing on B2B market first")
- Things tried and dropped ("CSV import didn't work because X")

### 5. Tell the user what was updated
Brief and clear: "Updated memory for [folder]: added [X], marked [Y] as done."

---

## RULES

- **NEVER overwrite memory.md completely** — always read first, then edit/append
- Keep entries concise — this is a reference, not a journal
- Be specific about results, not just actions: "Built export feature, tested, works" > "Worked on export"
- If you're unsure whether something is worth remembering, err on the side of saving it
- Always tell the user when you create or update a memory file
- Memory files are a supplement to session logs, not a replacement. Session logs track everything by date. Memory files track everything by project.
