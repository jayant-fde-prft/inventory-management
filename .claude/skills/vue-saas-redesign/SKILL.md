---
name: vue-saas-redesign
description: Guidelines for a modern SaaS-style layout in this Vue 3 app — fixed left sidebar navigation instead of a top nav bar. Use this skill when redesigning navigation/layout or adding a new top-level view.
---

# Vue SaaS Sidebar Layout

## What "SaaS layout" means here

A fixed-width left sidebar (~240px, always expanded, no collapse toggle) replaces the horizontal top nav. Nav items are icon + label, using inline SVGs only — no icon library dependency. Everything else (cards, tables, badges, colors) stays whatever this app already uses; this skill is scoped to the nav shell, not a full design-system rewrite.

## Shell pattern

```html
<div class="app-shell">
  <Sidebar />
  <div class="app-body">
    <FilterBar />
    <main class="main-content"><router-view /></main>
  </div>
</div>
```

```css
.app-shell { display: flex; min-height: 100vh; }
.app-sidebar { position: fixed; left: 0; top: 0; width: 240px; height: 100vh; }
.app-body { flex: 1; margin-left: 240px; display: flex; flex-direction: column; min-height: 100vh; }
```

Sidebar nav items: `router-link` + inline SVG (18-20px, `stroke="currentColor"`, `stroke-width="1.5"`) + `t('nav.*')` label. Active route reuses the existing accent blue (`#2563eb` text / `#eff6ff` background).

## Dropdown flyout direction

Any menu (profile, language switcher, etc.) that lives in the sidebar footer must anchor its dropdown with `left: 0; right: auto`, not `right: 0` — a 240px column can't fit a wider dropdown anchored to its own right edge without it overflowing off the sidebar. Let it flyout rightward over the main content instead, and make sure no ancestor container clips with `overflow: hidden`.

## Reminder

Per this repo's `CLAUDE.md`, any `.vue` file creation or significant modification must go through the **vue-expert** subagent.
