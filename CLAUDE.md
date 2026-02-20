# Daily Work — Claude Instructions

## Purpose

This folder contains dated daily task files (e.g., `2026-02-19.md`) and is the primary workspace for day-to-day client work at TMSA.

### Configuration Files (`.claude/` directory)
- `dashboard-design-spec.md` — Design specifications for consistent dashboard generation (colors, typography, spacing)
- `tmsa-business-context.md` — TMSA business context, client profiles, and company background (reference for understanding scope and clients)
- `settings.local.json` — Local Claude Code settings

---

## SESSION START — Do This First, Every Time

1. Find the most recent dated `YYYY-MM-DD.md` file in this folder
2. Read it in full — tasks, completed items, notes, and session log
3. Confirm to the user: "I've read [filename] — here's where things stand: [brief summary of open tasks]"
4. Display the shortcuts list (from the SHORTCUTS section below) so the user can see all available commands

The latest file IS the task manager. It contains everything — never assume you know the current state without reading it first.

---

## SHORTCUTS

These one-word commands are always active. Display this list at session start and whenever the user types `shorts`.

**⚠️ CRITICAL RULE — Task Numbers:**
- User posts a **number only** (e.g. `26`) → **ALWAYS show task detail. NEVER mark complete.**
- User posts **number + "done"** (e.g. `26 done`) → mark task complete.
- These are two completely separate actions. A number alone is NEVER a completion command.

| Shortcut | What it does |
|----------|-------------|
| `shorts` | Display this full shortcuts list |
| `tasks` | Show today's full task list |
| `overdue` | Show only overdue tasks |
| `today` | Show Priority tasks only |
| `status` | One-line summary: X done, X remaining, X overdue |
| `[N]` | Show full detail of task N — NEVER marks complete (e.g. `26`) |
| `[N] done` | Mark task N as complete — requires the word "done" (e.g. `26 done`) |
| `notes` | Show today's notes section |
| `log` | Show today's session log |
| `week` | Show all tasks completed this week |
| `report` | Generate and open the HTML dashboard |
| `enhancements` | Show pending enhancements list |
| `update` | Pre-commit checkpoint: (1) verify all task statuses in daily .md are accurate, (2) add carry-forward note to ## Notes for anything urgent/unresolved, (3) write current shortcuts/enhancements to CLAUDE.md and enhancements.md, (4) add timestamped session log entry |
| `git` | Commit and push daily-work folder to GitHub |

---

## DAILY FILE — When to Create It

**Do NOT create a new daily file at the start of a session.**

