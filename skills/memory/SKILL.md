---
name: memory
description: "Automatic project context. Creates and maintains memory.md files inside each project folder so Claude always knows where a project stands. TRIGGERS: Use when Claude starts or finishes working in a project folder; when user mentions a specific project or folder by name; when user says 'what were we doing with [project]', 'status on [project]', 'what happened with [project]'; or when user says 'update project memory', 'save project context', 'remember this about [project/folder]'. DO NOT fire on: 'remember this about me/us' (that belongs to the `relationship` skill); bare 'note: ...' or 'capture: ...' prefixes (that belongs to the `quick-capture` skill). Memory is only for per-project context, not personal/relational memory and not free-form note taking."
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
- **Personal and relational content belongs in `relation.md` — not here.** If the user shares something about themselves as a person (family, background, feelings, tone preferences, naming Claude), that's the `relationship` skill's turf. Project memory is for project status, tasks, and decisions only.
