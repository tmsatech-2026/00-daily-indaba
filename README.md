# 00-Daily-Work Dashboard

**A light-themed, externally-shareable daily task dashboard for TMSA.**

This repository contains the daily work dashboard system used by Tourism Marketing SA (TMSA) for task management and client communication.

---

## 🎯 Quick Links

**View the latest dashboard:**
https://tmsatech-2026.github.io/00-daily-work/dashboard-2026-02-19.html

(Replace the date in the URL to view dashboards from other days)

---

## 📁 What's in This Repo

### Dashboard Files
- **`dashboard-YYYY-MM-DD.html`** — Generated dashboards (one per date)
  - Light theme for readability
  - Displays all active tasks grouped by client and category
  - Tracks completed tasks by week (Monday–Sunday)
  - Ready to share externally via GitHub Pages

### Reference & Documentation
- **`dashboard-template.html`** — Master template with exact HTML structure and CSS
  - Use this to understand the dashboard layout
  - All styling is embedded (colors, fonts, spacing)

- **`dashboard-design-spec.md`** — Complete design specification
  - Color palette, typography scale, spacing rules
  - Component styles (cards, badges, tasks)
  - Responsive layout guidelines

- **`CLAUDE.md`** — Complete workflow documentation
  - Dashboard generation process
  - File structure and naming conventions
  - GitHub Pages setup
  - External sharing workflow

### Configuration
- **`.claude/`** — Configuration directory
  - `dashboard-design-spec.md` — Quick reference copy
  - `tmsa-business-context.md` — TMSA company and client context
  - `settings.local.json` — Local Claude Code settings

### Daily Files
- **`2026-02-19.md`** (and other dated files)
  - Complete daily task records
  - Session logs with timestamps (SAST/UTC+2)
  - Completed tasks, notes, and carry-forwards

---

## 🚀 Viewing Dashboards

Each dashboard is automatically published to GitHub Pages.

**Format:**
```
https://tmsatech-2026.github.io/00-daily-work/dashboard-YYYY-MM-DD.html
```

**Examples:**
- 19 Feb 2026: https://tmsatech-2026.github.io/00-daily-work/dashboard-2026-02-19.html
- 20 Feb 2026: https://tmsatech-2026.github.io/00-daily-work/dashboard-2026-02-20.html

---

## 📊 Dashboard Features

### Layout
- **Header** — Project title, date, and week overview
- **Stats Row** — Quick count of Priority, This Week, Build, Admin, and Done tasks
- **Clients Section** — Tasks grouped by client with task details and context
- **Internal Section** — Build (Claude Code) and Admin tasks
- **Completed Bar** — All tasks completed during the week (Monday–Sunday)

### Styling
- **Light theme** — Soft gray background (#e2e8f0), dark navy text (#0f172a)
- **Readable typography** — Space Grotesk headlines, Inter body text
- **Color-coded badges** — Priority (red), This Week (amber), Build (blue), Admin (purple), Done (green)
- **Clean spacing** — Generous padding, clear visual hierarchy

---

## 📝 How to Share a Dashboard

1. **Generate** a new dashboard from the daily task file
2. **Commit & push** to this repo:
   ```bash
   git add dashboard-YYYY-MM-DD.html
   git commit -m "Update dashboard for YYYY-MM-DD"
   git push origin main
   ```
3. **Share the link** with stakeholders:
   ```
   https://tmsatech-2026.github.io/00-daily-work/dashboard-YYYY-MM-DD.html
   ```
4. **Dashboard goes live** within seconds — no additional setup needed

---

## 🔧 Technical Details

- **Technology:** Static HTML + CSS (no JavaScript required)
- **Browser support:** All modern browsers (Chrome, Firefox, Safari, Edge)
- **Hosting:** GitHub Pages (deployed from `main` branch, root folder)
- **Updates:** Changes publish within seconds of push

---

## 📚 Documentation

For detailed workflow documentation, see **`CLAUDE.md`**, which includes:
- Dashboard generation process
- Styling standards and design tokens
- "Completed This Week" format
- GitHub Pages setup and sharing workflow
- Session start/end procedures

---

## 👥 For External Recipients

If someone shares a dashboard link with you:
1. Click the link to view the latest dashboard
2. No login or account required
3. Dashboard is read-only (view only)
4. All information is current as of the last update

---

## 📅 Dashboard Naming Convention

Dashboards follow a strict naming convention for consistency:

```
dashboard-YYYY-MM-DD.html
```

- **YYYY** = Year (e.g., 2026)
- **MM** = Month (01–12)
- **DD** = Day (01–31)

Example: `dashboard-2026-02-19.html` = 19 February 2026

---

## 📞 Questions?

For questions about the dashboard system or workflow, refer to:
- **`CLAUDE.md`** — Complete workflow and standards
- **`.claude/dashboard-design-spec.md`** — Design details
- **`.claude/tmsa-business-context.md`** — Company context

---

**Last Updated:** 19 February 2026
**Maintained by:** TMSA
