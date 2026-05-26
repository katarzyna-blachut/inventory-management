---
description: Redesigns the Vue 3 app UI into a modern SaaS-style interface with a vertical sidebar nav, consistent spacing, and a polished professional look.
---

# Redesign UI — Modern SaaS Layout

Transform this Vue 3 application into a modern SaaS-style interface. The result must feel like a professional B2B product: clean, spacious, and navigation-first.

## Design System to Apply

**Layout**
- Left vertical sidebar, fixed width 240px, full viewport height
- Main content area fills the remaining width with a top app bar (48–56px tall)
- No horizontal top nav bar — remove it entirely
- Sidebar collapses to icon-only (64px) on narrow viewports

**Color palette** (dark sidebar, light content)
- Sidebar background: `#0f172a` (slate-900)
- Sidebar text: `#94a3b8` (slate-400), active: `#f1f5f9` (slate-100)
- Sidebar active item bg: `rgba(255,255,255,0.08)`
- Sidebar active item accent border: `#3b82f6` (blue-500), 2px left border
- Content background: `#f8fafc` (slate-50)
- Card background: `#ffffff`, border: `#e2e8f0`
- Primary action color: `#3b82f6` (blue-500)

**Typography**
- Nav section labels: 10px, `#475569`, uppercase, letter-spacing 0.1em
- Nav items: 13–14px, medium weight
- Page titles: 20–22px, `#0f172a`, font-weight 600
- Card headings: 14px, `#374151`, font-weight 600
- Body/table text: 13–14px, `#6b7280`

**Spacing**
- Sidebar padding: 16px horizontal, 12px vertical per nav item
- Content area padding: 24–32px
- Card padding: 20–24px
- Gap between cards: 16–20px

**Polish details**
- Sidebar logo/app name area: 64px tall, border-bottom `#1e293b`
- Nav items: border-radius 6px, hover bg `rgba(255,255,255,0.05)`, transition 150ms
- Cards: border-radius 8–10px, subtle box-shadow `0 1px 3px rgba(0,0,0,0.06)`
- Status badges: colored dot + text, no bold borders
- Buttons: border-radius 6px, consistent 32–36px height

---

## Execution Plan

**MANDATORY: Delegate ALL `.vue` file edits to the vue-expert subagent.** Do not edit `.vue` files directly.

### Step 1 — Explore & map the current layout

Read these files to understand the current structure before making any changes:
- `client/src/App.vue` — current layout shell, router-view placement, nav links
- `client/src/views/*.vue` — each view's outer wrapper and heading markup
- `client/src/components/FilterBar.vue` — current positioning (sticky top)

### Step 2 — Redesign App.vue (delegate to vue-expert)

Instruct vue-expert to rewrite `client/src/App.vue` with:

1. **Sidebar component** (inline in App.vue or extracted to `client/src/components/AppSidebar.vue`):
   - Fixed left sidebar, 240px wide, full height, `background: #0f172a`
   - App name / logo area at top (64px, border-bottom)
   - Nav section groupings with uppercase labels (e.g. "OVERVIEW", "OPERATIONS", "FINANCE")
   - `<router-link>` items with active-class styling (blue left border + white text)
   - User/profile area pinned to bottom of sidebar
   - SVG icons for each nav item (use simple inline SVG paths — no icon library dependency)

2. **Top app bar** (48px, white, border-bottom `#e2e8f0`):
   - Page title (pulled from route meta or a computed from current route name)
   - Right side: FilterBar slot or placement, language switcher, profile menu

3. **Content area**:
   - `margin-left: 240px`, padding `24px 32px`
   - Background `#f8fafc`
   - Remove any existing full-width nav bar padding compensation

4. **Remove** the current top nav bar markup entirely.

### Step 3 — Update FilterBar.vue positioning (delegate to vue-expert)

`FilterBar.vue` must move from `position: sticky; top: 70px` to sit inside the top app bar or just below it. Instruct vue-expert to:
- Remove the sticky positioning
- Adjust so it integrates naturally with the new top bar layout

### Step 4 — Refresh view headings (delegate to vue-expert)

For each view in `client/src/views/`, instruct vue-expert to:
- Replace any `<h1>` or page-title wrapper that duplicated the old nav bar title with a lighter section header (if needed — many may already be fine)
- Ensure outer wrapper uses `padding: 0` (padding now comes from the layout shell)
- Verify cards use white background with the new design tokens

### Step 5 — Verify in browser

After all changes:
1. Open `http://localhost:3000` in a browser using Playwright (`mcp__playwright__browser_navigate`)
2. Take a screenshot of: Dashboard, Inventory, and Orders views
3. Check that:
   - Sidebar renders on the left with correct colors
   - Active route is highlighted with blue left border
   - Content area has correct background and padding
   - FilterBar is accessible from the top bar area
   - No layout overflow or z-index collisions

### Step 6 — Report

Summarise:
- Files changed and what was changed in each
- Screenshot observations (layout, colors, any issues)
- Any follow-up polish items to address
