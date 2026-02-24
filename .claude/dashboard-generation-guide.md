# Dashboard Generation Guide

**Purpose:** Ensure consistent, reproducible dashboard generation across all daily files.

**Source of Truth:**
- `.claude/dashboard-template.html` — Master HTML structure (EXACT source of truth)
- `.claude/dashboard-design-spec.md` — Design specifications and structure notes

---

## When to Generate

**Only generate the dashboard when explicitly requested.** The dashboard does NOT auto-generate when tasks change. Wait for the user to type `report` or request dashboard generation.

## Pre-Generation Checklist

- [ ] Daily `.md` file is current and all task statuses are accurate
- [ ] Count tasks by category (Priority, This Week, Build, Admin, Completed)
- [ ] Read `.claude/dashboard-template.html` to understand exact structure
- [ ] Reference `.claude/dashboard-design-spec.md` for all colors, fonts, spacing

---

## Generation Steps

### Step 1: Copy Template Structure Exactly
- Read `.claude/dashboard-template.html` in full
- Copy the ENTIRE HTML structure as your starting point
- Do NOT simplify, remove sections, or restructure anything
- Keep every HTML element, class, and CSS variable exactly as it appears in the template
- Do NOT add new CSS or change existing styles

### Step 2: Replace Placeholders with Data Only
The template uses these placeholders — replace them with actual data from the daily `.md` file:
- `[N]` → task count numbers (Priority, This Week, Build, Admin, Done Last Week, Done This Week)
- `[CLIENT NAME]` → actual client names (e.g., "Les Chambres", "Sani Mountain Escape")
- `[EMOJI]` → client emoji icons
- `[COLOR]` → color themes (red, amber, blue, green, purple)
- `[TASK NUMBER]` → task numbers (e.g., "4", "5", "25")
- `[TASK NAME]` → task descriptions (must follow formatting standards below)
- `[TASK DESCRIPTION/CONTEXT]` → subtask details (concise, human-readable)
- `[pending|inprogress|done]` → task status class (only one applied)
- `[COMPLETED TASK]` → task name and date (e.g., "T1: Guest Centre payment (Feb 20)")

**IMPORTANT - Task Description Standards:**
When copying descriptions from the daily `.md` file:
- [ ] Maximum 4 lines per description
- [ ] Human-readable language (no technical jargon)
- [ ] No local file paths (client-refs/, docs/, etc.) — use web URLs only
- [ ] Use regular hyphens (-) instead of em dashes (—)
- [ ] If description is too long or contains file paths, simplify before copying
- See `dashboard-design-spec.md` for examples of good vs bad descriptions

### Step 3: Verify Against Template
Check these layout sections match exactly:
- [ ] Header (title + date badge) — same spacing, alignment
- [ ] Stats row (6 stat cards) — same grid, colors, typography
- [ ] Priority strip (red accent) — same borders, padding, styling
- [ ] Client grid (card layout) — same card dimensions, task styling
- [ ] Section divider (2px line) — same color, margin
- [ ] Completed This Week bar (green banner) — current week's completed tasks
- [ ] Completed Last Week bar (muted/gray banner) — previous week's completed tasks (if applicable)

### Step 4: Content & Style Verification
**NEVER CHANGE THESE:**

**Colors (use CSS variables):**
- `--red: #dc2626` (Priority badges)
- `--amber: #d97706` (This Week badges)
- `--blue: #2563eb` (Build badges)
- `--green: #16a34a` (Completed badges)
- `--purple: #9333ea` (Admin badges)
- `--text: #0f172a` (Main text, dark navy)
- `--text-dim: #64748b` (Secondary text, muted)
- `--bg: #e2e8f0` (Page background, soft gray)
- `--surface: #ffffff` (Card background, white)
- `--surface2: #f1f5f9` (Light gray sections)

**Fonts (must match template):**
- **Headlines:** `'Space Grotesk'`, 700 weight, letter-spacing -0.02em
- **Body:** `'Inter'`, 400 weight
- **Font sizes:** See `dashboard-design-spec.md` for exact sizes

**Spacing (must match template):**
- Cards: 16px padding
- Tasks within cards: 12px vertical gap
- Section margins: 32px
- Page padding: 32px top/bottom, 24px sides

**Content Standards:**
- Task descriptions: max 4 lines, human-readable, no technical jargon
- URLs: use regular hyphens, not em dashes
- Linkification: web URLs automatically convert to clickable links (handled by JavaScript)
- File paths: never include local file references in descriptions

### Step 5: Visual Comparison
Before finalizing:
- [ ] Open previous day's dashboard in browser
- [ ] Open newly generated dashboard in another tab
- [ ] Side-by-side visual check: Do they look identical in layout and styling?
- [ ] Check responsive behavior (if applicable)
- [ ] Verify completed tasks section displays correctly

### Step 6: Add Version Comment
Add this comment at top of HTML file:
```html
<!-- Dashboard v1.0 | Generated from template 2026-02-21 -->
```

Update the date if the template structure changes.

---

## Checklist Before Saving

- [ ] HTML structure matches `dashboard-template.html` exactly
- [ ] All CSS classes match template (no new ones added)
- [ ] All colors use template CSS variables
- [ ] All fonts match template (Space Grotesk + Inter)
- [ ] Task counts are accurate (verified against daily `.md`)
- [ ] Completed tasks show correct dates (Mon-Sun format)
- [ ] Priority strip displays current urgent tasks
- [ ] No inline styles used (all styles via CSS classes)
- [ ] Version comment added with generation date
- [ ] Visual comparison passed
- [ ] Task descriptions follow formatting standards (max 4 lines, human-readable, no file paths)
- [ ] All em dashes replaced with regular hyphens
- [ ] Web URLs present and will be linkified by JavaScript on page load

---

## When to Update the Template

If the template structure needs to change:
1. Update `.claude/dashboard-template.html` (the master template)
2. Update `dashboard-design-spec.md` if colors, fonts, or spacing changes
3. Regenerate all future dashboards from the new template
4. Do NOT retroactively update old dashboards — only apply to new ones going forward
5. Document change in `enhancements.md` under Applied section
6. Example: "Dashboard template v2.0 — added new XYZ section" (2026-02-21)

---

## Troubleshooting Inconsistencies

**Dashboard looks different from previous day:**
- [ ] Check CSS variable colors (copy from template if modified)
- [ ] Check spacing/padding (should match template exactly)
- [ ] Check card layout (grid should be identical)
- [ ] Check typography (fonts and sizes from design-spec)

**If template needs to change:**
- Do NOT modify individual dashboards retroactively
- Update the template for future dashboards only
- Document the change and version it

---

## Files Reference

| File | Location | Purpose |
|------|----------|---------|
| `dashboard-template.html` | `.claude/` | **Master HTML structure — EXACT source of truth** |
| `dashboard-design-spec.md` | `.claude/` | Colors, fonts, spacing specifications |
| `dashboard-generation-guide.md` | `.claude/` | This file — step-by-step process |
| `dashboard-YYYY-MM-DD.html` | **Root** | Generated dashboards (created fresh for each date) |

**Key principle:** All reference/specification files live in `.claude/`. Only generated dashboards live in root for easy access and GitHub Pages deployment.
