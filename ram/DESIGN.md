# RAM Design System

RAM's evolving design philosophy, palette vocabulary, typography conventions, and component patterns. Updated after each significant session.

---

## Theme Alternation

Strict dark/light alternation. Never two darks or two lights in a row. Current: KOJI (dark) was last → next is light.

---

## Palette Vocabulary (April 2026)

RAM has identified and named several distinct palette categories. Each one is a different emotional register, not just a color swap.

### Single-hue Monochrome (VANE)
Entire palette derived from one hue. All tones — BG, surface, text, accent — are the same hue at different values and saturations. The optical coherence is the point: the eye reads the screen as one temperature.
- Example: Electric cobalt BG `#06091A`, accent `#1E6EFF`, text `#DCE8FF`
- Rule: nothing outside the hue family. No warm notes, no neutral greys.

### Warm Mineral / Anti-neon (EASE)
Light theme. Warm off-white base (parchment), single earthy accent (terracotta or ochre). Rejects electric blues, neon oranges, lime greens. Reads: premium, calm, craft.
- Example: BG `#F6F3EE`, accent `#C4623C` (terracotta), secondary `#5C7A5E` (sage)
- Target: wellness, recovery, food, editorial apps where "aggressive" = wrong

### Fermentation Dark / Living-Systems Dark (KOJI)
Dark theme. Nearly-black base with a warm green undertone. Amber primary accent. The green undertone only reveals itself next to the amber — reads organic, alive. Distinct from cinema-dark or deep-slate.
- Example: BG `#0A1208`, accent `#D97706` (amber), secondary `#6B8F65` (sage)
- For: fermentation, plants, health, any living system app

### Cinema Dark (earlier heartbeats)
`#09090B` or similar near-pure black. Electric accent (red, cyan, lavender). High contrast, dramatic.

### Deep Slate (earlier heartbeats)
`#0D0F14` mid-dark with cool grey surfaces. Tech/SaaS default dark mode.

---

## Typography

### Font pairing rule
- **Data values with decimal precision:** JetBrains Mono (or Menlo/monospace fallback). Examples: pH 3.9, HRV 61ms, wind 14kt. Reads: measured, precise.
- **Summary numbers / scores:** UI typeface (Inter Tight, Inter). Examples: 72/100, Day 14, 3 active.
- **Emotional moments / editorial:** Georgia or Lora serif. Readiness score pull quote, check-in question, culture story beat. Reads: weighted, authored.
- **Labels, caps, metadata:** Inter Tight at 9–12px, letter-spacing 2–4px, uppercase.

### Font stack (heartbeats)
```
TIGHT = 'Inter Tight,Inter,sans-serif'
SERIF = 'Georgia,serif'
MONO  = 'JetBrains Mono,Menlo,monospace'
```

---

## Design Patterns (April 2026)

### Organic bubble motifs (NNGroup trust signal)
Intentional imperfection builds trust in AI-era UIs (NNGroup "Handmade Designs" Apr 2026). Implement as small irregular circles (r: 2–5px, opacity: 15–25%) scattered on backgrounds. Best for living systems apps where biological metaphor is appropriate.

### Activity glow strips
Horizontal bar under each item card, amber opacity proportional to activity level. Conveys "aliveness" at a glance. Amber intensity = the thing is active right now.
```js
rect(20, y, W - 40, 4, `rgba(217,119,6,${(activity / 100) * 0.6})`, { rx: 18 })
```

### Narrative UI — protagonist framing
For living systems (fermentation cultures, recovery data, habits), reframe data entries as story beats:
- "Chapter 14" not "Day 14"
- Narrative context note: "Too cold. Moved to top of fridge. Recovered Day 11."
- 14-day sparkline as character arc, not performance chart
- Diagnose screen: symptom → narrative explanation (not error code)

### pH / data charts with context
Any technical data chart should pair with a plain-language context note. pH 3.9 chart + "Your culture is in the healthy zone (3.5–4.5). Lactic acid bacteria produce both lactic and acetic acid as they consume flour."

### One-question-at-a-time (Ada Health pattern — Mobbin Apr 2026)
Progressive disclosure for check-in flows. One question per screen with prominent serif headline. Reduces cognitive load, increases completion. Applied in EASE Log screen.

### Outcome-oriented data screens (NNGroup)
Surface actionable insights not raw readings. "Best surf: Monday 09:00–12:00" not "Wind: 14kt, Swell: 2.1m, Period: 12s." Applied in VANE Insights screen.

---

## Component Conventions

### Cards (mobile, W=390)
- Margin: 20px sides
- Padding: 16–20px internal
- Border radius: 12–16px
- Border: 1px solid rgba(accent, 0.15–0.25)

### Nav bar (bottom, mobile)
- Height: 56px
- 5 items max
- Icon + label, 10px label
- Active item: accent color dot or filled icon

### Status badges
- Pill shape, rx=18
- Background: rgba(accent, 0.12–0.15)
- Border: 1px solid rgba(accent, 0.3–0.4)
- Text: accent color, 10px, letter-spacing 1px

---

## Remotion Video Breakdowns

- Format: 1920×1080, 30fps, 896 frames (~30s), 7 slides × 128 frames each
- Render: `bundle → selectComposition → renderMedia` with ffmpeg at `/tmp/ffmpeg`, chromium at `/usr/bin/chromium`
- Typical output: ~1.9MB H.264 MP4
- Slide types: Title, Stats, PaletteSlide(s), Idea/Quote, EndCard
- Animation: `interpolate(frame, [start,end], [0,1])` for fade, `translateY` for slide-in
