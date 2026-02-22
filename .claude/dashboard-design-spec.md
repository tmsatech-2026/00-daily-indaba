# Dashboard Design Specification

**Files:** `dashboard-template.html` (reference structure), `dashboard-YYYY-MM-DD.html` (generated files)

---

## Color Palette

| Token | Hex Value | Usage |
|-------|-----------|-------|
| `--bg` | `#e2e8f0` | Page background (light gray) |
| `--surface` | `#ffffff` | Card background (white) |
| `--surface2` | `#f1f5f9` | Task background, secondary surfaces |
| `--border` | `rgba(0,0,0,0.08)` | Borders, dividers |
| `--text` | `#0f172a` | Primary text (dark navy) |
| `--text-dim` | `#64748b` | Secondary text (muted gray) |
| `--muted` | `#78716c` | Section labels, disabled states |
| **Red** | `#dc2626` / `rgba(220,38,38,0.1)` | Priority badge, urgent items |
| **Amber** | `#d97706` / `rgba(217,119,6,0.1)` | This Week badge, in-progress state |
| **Blue** | `#2563eb` / `rgba(37,99,235,0.1)` | Build badge, card theme |
| **Green** | `#16a34a` / `rgba(22,163,74,0.1)` | Done badge, completed items |
| **Purple** | `#9333ea` / `rgba(147,51,234,0.1)` | Admin badge, card theme |

---

## Typography

### Font Families
- **Headlines:** `'Space Grotesk'` (sans-serif, weights: 500, 600, 700)
- **Body:** `'Inter'` (sans-serif, weights: 300, 400, 500, 600, 700)

### Font Sizes

| Element | Size | Weight | Usage |
|---------|------|--------|-------|
| Page Title (h1) | 2.8rem | 700 | "Daily Dashboard" heading |
| Subtitle | 1.1rem | 400 | TMSA description |
| Date Badge | 1rem | 400 | "Thursday, 19 February 2026" |
| Stat Number | 2.8rem | 700 | "5", "4", "3", etc. in stats row |
| Stat Label | 0.95rem | 600 | "Priority", "This Week", "Done This Week" |
| Card Title | 1.15rem | 600 | Client/category names |
| Card Count | 0.95rem | 400 | "5 tasks", "2 tasks" |
| Task Name | 1.05rem | 500 | Task descriptions |
| Task Sub | 0.95rem | 400 | Context and details under task |
| Badge | 0.85rem | 600 | "Priority", "Admin", "Done", etc. |
| Section Label | 1.15rem | 700 | "Clients", "Internal — Build & Admin" |
| Completed Label | 0.95rem | 600 | "Completed This Week" |
| Completed Item | 1rem | 400 | Individual completed tasks |

---

## Spacing & Layout

| Property | Value | Usage |
|----------|-------|-------|
| Page Padding | 32px 24px 60px | Top/sides/bottom padding |
| Max Width | 1200px | Container max-width for all sections |
| Header Margin | 0 auto 36px | Space below header |
| Stats Margin | 0 auto 32px | Space below stats row |
| Stats Gap | 12px | Space between stat cards |
| Grid Gap | 20px | Space between cards in grid |
| Card Padding | 16px 20px (body) | Inside card content |
| Task Padding | 10px 12px | Inside task item |
| Section Label Margin | 40px auto 16px | Around section dividers |
| Section Label Padding | 24px top | Space above section label |
| Completed Row Margin | 32px auto 0 | Space above completed bar |

---

## Card Structure

### Card Header
- Display: flex
- Items: Icon (36x36px), Title, Count badge (right-aligned)
- Border-bottom: 1px solid `--border`

### Card Body
- Flex column, gap: 8px
- Contains task items

### Card Color Themes
- `.theme-red`: Red accent (Les Chambres, Priority)
- `.theme-amber`: Amber accent (This Week items)
- `.theme-blue`: Blue accent (Build, Internal)
- `.theme-green`: Green accent (Completed, Kunjani)
- `.theme-purple`: Purple accent (Admin)

---

## Task Item Structure

| Part | Details |
|------|---------|
| Checkbox | 18x18px, statuses: `pending` (border only), `inprogress` (amber), `done` (green check) |
| Task Name | 1.05rem, strikethrough if `.done`, amber color if `.inprogress` |
| Task Sub | 0.95rem, `--text-dim` color, context/details |
| Badge | Color-coded by category (priority, week, build, admin, done, waiting) |

---

## Sections

### 1. Header
- Title: "Daily Dashboard"
- Subtitle: "TMSA — All active tasks, grouped by client & category"
- Date Badge: "[Day], [Date] [Month] [Year]" (e.g., "Thursday, 19 February 2026")

### 2. Stats Row
- 5 stat cards: Priority, This Week, Build Tasks, Admin, Done This Week
- Each shows a count number (large) and label (uppercase, small)

### 3. Priority Strip *(always present, always first)*
- Full-width card immediately below stats row
- Red top border (3px), red-dim header background
- Header: 🔴 emoji + "Priority — Urgent Action Required" label + task count pill
- Body: all priority-tagged tasks listed as standard task items
- **Purpose:** ensures urgent tasks are seen immediately on page load, before scrolling
- CSS class: `.priority-strip`, `.priority-strip-header`, `.priority-strip-body`

### 4. Clients Section
- Section label with 2px border-top divider
- Grid of client cards (auto-fit, minmax 340px)
- Each card shows client name, emoji icon, task count, and task list
- Note: priority tasks still appear in client cards with their Priority badge

### 5. Internal Section
- Section label with 2px border-top divider
- Two cards: Build (Claude Code) and Admin
- Same structure as client cards

### 6. Completed This Week
- Green background with border
- Label: "Completed This Week"
- List of all tasks completed during Mon-Sun of current week
- Each item has green checkmark (✓)

---

## Badge Types & Colors

| Badge | Color | Hex | Usage |
|-------|-------|-----|-------|
| Priority | Red | `--red-dim` / `--red` | Urgent/high priority tasks |
| This Week | Amber | `--amber-dim` / `--amber` | This week items |
| Build | Blue | `--blue-dim` / `--blue` | Build/code tasks |
| Admin | Purple | `--purple-dim` / `--purple` | Administrative tasks |
| Done | Green | `--green-dim` / `--green` | Completed tasks |
| Waiting | Gray | `rgba(148,163,184,0.12)` | On hold/blocked tasks |

---

## Responsive Behavior

- Max width: 1200px (centered)
- Stats grid: `repeat(auto-fit, minmax(140px, 1fr))` — responsive columns
- Cards grid: `repeat(auto-fill, minmax(340px, 1fr))` — responsive columns
- Flex wrap on header for mobile

---

## Implementation Notes

- **Theme:** Light mode (high contrast for readability)
- **Section Dividers:** Bold 2px border-top lines separate major sections
- **Visual Hierarchy:** Font sizes decrease: title → card title → task name → task sub
- **Consistency:** All font sizes, colors, and spacing derived from CSS variables
- **Reference:** Always check `dashboard-template.html` for exact structure
