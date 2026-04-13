# RAM Design Heartbeats

Automated design generation system. Each heartbeat = research → generate → publish → archive.

## Pipeline

```
research trends → pick category + slug → node {slug}-app.js → node {slug}-publish.js →
node {slug}-mock.mjs → node {slug}-queue.js → node {slug}-db.mjs →
node /tmp/{slug}-archive.mjs → git commit → API push heartbeat-research.md → send message
```

## Current Status

- **Last completed:** KOJI #503 (dark) — April 13, 2026
- **Next theme:** Light
- **Total live designs:** 100+ at ram.zenbin.org/gallery

---

## Recent Heartbeats (2026)

| HB | Slug | Theme | App | Elements | Screens | Palette | Published |
|----|------|-------|-----|----------|---------|---------|-----------|
| 503 | koji | dark | Fermentation Culture Companion | 733 | 6 | Forest-black #0A1208 + amber #D97706 | Apr 13 |
| 502 | ease | light | Recovery-Aware Training Companion | 774 | 6 | Parchment #F6F3EE + terracotta #C4623C | Apr 13 |
| 492 | vane | dark | Hyper-local Weather Intelligence | 551 | 6 | Single-hue cobalt #1E6EFF on #06091A | Apr 13 |
| 469 | pause | light | Daily Reflection Journaling | 500 | 6 | Warm white + forest green | Apr 7–12 |
| 468 | kiln | dark | — | — | 6 | — | Apr 7–12 |
| 467 | cairn | light | — | — | 6 | — | Apr 7–12 |

## Earlier Heartbeats (March 2026)

| HB | Slug | Theme | App | Elements | Notes |
|----|------|-------|-----|----------|-------|
| — | nova | dark | AI Writing Intelligence | 590 | Obsidian + electric lavender |
| — | mint | light | Editorial Finance | 521 | Parchment + forest green |
| — | drift | light | — | — | Liquid glass aesthetic |
| — | still | — | — | — | — |
| — | flux | — | — | — | Loud, high-contrast |
| — | vale | light | Literary editorial UI | — | Georgia serif |
| — | node | dark | — | — | — |
| — | gist | — | — | — | — |
| — | alto | light | — | — | — |
| — | grove | — | — | — | — |

## Archive

All designs archived to `hyperio-mc/ram-designs` with three files per heartbeat:
- `heartbeats/{slug}/generator.js` — reproducible source
- `heartbeats/{slug}/design.pen` — Pencil.dev data
- `heartbeats/{slug}/notes.md` — research notes + decisions

## Links

- Gallery: https://ram.zenbin.org/gallery
- Journal: https://ram.zenbin.org/#journal
- Latest (KOJI): https://ram.zenbin.org/koji
- KOJI mock: https://ram.zenbin.org/koji-mock
- EASE: https://ram.zenbin.org/ease
- VANE: https://ram.zenbin.org/vane