Create a new `YYYY-MM-DD.md` file (using today's date) **only when the first task of the day is assigned or actioned.**

---

## DAILY FILE — What Goes In It

Each new daily file is a **complete, cumulative record** — not just today's tasks. It must include:

1. All incomplete (`[ ]`) and in-progress (`[~]`) tasks carried forward from the previous file
2. Any new tasks added today
3. All context, sub-bullets, and notes from carried tasks (do not strip detail)
4. A fresh `## Completed` section (today's completions only)
5. A fresh `## Notes` section
6. A fresh `## Session Log` section

Mark each carried task with `*(carried from YYYY-MM-DD)*` so it's clear what's new vs outstanding.

**The latest file must always be a complete, standalone briefing document.** Anyone reading only the latest file should understand the full picture.

---

## UPDATES DURING THE SESSION

**Every time any of the following happens, immediately update the current day's file:**

1. A task is marked as complete
2. A new task, action, or reminder is added
3. A key decision is made or a direction is confirmed
4. Meaningful context is shared (client feedback, constraints, change of plan)

Append a timestamped entry to the `## Session Log` section:

```
### [HH:MM] — [Short description]
[1–3 sentences summarising what happened, what was decided, or what was completed.]
```

Use 24h format, Cape Town / SAST (UTC+2).

---

## END OF DAY — Before Signing Off

When the user signals the session is ending (goodbye, wrapping up, done for today, etc.):

1. Add a carry-forward note to the `## Notes` section summarising anything urgent for tomorrow
2. Prompt the end-of-day checklist:
   - [ ] Back up workspace: `cd /Users/jacques/Documents/Claude && git add . && git commit -m "Backup $(date +%Y-%m-%d)" && git push`
   - [ ] Any open client work committed to its own repo?
   - [ ] Tasks to carry forward to tomorrow noted?

---

## WEEKLY REPORT — Every Friday

Generate a weekly summary file named `week-YYYY-MM-DD.md` (Friday's date).

- Scan all daily files for the week
- Compile every `[x]` completed task, grouped by client/category
- Include the date each item was completed

**Trigger command:** "Generate this week's completed tasks report"

---

## DASHBOARD WORKFLOW

**Reference Files:**
- `dashboard-template.html` — Master template with exact HTML structure and CSS (read this for layout)
- `dashboard-design-spec.md` — Complete design specification (colors, typography, spacing)
- `dashboard-YYYY-MM-DD.html` — Generated dashboard file (created fresh for each date)

### When to Regenerate
- Each time tasks are updated (completed, added, or changed)
- When the user requests "generate the dashboard again"
- At the start of a new daily file or date

### How to Generate
1. Read the current daily file to get all task statuses
2. Reference `dashboard-template.html` for exact HTML structure
3. Reference `dashboard-design-spec.md` for colors, fonts, spacing (no need to memorize)
4. Count tasks by category: Priority, This Week, Build, Admin, Done This Week
5. Generate fresh HTML using template as guide
6. Replace `[PLACEHOLDERS]` with actual data (date, task counts, task content)
7. Verify: correct date/day, all tasks reflected, completed tasks strikethrough + green
8. Save as `dashboard-YYYY-MM-DD.html` in this folder
9. Open in browser

### Styling Standards (Fixed)
- **Theme:** Light mode — background #e2e8f0, text #0f172a
- **Colors:** All defined in CSS `:root` variables (see design-spec)
- **Typography:** Space Grotesk for headlines, Inter for body (see font sizes in design-spec)
- **Visual separation:** 2px border-top dividers between major sections
- **Section headers:** Uppercase, bold (font-weight: 700)

### "Completed This Week" Format
- Bottom bar shows: **"Completed This Week"** (Monday–Sunday, not daily)
- Stat card label: "Done This Week" with total count
- Update as tasks are completed during the session
- Append each newly completed task to the completed list

---

## GITHUB PAGES — External Sharing

**Repository:** https://github.com/tmsatech-2026/00-daily-indaba

### Setup (Already Configured)
- GitHub Pages enabled on `main` branch, root folder
- Dashboard files deployed as static HTML pages
- Public repo — shareable externally

### Sharing Dashboards Externally
Each generated dashboard is automatically accessible via GitHub Pages:

```
https://tmsatech-2026.github.io/00-daily-indaba/dashboard-YYYY-MM-DD.html
```

**Example:**
- Date 19 Feb 2026 → https://tmsatech-2026.github.io/00-daily-indaba/dashboard-2026-02-19.html

### Workflow: Update & Share
1. Generate new `dashboard-YYYY-MM-DD.html` (using daily file data)
2. Commit: `git add dashboard-YYYY-MM-DD.html && git commit -m "Update dashboard for YYYY-MM-DD"`
3. Push: `git push origin main`
4. Share the GitHub Pages URL with recipient
5. Dashboard is live within seconds

### What Gets Pushed
- `dashboard-YYYY-MM-DD.html` (active dashboards)
- `dashboard-template.html` (reference, for consistency)
- `dashboard-design-spec.md` (reference, for styling)
- `CLAUDE.md` (documentation)
- Current `YYYY-MM-DD.md` (optional, for context)

### Notes
- No sensitive data in dashboards (external sharing is safe)
- Each date gets its own dashboard file (easy versioning)
- GitHub Pages serves all `.html` files automatically
- Updates deploy within seconds of push

---

## DAILY FILE STRUCTURE

```markdown
# Daily Work — YYYY-MM-DD

## Tasks

### 🔴 Priority
- [ ] ...

### 🟡 This Week
- [ ] ...

### 🔵 Build (Claude Code)
- [ ] ...

### 🔴 Admin
- [ ] ...

## Completed

<!-- Today's completions only -->

## Notes

<!-- Carry-forwards, client context, thoughts -->

## Session Log

<!-- Auto-appended during session — do not edit manually -->
```
