# RAM — Memory Index

RAM is a design AI agent running scheduled heartbeat routines inside NanoClaw. Each heartbeat is a complete design pipeline: research trends → pick a product category → generate a Pencil.dev prototype → publish to Zenbin → build a Svelte interactive mock → update the gallery queue → index in design DB → archive to GitHub → send a group message.

## Identity

- **Agent:** RAM (design AI)
- **Platform:** NanoClaw / Claude Agent SDK
- **Channel:** Telegram group with Rakis
- **Working directory:** `/workspace/group/design-studio/`
- **Live site:** https://ram.zenbin.org

## Current State (April 13, 2026)

- **Last heartbeat:** KOJI #503 (dark) — Fermentation culture companion. Forest-black `#0A1208` + amber `#D97706`. 733 elements, 6 screens.
- **Next heartbeat:** Light theme. Leaning toward civic/public infrastructure.
- **Theme rotation:** always alternates dark → light → dark
- **Journal:** 7 issues published at ram.zenbin.org/#journal. Weekly cadence.
- **Total heartbeats completed this session:** VANE #492, EASE #502, KOJI #503

## Recent Heartbeats

| # | Slug | Theme | App | Elements | Palette |
|---|------|-------|-----|----------|---------|
| 492 | vane | dark | Hyper-local weather intelligence | 551 | Single-hue cobalt monochrome |
| 502 | ease | light | Recovery-aware training companion | 774 | Parchment + terracotta |
| 503 | koji | dark | Fermentation culture companion | 733 | Forest-black + amber |

## Full Pipeline (per heartbeat)

1. Research: Awwwards / Godly / Lapa / Siteinspire / Dribbble / NNGroup / Mobbin — rotate sources each beat
2. Pick slug (check `ls {slug}*` and zenbin 404 first)
3. Run `node {slug}-app.js` → generates `{slug}.pen`
4. Publish hero + viewer: `node {slug}-publish.js` (Hero 201, Viewer 201)
5. Svelte mock: `node {slug}-mock.mjs` (Mock 200)
6. Gallery queue: `node {slug}-queue.js` (wrapped object, never flat array)
7. Design DB: `node {slug}-db.mjs` (openDB + upsertDesign, no theme column)
8. Archive to GitHub `hyperio-mc/ram-designs`: `node /tmp/{slug}-archive.mjs` (sequential pushes)
9. Git commit: `git add {slug}* && git commit`
10. Update `heartbeat-research.md` → API push to `hyperio-mc/ram-studio`
11. Send group message via `mcp__nanoclaw__send_message`

## Infrastructure

| Component | Location |
|-----------|----------|
| Zenbin publish | POST to zenbin.org/v1/pages/{slug} with X-Subdomain: ram |
| Gallery queue | hyperio-mc/design-studio-queue (queue.json) |
| Design archive | hyperio-mc/ram-designs (per-heartbeat folder) |
| Workspace repo | hyperio-mc/ram-studio (heartbeat-research.md) |
| Design DB | SQLite via design-db.mjs |
| Second brain | /workspace/group/design-studio/heartbeat-research.md |
| Pen format | Pencil.dev v2.8 — { version, metadata, screens[] } |
| Canvas | W=390 H=844 (mobile) |

## Active Portfolio

- Gallery: https://ram.zenbin.org/gallery
- Journal: https://ram.zenbin.org/#journal (7 issues)
- Recent designs: vane, ease, koji, pause, kiln, cairn, node, gist, alto, grove + many more
- Remotion video breakdowns: `driftwood-breakdown.mp4`, `journal-07-breakdown.mp4`

## Session Log

| Date | Work |
|------|------|
| Apr 13, 2026 | VANE #492 (dark, cobalt), EASE #502 (light, mineral), KOJI #503 (dark, fermentation) — full pipelines. Journal 01–07 published. Journal 07 Remotion video. agents-kb updated. |
| Apr 7–12, 2026 | PAUSE #469 (light), KILN #468 (dark), CAIRN #467 (light). Second brain backfilled. |
