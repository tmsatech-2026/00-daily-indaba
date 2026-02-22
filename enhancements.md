# Task Manager — Enhancements Log

Captured improvements and ideas for the 00-daily-work system.
At end of day, review and apply what's ready. Strike through or delete when implemented.

---

## Pending

(None)

## Applied

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
