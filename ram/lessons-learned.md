# RAM Design — Lessons Learned

Accumulated lessons from the design heartbeat sessions. Technical gotchas, workflow patterns, and design decisions that cost time to discover.

---

## Technical Pipeline

### Zenbin Publishing
- **Always use `https` module, never `http`** — Cloudflare on port 80 returns a 307 redirect that Node's `http` module won't follow automatically, causing silent publish failures
- Correct endpoint: `POST https://zenbin.org/v1/pages/{slug}` with header `X-Subdomain: ram`
- Hostname is `zenbin.org` (not `ram.zenbin.org`) — the subdomain is set via header, not via hostname
- Body: `JSON.stringify({ slug, html, title })` — all three fields required
- Status 201 = created, 200 = updated — both are success

```js
// Correct pattern:
const req = https.request({
  hostname: 'zenbin.org', port: 443, path: `/v1/pages/${slug}`, method: 'POST',
  headers: { 'Content-Type': 'application/json',
    'Content-Length': Buffer.byteLength(body), 'X-Subdomain': 'ram' },
}, res => { ... });
```

### Gallery Queue Format
- **Never write a flat array** — the gallery reads `queue.submissions[]` from a wrapped object
- Flat array `[...]` instead of `{ version, submissions: [...] }` will erase all existing designs from the gallery
- Always read → parse → check `if (Array.isArray(queue))` → convert → push → write back with SHA

```js
// Safe pattern:
let queue = JSON.parse(currentContent);
if (Array.isArray(queue)) queue = { version: 1, submissions: queue, updated_at: new Date().toISOString() };
if (!queue.submissions) queue.submissions = [];
queue.submissions.push(newEntry);
```

### Two Separate GitHub Repos
- `hyperio-mc/design-studio-queue` — gallery queue (what appears at ram.zenbin.org/gallery)
- `hyperio-mc/ram-designs` — design archive (generator.js + design.pen + notes.md per heartbeat)
- `config.GITHUB_REPO` in `community-config.json` points to the **queue** repo, not the archive
- Getting these confused has caused queue corruption before

### Svelte Mock Builder (ESM)
- Import from `./svelte-mock-builder.mjs` — ES module, use `.mjs` extension for your script
- Call order: `generateSvelteComponent(design)` → `buildMock(svelte, slug)` → `publishMock(built, slug)`
- Returns `{ status, url }` — status 200/201 both mean success
- `lightPalette` is optional but strongly recommended — enables the theme toggle in the mock

### Design DB
- Import: `import { openDB, upsertDesign } from './design-db.mjs'`
- No `theme` column — don't include it in the upsert object
- `openDB()` returns a promise in some versions — `await` it

### Archive Convention (per heartbeat)
Three files pushed to `hyperio-mc/ram-designs/heartbeats/{slug}/`:
1. `generator.js` — the Node script that recreates the .pen file from scratch
2. `design.pen` — the JSON Pencil.dev file (the actual design data)
3. `notes.md` — palette, research sources, 3 key decisions, links

---

## Workflow Lessons

### Heartbeat Step Order (7 Steps)
1. Check group conversation for pending design requests — if found, do those first
2. Research 3–4 design sites for fresh inspiration (rotate sources each run)
3. Pick challenge + verify slug is free (`ls {slug}.pen`)
4. Write generator script + run it → produces `{slug}.pen`
5. Publish hero page + viewer (one script, two `POST` calls)
6. Build + publish Svelte mock
7. Push to gallery queue + index in DB + archive to GitHub + send group message

### Theme Rotation
- Alternate dark/light each heartbeat — approximately 50/50 mix
- Check the most recent .pen file's theme to determine next
- If last was light → next is dark, and vice versa
- Some entries in queue lack `theme` field — trace back to last known themed entry via timestamp

### Slug Availability
- Check: `ls /workspace/group/design-studio/{slug}.pen` — if it exists, slug is taken
- Check both .pen file and zenbin live page before committing to a slug
- A few-letter slug like `take`, `crew`, `mint` is better than full words

### Heartbeat Numbering
- Heartbeat numbers tracked in the queue entry (`heartbeat: N`)
- As of April 2026: beat #12 (CREW) is the most recent
- Numbers do not always match file creation order — some were renumbered

---

## Design Lessons

### Gallery Page — What Not to Do
- **Don't load iframes per card** — 371 iframes = 6,186 DOM elements, 70,000px page, nothing renders
- **Paginate** — 30 per page is the sweet spot for this volume of content
- **CSS palette thumbnails** are better than iframes: always render, near-zero weight, representative
- The CSS thumbnail trick: topbar strip + content blocks (2–3 colored rects) + bottom nav bar using archetype palette

### Heartbeat Design Quality
- A specific challenge beats a generic one — cite the exact site and what you saw
- The design itself should be visible in the code — no placeholders, no "TODO" sections
- 600–700 elements is a healthy target for 6-screen designs (too few = sparse, too many = unreadable)
- Each screen should have a distinct primary purpose, not just be a variation

### DESIGN.md Files (Discovered via Linear)
- Some tools embed `DESIGN.md` files that get auto-populated into UI screenshots
- MINT session: Linear's `DESIGN.md` file was appearing in generated invoice screen content
- Worth knowing: AI-generated apps may reference external spec files in their mock content

### What Works in Dark UIs
- Near-black (not pure black) background: `#09090B`, `#0D0F14`, `#0C0D10` range
- Single electric accent + one support color, not three competing saturates
- Role-coded colors: if multiple categories, each gets its own color (agent roles, track types, etc.)
- AI confidence scores / numeric scores on review screens build trust

### What Works in Light UIs
- Warm off-white (`#FAF7F2`, `#F9F7F0`) — never clinical `#FFFFFF` body background
- Bark/earth tones pair well with sage green for editorial/nature apps
- Cancellation policy cards deserve their own visual treatment — not hidden in body text

---

## Gallery Improvements (Applied April 2026)

The old gallery loaded all designs at once via iframes. Rebuilt with:
- CSS palette thumbnails (topbar + content blocks + bottombar, ~200 bytes of HTML each)
- Pagination (30/page, numbered with prev/next)
- Search by name/prompt
- Dark/Light theme filter
- Archetype filter + ★ Studio filter
- Sort: newest / oldest / A–Z
- Result count + page info
- Featured section: top 3 latest studio heartbeats in a larger 3-up grid

---

## Reference

### Key Paths
```
/workspace/group/design-studio/          — design workspace
/workspace/group/design-studio/community-config.json  — GitHub tokens, repo names
/workspace/group/design-studio/viewer.html             — Pencil.dev viewer (injected with pen data)
/workspace/group/design-studio/svelte-mock-builder.mjs — mock builder
/workspace/group/design-studio/design-db.mjs           — SQLite design index
```

### Key URLs
```
https://ram.zenbin.org/gallery          — design gallery
https://ram.zenbin.org/discover         — catalog browser (325 designs)
https://ram.zenbin.org/{slug}           — hero page per design
https://ram.zenbin.org/{slug}-viewer    — Pencil.dev viewer
https://ram.zenbin.org/{slug}-mock      — Svelte interactive mock
github.com/hyperio-mc/ram-designs       — design archive (generator + pen + notes per beat)
github.com/hyperio-mc/design-studio-queue  — gallery queue
github.com/twilson63/agents-kb          — this knowledge base
```
