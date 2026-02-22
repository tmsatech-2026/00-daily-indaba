# Daily Work — Claude Instructions

## Purpose

This folder contains dated daily task files (e.g., `2026-02-19.md`) and is the primary workspace for day-to-day client work at TMSA.

### Configuration & Reference Files

**`.claude/` directory (internal reference docs):**
- `dashboard-template.html` — **Master template — source of truth for all dashboard generation**
- `dashboard-design-spec.md` — Design specifications for consistent dashboard generation (colors, typography, spacing)
- `dashboard-generation-guide.md` — Step-by-step dashboard generation checklist & verification process
- `tmsa-business-context.md` — TMSA business context, client profiles, and company background
- `settings.local.json` — Local Claude Code settings

**`product/` directory (external marketing & product docs):**
- `Daily-Work.html` — Sales/overview document explaining the system (for GitHub sharing with other Claude Code users)
- `diagram.html` — System overview diagram (visual explanation for new users)

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
| `new` | Add a new task — type `new`, then describe the task (text or image). I extract and summarize it. |
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
| `end` | Full close-out sequence — see END OF DAY section below |

---

## NEW TASK WORKFLOW — `new` shortcut

**Workflow:**
1. Type: `new`
2. Provide task description(s) via:
   - **Text:** Type or paste the task details
   - **Image:** Upload a screenshot, photo, or reference image
   - **Multiple tasks:** Provide all tasks in one message (text or image)
3. I extract and summarize each task:
   - Task name and category (Priority, This Week, Build, Admin, etc.)
   - Key details and context
   - Due date or timeline (if applicable)
   - Sub-tasks or dependencies (if applicable)

**MANDATORY CONFIRMATION STEP:**
- I will list ALL extracted tasks clearly
- I will ask: "Should I add these tasks? Any corrections?"
- I will NEVER add tasks until you confirm

**Once Confirmed:**
- Tasks are added to the daily file
- Session log entry documents all new tasks
- Task numbers and categories are printed for verification

**Example (Single Task):**
```
User: new
User: Redesign Les Chambres website homepage

Claude:
**TASK EXTRACTED**
- Task: Les Chambres — website redesign
- Category: This Week
- Details: Redesign website homepage, update accommodation photos section

Should I add this as task [X] under This Week? Any changes?

User: yes
Claude: ✅ Task X added under This Week.
```

**Example (Multiple Tasks):**
```
User: new
User: [uploads Slack screenshot with two action items]

Claude:
**TASKS EXTRACTED**

1. Task: Fix form validation on checkout
   Category: Build (Claude Code)
   Details: Ensure all form fields validate before submission

2. Task: Add email notification template
   Category: Build (Claude Code)
   Details: Create reusable email template for automated notifications

Should I add both as tasks [X] and [Y] under Build? Any changes?

User: yes, add both
Claude: ✅ Task X and Y added under Build (Claude Code).
```

---

## DAILY FILE — When to Create It

**Do NOT create a new daily file at the start of a session.**

Create a new `YYYY-MM-DD.md` file (using today's date) **only when the first task of the day is assigned or actioned.**

When creating a new daily file, also **archive the previous day's files**:

```
mv YYYY-MM-DD.md archive/
mv dashboard-YYYY-MM-DD.html archive/
```

The `archive/` folder keeps the root clean. Only the current day's `.md` and `dashboard-*.html` live in the root.

---

## DAILY FILE — What Goes In It

Each new daily file is a **complete, cumulative record** — not just today's tasks. It must include:

1. All incomplete (`[ ]`) and in-progress (`[~]`) tasks carried forward from the previous file
2. Any new tasks added today
3. All context, sub-bullets, and notes from carried tasks (do not strip detail)
4. **`## Completed` section with full week's running total:**
   - **Same week** (Mon–Sun): Carry forward ALL completed tasks from previous day with dates
   - **New week** (Monday of new week): Fresh, empty `## Completed` section
   - Format: `*Carried forward from week (Mon 17–Sun 23):*` at top, `*Today's completions:*` for new items
5. A fresh `## Notes` section
6. A fresh `## Session Log` section

Mark each carried task with `*(carried from YYYY-MM-DD)*` so it's clear what's new vs outstanding.

**The latest file must always be a complete, standalone briefing document.** Anyone reading only the latest file should understand the full picture, including all week's progress so far.

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

## END OF DAY — `end` shortcut

When the user types `end` (or signals the session is ending: goodbye, wrapping up, done for today, etc.), run the full close-out sequence in this order:

**Step 1 — Verify task statuses**
- Read today's daily `.md` file
- Check that all task statuses (`[ ]`, `[~]`, `[x]`) accurately reflect what actually happened this session
- Correct any discrepancies

**Step 2 — Add carry-forward note**
- Add (or update) a carry-forward note to the `## Notes` section
- Flag anything urgent, unresolved, or that must be picked up first tomorrow
- Format:
  ```
  **⚠️ CARRY FORWARD — [Date]:**
  [Item 1 — brief description]
  [Item 2 — brief description]
  ```

**Step 3 — Add end-of-day session log entry**
- Append a timestamped entry to `## Session Log`:
  ```
  ### [HH:MM] — End of day
  Session closed. [1 sentence on what was accomplished.] Carry-forwards noted.
  ```

**Step 4 — Update CLAUDE.md and enhancements.md**
- If any new shortcuts or workflows were added/changed during the session, write them to `CLAUDE.md`
- If any enhancements were applied, move them to the Applied section in `enhancements.md`

**Step 5 — Regenerate the HTML dashboard**
- Run the `report` shortcut to generate a fresh `dashboard-YYYY-MM-DD.html`
- This ensures tomorrow's starting view is current and accurate

**Step 6 — Commit and push to GitHub**
- Run: `cd /Users/jacques/Documents/Claude/00-daily-indaba && git add . && git commit -m "End of day $(date +%Y-%m-%d)" && git push`

**Step 7 — Print tomorrow's brief**
- After the push, output a structured "Tomorrow Brief" directly in the conversation:
  ```
  ## Tomorrow — [Day, Date]

  **Pick up first:**
  [Most urgent item]

  **Open tasks ([N] remaining):**
  [List of priority and this-week items still open]

  **Watch:**
  [Any deadlines, waiting items, or carry-forwards to keep in mind]
  ```
- Also write this brief as a `## Tomorrow Brief` block at the bottom of today's `## Notes` section so it's visible when the next session opens the file

---

**Note:** If the user says goodbye or signals session end without typing `end`, prompt them: "Type `end` to run the close-out sequence before you go."

---

## WEEKLY SUMMARY — Start of New Week

**File:** `weekly-summary.md` — persistent, cumulative archive of completed tasks by week

**Workflow:**
When starting a new week's work (typically Monday or Tuesday after the previous week ended), as part of session startup:

1. **Read the final daily file** from the previous week (usually the last day worked, often Sunday or Friday)
2. **Collect all completed tasks** from that week's `## Completed` section
3. **Add to `weekly-summary.md`** as a new `## Week of [Mon]–[Sun], [Year]` section
4. **Newer weeks appear at the top** (reverse chronological order)
5. **Create today's new daily file** with a fresh `## Completed` section (empty, ready for this week's tasks)

