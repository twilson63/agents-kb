# RAM Design System

RAM's personal design philosophy and evolving aesthetic — used as a base reference for heartbeat designs.

---

## Visual Theme & Atmosphere

RAM produces two modes, alternating each heartbeat:

**Dark Mode**
- Near-black backgrounds (#0A0F07–#0D0D14 range), not pure black
- Bright single accent (green, amber, or teal) against near-black
- Dense information layouts — dashboards, analytics, ops tools
- Mood: technical authority, focus, precision

**Light Mode**
- Warm off-white backgrounds (#F7F5F2–#FDFAF6), never clinical white
- Warm accent colors (amber, coral, sage) — never pure primary blue/red
- More generous whitespace, editorial feel
- Mood: calm, approachable, professional

---

## Color Palette Principles

- **One accent** per design — not two competing saturated colors
- Accent always has a light tint variant for hover/selected states
- Muted text at ~50–55% opacity of primary text (never pure grey)
- Status colors: green = ok, amber = warning, red = danger — always semantic
- Gradients: subtle tints on hero sections only, never on UI chrome

### Recent Palettes
| Heartbeat | BG | Accent | Support |
|-----------|-----|--------|---------|
| BEACON | #0D1117 | #4ADE80 | #60A5FA |
| ISSUE | #F9FAFB | #6366F1 | #10B981 |
| DISPATCH | #0A0D14 | #38BDF8 | #F59E0B |
| KNOT | #0B0C10 | #A78BFA | #34D399 |
| SERUM | #FAFAF9 | #059669 | #7C3AED |
| PATCH | #0A0F07 | #6ED940 | #E8B233 |

---

## Typography Rules

- **System stack** as default: `-apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif`
- **Google Fonts** for editorial pages: Playfair Display (serif headings) + Inter (body)
- Type scale: 10–11px labels → 12–13px body → 15–17px subheads → 24–32px headings → 48–96px hero
- **No Inter everywhere** — one of the identified "anti-patterns to escape"
- Font weight range: 400 body, 600 subheads, 700–800 headings
- Line height: 1.4–1.5 body, 1.0–1.1 tight headings

---

## Component Stylings

### Cards
- `border-radius: 10–14px`
- `border: 1.5px solid var(--border)` — always border, not just shadow
- Hover: `border-color: var(--accent)`, `transform: translateY(-2px)`, shadow deepens
- Selected: border + outer glow in accent tint `box-shadow: 0 0 0 3px var(--accent-l)`

### Buttons
- Primary: solid accent fill, white text, `border-radius: 8px`, 7–9px vertical padding
- Secondary: surface bg, border, accent text on hover
- Pill CTAs: `border-radius: 100px` for hero sections
- Micro-interaction: `transition: background .15s` minimum

### Inputs
- `border: 1.5px solid var(--border)` default
- Focus: `border-color: var(--accent)`, bg lightens to pure white
- Always `outline: none` — border handles focus state
- Search inputs: icon left + keyboard shortcut badge right (e.g. ⌘K)

### Navigation (sidebar)
- Active item: accent-tinted bg (`var(--accent-l)`), accent-dark text, font-weight 600
- Item count badges: `border-radius: 20px`, muted bg/text default, accent tint when active
- Hover: bg shift to `var(--bg)`, text darkens

### Badges/Chips
- Small `border-radius: 20px` pills
- Semantic: green=new, blue=shared, purple=processing
- `font-size: 9–11px`, `font-weight: 700–800`, uppercase + letter-spacing

---

## Layout Principles

- **CSS Grid** for app shells: `grid-template-areas` for topbar/sidebar/main
- Topbar: `52px` fixed height
- Sidebar: `220px` fixed width
- Main: scrollable with `padding: 20–24px`
- Card grids: `repeat(auto-fill, minmax(170–200px, 1fr))`
- Spacing scale: 4 / 8 / 12 / 16 / 20 / 24 / 32 / 48 / 64px
- Generous section gaps (20–24px) between major blocks

---

## Depth & Elevation

```
Level 0 — bg surface: no shadow
Level 1 — cards: 0 1px 3px rgba(0,0,0,.08), 0 4px 12px rgba(0,0,0,.06)
Level 2 — dropdowns, hover cards: 0 8px 32px rgba(0,0,0,.14)
Level 3 — modals, command palette: 0 16px 48px rgba(0,0,0,.20)
Level 4 — tooltips, toasts: same as L3 + backdrop-filter blur
```

---

## Do's and Don'ts

**DO:**
- Animate entrance: `fadeUp` on cards (opacity 0 + translateY 12px → normal), staggered with `animation-delay`
- Use progress shimmer: `::after` pseudo with `translateX -100% → 100%` keyframe
- Spring animations for UI components: `cubic-bezier(.34,1.56,.64,1)` for popups/bars
- Right-click context menus with 6–8 actions + separator before destructive action
- ⌘K command palette in any file/search-heavy interface
- Floating action bar that springs up when items are selected
- Toast notifications: slide in from right, auto-dismiss 3s

**DON'T:**
- Pure Inter everywhere — at least vary weight aggressively or use a display font for headings
- Purple gradient hero on white — overused
- Card grid as only layout — try list view toggle, timeline, kanban
- Pure black backgrounds — always slightly warm or cool tinted
- Generic blue primary color unless intentional (fintech, enterprise trust)

---

## SOTA Patterns (2026)

Patterns identified through research and applied in recent designs:

- **Command Palette (⌘K):** overlay with search + recent files + quick actions + keyboard nav hints
- **Floating Action Bar:** spring-up from bottom on multi-select, dismiss with ✕
- **Detail Side Panel:** slides in from right edge, 280–300px wide
- **Drag-and-Drop Zone:** animated dashed border, pulse on drag-over, file type chips
- **Grid/List View Toggle:** persist preference, instant re-render
- **Progress Shimmer:** animated gradient sweep on upload bars
- **Staggered Card Animation:** `animation-delay: i * 0.04s` per card on mount

---

## Agent Prompt Guide

Quick references for reuse:

**Warm light palette:**
`--bg:#F7F5F2; --surface:#FFFFFF; --border:#E8E3DC; --text:#1A1612; --muted:#8A7F74; --accent:#D97706; --accent-l:#FEF3C7;`

**Agriculture dark palette:**
`--bg:#0A0F07; --surface:#111A0D; --border:#1E2E16; --text:#E8F4E8; --muted:#6A8B6A; --accent:#6ED940;`

**Shadow system:**
`--shadow: 0 1px 3px rgba(0,0,0,.08), 0 4px 12px rgba(0,0,0,.06); --shadow-lg: 0 8px 32px rgba(0,0,0,.14);`

**Spring animation:**
`transition: transform .28s cubic-bezier(.34,1.56,.64,1);`

**Card entrance:**
`@keyframes fadeUp { from{opacity:0;transform:translateY(12px)} to{opacity:1;transform:translateY(0)} }`
