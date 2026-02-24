# Task Manager — Enhancements Log

Captured improvements and ideas for the 00-daily-work system.
At end of day, review and apply what's ready. Strike through or delete when implemented.

---

## Pending

(None)

## Applied

- [x] **Clickable links in dashboard** — All web URLs and markdown links in task descriptions auto-convert to clickable HTML links with target="_blank". Web URLs only: markdown links `[text](url)` with web addresses, bare URLs (http://, https://), and www. links. Local file paths (e.g., client-refs/...) are ignored. JavaScript linkifyText() function added to template and applied on page load (2026-02-24)
- [x] **Dynamic date badge** — dashboard date pulls from JS clock, no hardcoding (2026-02-20)
- [x] **Sequential task numbering** — tasks numbered 1–N, say "[N] done" to check off (2026-02-20)
- [x] **One-word shortcuts** — full list documented in `CLAUDE.md` (2026-02-20)
- [x] **Shortcuts auto-display at session start** — SESSION START protocol updated to display shortcuts table (2026-02-20)
- [x] **`shorts` shortcut** — shows full shortcuts list on demand (2026-02-20)
- [x] **`update` shortcut** — mid-session state preservation command (2026-02-20)
- [x] **Shortcut renames** — `focus` → `today`, `push` → `git` (2026-02-20)
- [x] **Shortcuts table sorted by priority** — most-used first, end-of-day last (2026-02-20)
- [x] **`end` shortcut** — full 7-step close-out sequence: verify statuses → carry-forward note → session log → update docs → regenerate dashboard → git push → tomorrow brief (2026-02-20)
- [x] **Priority strip** — full-width red-accented section above client cards showing all priority tasks at first glance; added to dashboard-template.html, dashboard-design-spec.md, and CLAUDE.md dashboard workflow (2026-02-20)
- [x] **Archive folder** — previous day's `.md` and `dashboard-*.html` moved to `archive/` when new daily file is created; keeps root clean; workflow documented in CLAUDE.md (2026-02-21)
- [x] **Weekly summary workflow** — `weekly-summary.md` maintains persistent archive of weekly completions; completed tasks now carried forward in daily files with dates, reset on Monday of new week; update weekly-summary at start of each new week during session startup; prevents context loss and creates historical record for productivity tracking (2026-02-21)
- [x] **`new` shortcut — fast task capture with confirmation** — Type `new` + description/image → I extract and summarize ALL tasks → ask for confirmation before adding. MANDATORY confirmation step prevents missed tasks. Supports single or multiple tasks (2026-02-21)
- [x] **Dashboard generation workflow clarified** — Dashboard now regenerates ONLY on explicit user request (`report` shortcut or direct request). No automatic regeneration on task changes, completions, or additions. Updated CLAUDE.md and dashboard-generation-guide.md to reflect manual-only workflow (2026-02-21)
- [x] **Shortcuts reference section added to dashboard** — Bottom of dashboard now includes two-column grid with all shortcuts (name + brief description). Matches CLAUDE.md shortcuts list. Added to dashboard-template.html so all future dashboards include this reference (2026-02-22)
- [x] **Split completed sections: This Week + Last Week** — Dashboard now shows two completed banners: "Completed This Week" (green, current Mon–Sun) and "Completed Last Week" (muted/gray, previous Mon–Sun). Stats row expanded to 6 cards with separate "Done Last Week" and "Done This Week" counts. Week boundary is Monday–Sunday. Updated: dashboard-template.html, dashboard-design-spec.md, dashboard-generation-guide.md, CLAUDE.md (2026-02-23)
- [x] **Dashboard template: Fixed missing "Done Last Week" stat card** — Template was missing the 5th stat card (Done Last Week) in the stats row. Added as muted/gray colored stat card between Admin and Done This Week. Template now has all 6 stat cards as specified in design-spec. Updated: dashboard-template.html (2026-02-24)
- [x] **Session startup: Auto-date check and archiving** — SESSION START now includes: (1) Check today's date, (2) Verify YYYY-MM-DD.md exists for today, (3) If new day: archive previous day's .md and dashboard-*.html files to archive/ folder, (4) Create new daily file if needed. Keeps root clean and prevents working on old files. Updated: CLAUDE.md, MEMORY.md (2026-02-24)
- [x] **Task description formatting standards formalized** — All task descriptions now follow consistent rules: max 4 lines, human-readable language, no technical jargon, no local file paths (use web URLs only), regular hyphens only. Standards documented in CLAUDE.md (new "TASK DESCRIPTION STANDARDS" section), dashboard-design-spec.md (formatting rules + examples), and dashboard-generation-guide.md (Step 2 + Step 4 verification checklist). Applied to all tasks in 2026-02-24.md. Future dashboards will validate against these standards. Updated: CLAUDE.md, dashboard-design-spec.md, dashboard-generation-guide.md (2026-02-24)