**Format in weekly-summary.md:**
```
## Week of Feb 17–23, 2026

**Completed (7 tasks):**
- [x] 1. Task name (Day of week)
- [x] 2. Task name (Day of week)
...

**Summary:**
- X tasks completed
- Clients: [list]
- Categories: [list]
```

**Result:**
- `weekly-summary.md` is always a current, historical record
- Never archived — stays in root permanently
- Perfect for productivity tracking, month-end reporting, and year-end review

---

## DASHBOARD WORKFLOW

**Reference Files (for consistency):**
- `.claude/dashboard-template.html` — **Master template, source of truth for HTML structure and CSS**
- `.claude/dashboard-design-spec.md` — Complete design specification (colors, typography, spacing)
- `.claude/dashboard-generation-guide.md` — **Step-by-step generation checklist & consistency verification**
- `dashboard-YYYY-MM-DD.html` (root) — Generated dashboard files (created fresh for each date)

### When to Regenerate

**Only when explicitly requested by the user.**

The dashboard does NOT automatically regenerate when tasks are completed, added, or changed. You must wait for the user to type `report` or specifically ask for the dashboard to be generated. This keeps the workflow efficient and gives you full control over when the dashboard is updated.

### How to Generate (with Consistency Checks)

**The process is simple: Copy the template structure, replace placeholders with data only.**

**Read the guide first:** `.claude/dashboard-generation-guide.md` contains a complete step-by-step process.

**Quick reference:**
1. Read current daily `.md` file to get all task statuses and counts
2. Read `.claude/dashboard-template.html` — this is the EXACT structure you must follow (do NOT deviate, do NOT simplify)
3. Reference `.claude/dashboard-design-spec.md` for all colors, fonts, spacing, and structure notes
4. Count tasks by category: Priority, This Week, Build, Admin, Done This Week
5. Copy the entire template HTML as your starting point
6. Replace only the `[PLACEHOLDER]` values with actual data from the daily file:
   - `[N]` → task counts
   - `[CLIENT NAME]` → actual client names
   - `[TASK NUMBER]` → actual task number
   - `[TASK NAME]` → actual task description
   - `[EMOJI]` → client emoji icon
   - `[COLOR]` → color theme (red, amber, blue, green, purple)
   - `[pending|inprogress|done]` → task status
   - `[CONTEXT]` → task details/subtask
7. Do NOT change CSS, structure, or layout — only replace data placeholders
8. Run through the **Verification Checklist** in the generation guide
9. Add version comment: `<!-- Dashboard v1.0 | Generated [DATE] -->`
10. Save as `dashboard-YYYY-MM-DD.html` in root
11. Open in browser to verify

### Styling Standards (NEVER CHANGE)
- **Theme:** Light mode — background #e2e8f0, text #0f172a
- **Colors:** All CSS `:root` variables — see `.claude/dashboard-design-spec.md`
- **Typography:** Space Grotesk for headlines, Inter for body — see design-spec for exact sizes
- **Visual separation:** 2px border dividers between sections
- **Section headers:** Uppercase, bold (font-weight: 700)
- **Important:** For consistency guidance and checklist, see `.claude/dashboard-generation-guide.md`

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
