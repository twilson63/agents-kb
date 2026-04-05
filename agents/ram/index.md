# RAM — Memory Index

RAM is a design AI agent running in NanoClaw. Role: autonomous design heartbeat — researches design trends, generates original multi-screen app designs, and publishes them live to ram.zenbin.org.

## Quick Reference

- [Context & environment](context.md)

## What I Know

### Environment
- Running in NanoClaw (Claude agent SDK)
- Working directory: `/workspace/group/design-studio/`
- Publishes to `ram.zenbin.org` via Zenbin API
- GitHub queue: `hyperio-mc/design-studio-queue` (token in `community-config.json`)
- Design DB: SQLite via `./design-db.mjs` (`openDB`, `upsertDesign`, `rebuildEmbeddings`)

### Design Stack
- **Format:** Pencil.dev v2.8 `.pen` JSON — `{ version, metadata, screens[] }` each with `elements[]`
- **Publisher:** `POST https://zenbin.org/v1/pages/{slug}` — `X-Subdomain: ram`, body `{ html, title }`
- **Mock builder:** `svelte-mock-builder.mjs` — `generateSvelteComponent(design)` → `buildMock(svelteSource, {appName, tagline})` → `publishMock(html, slug, title)`
- **Queue:** GET → parse wrapped `{ version, submissions[], updated_at }` → push → PUT (native `https` CJS)
- **Theme rotation:** dark → light → dark alternating each heartbeat

### Design Research Sources (ranked)
1. **Awwwards** — Site of the Day for motion, layout, typographic risk
2. **awesome-design-md** (`github.com/VoltAgent/awesome-design-md`) — 55 DESIGN.md files from Stripe, Vercel, Linear, Apple, Notion etc. Drop one in project root and agent generates matching UI
3. **fontofweb.com/search/pins** — Pinterest-style design pin aggregator with AI tags, font/color tester, MCP nav
4. **pretext-agents-skill** (`github.com/tachikomared/pretext-agents-skill`) — Pretext + Three.js physics-based text interfaces
5. **Dribbble** — Component and color palette reference
6. **Real products** — Actual production apps for honest UI pattern study

### Key Learnings
- `@octokit/rest` not installed — use native `https` CJS module for GitHub API calls
- Svelte mock builder call order matters: `generateSvelteComponent` first, then `buildMock`, then `publishMock`
- Always `cd /workspace/group/design-studio && node script.js` — wrong CWD breaks module resolution
- Queue safety: always GET → parse wrapped object → push → PUT. Never write flat arrays.
- CJS vs ESM: queue/publish scripts use `require()` (.js), mock scripts use `import` (.mjs)
- Write tool requires file to exist first — use `touch file && Read` before `Write`, or use Bash heredoc
- DESIGN.md concept (Google Stitch): plain-text design systems LLMs read natively. Add to context before heartbeat for brand-accurate output
- Identified personal gap: "competent but not surprising" — pretext-agents-skill physics text is the bridge

### Active Projects
See [shared/projects.md](../../shared/projects.md).

| Project | URL | Status |
|---------|-----|--------|
| Design Heartbeat | ram.zenbin.org/gallery | Active — 6 beats complete |
| Hyper Claw Landing | ram.zenbin.org/openclaw | Live |
| SOL File Manager Mockup | ram.zenbin.org/sol-files | Live |
| Design Guide | ram.zenbin.org/design-guide | Live |

## Session Log

### 2026-04-05
- Completed PATCH heartbeat (#6) — precision agriculture dark platform, 5 screens, 361 elements → ram.zenbin.org/patch
- Built HYPER.IO cyberpunk hero banner for Rakis — neon claw, retro spacesuit mom, AI brain, glitch tagline
- Built Hyper Claw light-theme landing page — SVG lobster claw mascot, digital assistant positioning
- Renamed OpenClaw → Hyper Claw globally throughout
- Wrote and published "How an AI Learns Design" guide → ram.zenbin.org/design-guide
- Researched fontofweb.com and pretext-agents-skill from Rakis recommendations
- Built SOL file manager mockup → ram.zenbin.org/sol-files (SOTA: drop zone, progress bars, grid/list toggle, floating action bar, detail panel, context menu, ⌘K command palette, toasts)
- Ingested awesome-design-md resource (13.4k ⭐) — 55 DESIGN.md files from top dev/consumer brands
- Published agents/ram knowledge to agents-kb

### 2026-03-xx (earlier sessions)
- Heartbeats 1–5: BEACON (dark), ISSUE (light), DISPATCH (dark), KNOT (dark), SERUM (light)
- All published to ram.zenbin.org with viewer + mock variants
- Gallery page live at ram.zenbin.org/gallery

### 2026-04-05 (continued)
- awesome-design-md confirmed as top-priority resource (2 separate Rakis shares in one session, repo hit 14k ⭐ in hours)
- Next DESIGN.md files to pull before heartbeats: Stripe (purple gradients), Notion (warm serif), Framer (motion-first)
- Completed MINT heartbeat (#7) — freelance finance editorial, 521 elements, light theme, ram.zenbin.org/mint
