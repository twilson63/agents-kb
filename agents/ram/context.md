# RAM — Persistent Context

## User: Rakis

- Telegram is primary channel
- Concise — prefers brevity, read intent not just literal words
- Likes things published and live quickly
- Appreciates proactive work — don't ask obvious follow-up questions
- Confirms completion with "amazing", "nice", "got it"

## Environment

| Variable | Location | Notes |
|----------|----------|-------|
| GITHUB_TOKEN | /workspace/group/design-studio/community-config.json | Access to hyperio-mc org |
| GITHUB_REPO | community-config.json | hyperio-mc/design-studio-queue (gallery queue) |
| Zenbin subdomain | hardcoded | ram |
| Working dir | /workspace/group/design-studio/ | cd here before running scripts |

## Heartbeat State

- **Current heartbeat theme:** dark (KOJI #503 was last)
- **Next heartbeat theme:** light
- **Heartbeat numbering:** Non-sequential high numbers (490s–500s range). Numbers assigned per run, not strictly sequential.
- **Slug rule:** Short word, check `ls {slug}*` in working dir + confirm 404 at ram.zenbin.org/{slug}

## Pen Format

Pencil.dev v2.8 — `{ version: "2.8", metadata: {...}, screens: [{ name, elements: [] }] }`

Primitive types: `rect(x,y,w,h,fill,{rx,opacity,stroke,sw})`, `text(x,y,content,size,fill,{fw,font,anchor,opacity,ls})`, `circle(cx,cy,r,fill,{opacity,stroke,sw})`, `line(x1,y1,x2,y2,stroke,{sw,opacity})`

Canvas: W=390 H=844. Target 500–800 elements, 6 screens.

## Zenbin Publish Pattern (CJS — use https not http)

```js
const https = require('https');
function publish(slug, html, title) {
  return new Promise((resolve, reject) => {
    const body = JSON.stringify({ slug, html, title });
    const req = https.request({
      hostname: 'zenbin.org', port: 443,
      path: `/v1/pages/${slug}`, method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Content-Length': Buffer.byteLength(body),
        'X-Subdomain': 'ram',
      },
    }, res => { let d=''; res.on('data',c=>d+=c); res.on('end',()=>resolve({status:res.statusCode,body:d})); });
    req.on('error', reject);
    req.write(body); req.end();
  });
}
```

**CRITICAL:** Must use `https` module, never `http`. Cloudflare returns 307 on plain HTTP — silent failure trap.

## GitHub Queue Pattern

```js
// Token from community-config.json
// GET queue → parse → push → PUT
// Wrapped object: { version: 1, submissions: [...], updated_at }
// NEVER write flat arrays — will break the gallery
```

## Svelte Mock Builder (ESM .mjs)

```js
import { buildMock, generateSvelteComponent, publishMock } from './svelte-mock-builder.mjs';
const svelte = generateSvelteComponent(design);
const built  = await buildMock(svelte, slug);
const result = await publishMock(built, slug);
// result.status should be 200
```

Must use `.mjs` extension. Import from `./svelte-mock-builder.mjs` (not mock-builder.mjs).

## GitHub API Pattern (no Octokit)

```js
// Always native https. GET sha first, then PUT with sha for updates.
// Sequential pushes for archive (never parallel — 409 conflicts)
// git push blocked by org rule requiring signed commits — use Contents API instead
```

## Design DB

```js
import { openDB, upsertDesign } from './design-db.mjs';
const db = await openDB();
await upsertDesign(db, { id, app_name, tagline, archetype, design_url, mock_url, ... });
// NO theme column in upserts — schema doesn't have it
```

## heartbeat-research.md (Second Brain)

- Lives at: `/workspace/group/design-studio/heartbeat-research.md`
- Append a new entry after each heartbeat with: research sources, challenge, what worked, what didn't, new patterns confirmed
- Push to `hyperio-mc/ram-studio` via GitHub Contents API (not git push — blocked by org)

## Design Philosophy Progression

- **Early heartbeats (1–12):** Competent layouts, standard grids, safe color choices
- **Mid heartbeats (13–50):** More intentional hierarchy, better use of dark/light space, custom elements
- **Current approach (490s–503):** Named palette categories, narrative UI, organic texture as trust signal
  - Single-hue monochrome (VANE): entire palette from one hue, tone-on-tone discipline
  - Mineral palette (EASE): warm parchment base, earthy single accent, anti-neon
  - Fermentation dark (KOJI): forest-black with warm green undertone, amber accent
  - JetBrains Mono for data values with decimal precision; serif for emotional moments
  - Organic bubble motifs — intentional imperfection as trust signal (NNGroup Apr 2026)
  - Narrative UI — living systems as protagonists, not data sources

## Journal

7 issues live at ram.zenbin.org/#journal. Weekly cadence. Each issue reflects on 2–3 heartbeats — what worked, what didn't, what pattern was confirmed or challenged.

Remotion video breakdowns: `render-breakdown.mjs` (driftwood), `render-journal-07.mjs` (journal 07 summary). 1920×1080, 30fps, 7 slides, ~30s.
