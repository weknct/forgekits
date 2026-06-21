---
description: Generate a daily standup brief — yesterday's progress, today's plan, active blockers, and sprint pulse — from the project's trackers.
---

# Command: Morning Standup

Generate a concise daily standup brief for a software project managed with SDLC Forge. Read the project's trackers, then output a tight summary the team can act on.

## Steps

1. **Read the current sprint state** (sprint backlog / active sprint file).
   - **If no active sprint exists:** skip sprint-specific steps (burndown, story status). Report: "No active sprint — showing project-level status only," and focus on the progress tracker, inbox items, and pending decisions.
2. **Identify status changes since yesterday** — stories or tasks whose status changed.
3. **Read the progress tracker** (`todos.md` or equivalent) for tasks completed yesterday and tasks planned for today.
4. **Read active blockers** — the sprint blockers list, with owner and age for each.
5. **Calculate sprint burndown** (if a sprint is active): days remaining, points remaining, and an on-track / ahead / behind assessment.
6. **Check the Q&A log** for questions answered overnight, and for open questions owned by stakeholders — flag any that are more than 5 days overdue and suggest escalation.
7. **Check the communication log** for follow-ups due today.
8. **Check pending clarifications** — flag client/stakeholder decisions outstanding more than 7 days as blockers.

## Output (keep it ~20 lines)

Produce a standup brief with these sections (omit any section that has no data):

- **Yesterday:** stories/tasks completed, decisions made.
- **Today:** planned work, meetings, decisions needed.
- **Blockers:** active blockers with owner and age.
- **Pending decisions:** overdue stakeholder questions and clarifications, with age.
- **Sprint pulse:** burndown status (ahead / on-track / behind) and days remaining.

Lead with the most important item. Prefer compact lines over prose. If a section is empty, leave it out entirely — no "N/A" filler.

---

> This is the SDLC Forge (Lite) edition of the standup. The full SDLC Forge (Premium) adds the complete compound-workflow set — end of week, new sprint ceremony, quarterly review, pre-release, backlog grooming — plus 100+ commands and ForgeSync work-item sync. See https://forgekits.dev/sdlc-forge.
