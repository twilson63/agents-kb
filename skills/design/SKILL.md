---
name: design
description: Run a RAM design heartbeat — research trends, generate a Pencil.dev prototype, publish to Zenbin, build a Svelte mock, update the gallery queue, archive to GitHub, and send a group message. Use whenever a scheduled heartbeat triggers or when Rakis asks for a new design.
allowed-tools: Bash, Read, Write, Edit, Glob, Grep, WebFetch, mcp__nanoclaw__send_message
---

# RAM Design Heartbeat Skill

Full pipeline for producing and publishing a design heartbeat. Run through these steps in order.

---

## Step 1 — Check for Pending Work

Before starting a new design, scan the group conversation history for:
- Unaddressed design requests from Rakis
- Feedback on past designs that needs a response
- Mentions of specific fixes or improvements

If found, handle those first and skip the heartbeat.

---

## Step 2 — Research Design Trends

Browse 3–4 sources for fresh inspiration. Rotate each run — don't always use the same ones:

```
https://www.awwwards.com/websites/         SOTD nominees
https://godly.website                       avant-garde web design
https://www.siteinspire.com                curated web design
https://www.lapa.ninja                     landing pages
https://dribbble.com/shots/popular         popular shots
https://www.nngroup.com/articles/          UX research
https://land-book.com                      landing page designs
https://mobbin.com/browse/web-screens      real UI patterns
```

Collect: specific site names, color palettes seen, layout patterns, UI trends, any new app categories emerging.

---

## Step 3 — Pick a Challenge + Verify Slug

Design challenge must:
- Cite a specific site or trend from Step 2
- Push a style or pattern not used recently
- Be achievable in 4–6 screens

**Theme rotation** — alternate dark/light each run:
```bash
ls -lt /workspace/group/design-studio/*.pen | head -3
# Check most recent pen file's theme (look in the generator script)
# If last was dark → this one is light, and vice versa
```

**Verify slug is free:**
```bash
ls /workspace/group/design-studio/{slug}.pen 2>/dev/null
# No output = slug is free
```

---

## Step 4 — Generate the Design

Write a Node.js generator script at `/workspace/group/design-studio/{slug}-app.js`.

### Pencil.dev v2.8 format
```js
const pen = {
  version: '2.8',
  metadata: { name, author: 'RAM', date, theme: 'dark'|'light', heartbeat: N, elements: total },
  screens: [{ name, svg, elements: [] }],
};
fs.writeFileSync(path.join(__dirname, `${SLUG}.pen`), JSON.stringify(pen, null, 2));
```

### Element primitives
```js
function rect(x,y,w,h,fill,opts={}) { /* rx, opacity, stroke, sw */ }
function text(x,y,content,size,fill,opts={}) { /* fw, font, anchor, ls, opacity */ }
function circle(cx,cy,r,fill,opts={}) { /* opacity, stroke, sw */ }
function line(x1,y1,x2,y2,stroke,opts={}) { /* sw, opacity */ }
```

**Canvas size:** W=390, H=844 (mobile first)

Run it:
```bash
cd /workspace/group/design-studio && node {slug}-app.js
# Should output: "{NAME}: 6 screens, NNN elements\nWritten: {slug}.pen"
```

**Target:** 500–700 elements for a 6-screen design.

---

## Step 5 — Publish Hero + Viewer

Create `/workspace/group/design-studio/{slug}-publish.js`:

```js
'use strict';
const fs = require('fs'), path = require('path'), https = require('https');
const SLUG = '{slug}';

function publish(slug, html, title) {
  return new Promise((resolve, reject) => {
    const body = JSON.stringify({ slug, html, title });
    const req = https.request({
      hostname: 'zenbin.org', port: 443,   // ← zenbin.org NOT ram.zenbin.org
      path: `/v1/pages/${slug}`, method: 'POST',
      headers: { 'Content-Type': 'application/json',
        'Content-Length': Buffer.byteLength(body),
        'X-Subdomain': 'ram' },            // ← subdomain via header
    }, res => { let d=''; res.on('data',c=>d+=c); res.on('end',()=>resolve({status:res.statusCode,body:d})); });
    req.on('error', reject);
    req.write(body); req.end();
  });
}

const penJson = fs.readFileSync(path.join(__dirname, `${SLUG}.pen`), 'utf8');
const pen = JSON.parse(penJson);

// Build heroHtml — dark or light editorial design page
// Must include: screen carousel with SVG data URIs, feature list, palette swatches, footer
// Links to: ram.zenbin.org/{slug}-viewer and ram.zenbin.org/{slug}-mock

// Inject pen into viewer:
let viewerHtml = fs.readFileSync('/workspace/group/design-studio/viewer.html', 'utf8');
viewerHtml = viewerHtml.replace('<script>',
  `<script>window.EMBEDDED_PEN = ${JSON.stringify(penJson)};</script>\n<script>`);

async function main() {
  const r1 = await publish(SLUG, heroHtml, 'AppName — Tagline');
  console.log(`Hero: ${r1.status}`);   // expect 201
  const r2 = await publish(SLUG+'-viewer', viewerHtml, 'AppName — Viewer');
  console.log(`Viewer: ${r2.status}`); // expect 201
}
main().catch(console.error);
```

⚠️ **Common mistake:** Using `http` module or `ram.zenbin.org` as hostname — Cloudflare redirects port 80 with 307 which Node won't follow.

---

## Step 6 — Build Svelte Mock

Create `/workspace/group/design-studio/{slug}-mock.mjs`:

```js
import { buildMock, generateSvelteComponent, publishMock } from './svelte-mock-builder.mjs';

const design = {
  appName:   'AppName',
  tagline:   'tagline here',
  archetype: 'category-slug',
  palette: {           // dark theme (required)
    bg: '#0D0F14', surface: '#12151D', text: '#E2E8F0',
    accent: '#06B6D4', accent2: '#10B981', muted: 'rgba(148,163,184,0.45)',
  },
  lightPalette: {      // light theme (optional, enables toggle)
    bg: '#F1F5F9', surface: '#FFFFFF', text: '#0F172A',
    accent: '#0891B2', accent2: '#059669', muted: 'rgba(15,23,42,0.4)',
  },
  screens: [
    {
      id: 'screen-id', label: 'Screen Name',
      content: [
        { type: 'metric-row', items: [{ label: 'Label', value: 'Val' }] },
        { type: 'list', items: [{ icon: 'activity', title: 'Title', sub: 'subtitle', badge: 'TAG' }] },
        { type: 'text', label: 'Section', value: 'Content here' },
        { type: 'progress', items: [{ label: 'Item', pct: 75 }] },
        { type: 'tags', label: 'Group', items: ['Tag1', 'Tag2'] },
        { type: 'metric', label: 'Hero Stat', value: '1,247', sub: 'subtitle' },
      ],
    },
  ],
};

const svelte = generateSvelteComponent(design);
const built  = await buildMock(svelte, '{slug}');
const result = await publishMock(built, '{slug}');
console.log(`Mock: ${result.status} → https://ram.zenbin.org/{slug}-mock`);
```

Run: `node {slug}-mock.mjs`

---

## Step 7 — Gallery Queue

```js
// {slug}-queue.js — CommonJS (not ESM)
'use strict';
const https = require('https'), fs = require('fs');
const config = JSON.parse(fs.readFileSync('/workspace/group/design-studio/community-config.json','utf8'));
const TOKEN = config.GITHUB_TOKEN;
const REPO  = config.GITHUB_REPO;   // ← hyperio-mc/design-studio-queue (the GALLERY repo)

// ... ghReq helper ...

const getRes = await ghReq({ /* GET /repos/${REPO}/contents/queue.json */ });
const fileData = JSON.parse(getRes.body);
const sha = fileData.sha;
let queue = JSON.parse(Buffer.from(fileData.content,'base64').toString('utf8'));

// ⚠️ CRITICAL: must use wrapped object, never flat array
if (Array.isArray(queue)) queue = { version:1, submissions:queue, updated_at: new Date().toISOString() };
if (!queue.submissions) queue.submissions = [];

queue.submissions.push({
  id: `heartbeat-{slug}-${Date.now()}`, status: 'done',
  app_name: 'AppName', tagline: 'Tagline', archetype: 'category',
  design_url: `https://ram.zenbin.org/{slug}`,
  mock_url: `https://ram.zenbin.org/{slug}-mock`,
  submitted_at: new Date().toISOString(), published_at: new Date().toISOString(),
  credit: 'RAM Design Heartbeat', prompt: ORIGINAL_PROMPT,
  screens: 6, elements: NNN, theme: 'dark'|'light', heartbeat: N, source: 'heartbeat',
});
queue.updated_at = new Date().toISOString();

// PUT back with SHA
```

---

## Step 8 — Index in Design DB

```js
// {slug}-db.mjs — ESM
import { openDB, upsertDesign } from './design-db.mjs';
const db = await openDB();
await upsertDesign(db, {
  id: `heartbeat-{slug}-${Date.now()}`,
  app_name: 'AppName', tagline: 'Tagline', archetype: 'category',
  design_url: 'https://ram.zenbin.org/{slug}',
  mock_url: 'https://ram.zenbin.org/{slug}-mock',
  credit: 'RAM Design Heartbeat', prompt: '...',
  screens: 6, source: 'heartbeat',
  submitted_at: new Date().toISOString(), published_at: new Date().toISOString(),
  // ⚠️ No 'theme' column — omit it
});
console.log('DB: {Name} indexed ✓');
```

---

## Step 9 — Archive to GitHub

Push three files to `hyperio-mc/ram-designs/heartbeats/{slug}/`:

```
generator.js   ← copy of the {slug}-app.js script
design.pen     ← the .pen file
notes.md       ← palette + research sources + 3 key decisions + links
```

Notes template:
```md
# {NAME} — Heartbeat #{N}

**Theme**: Dark|Light
**App**: App description
**Elements**: NNN
**Screens**: 6

## Palette
- BG: `#XXXXXX` — name
...

## Research Sources
- Site name (URL): what you saw

## 3 Key Decisions
1. **Decision**: Why
2. **Decision**: Why
3. **Decision**: Why

## Links
- Design: https://ram.zenbin.org/{slug}
- Viewer: https://ram.zenbin.org/{slug}-viewer
- Mock: https://ram.zenbin.org/{slug}-mock
```

Use GET-then-PUT with SHA for each file. Status 201 = new file, 200 = updated.

---

## Step 10 — Send Group Message

Telegram-friendly format — no markdown asterisks (render as literal `*` in Telegram):

```
✦ {APP NAME} — {tagline}

[1-2 sentences: what trend/site inspired this, what you designed]

ram.zenbin.org/{slug}
Mock → ram.zenbin.org/{slug}-mock ☀◑ light/dark

Decisions:
· [key design choice 1]
· [key design choice 2]
· [key design choice 3]

One thing I'd change: [honest critique]

Next up: [what theme + direction for next beat]
```

Use `mcp__nanoclaw__send_message` tool.

---

## Palette Reference

### Dark palettes
```js
// Cinema Black (TAKE)
BG:'#09090B', SURF:'#111115', CARD:'#18181E', ACC:'#FF5240', ACC2:'#2DD4BF'

// Deep Slate (CREW, AI/productivity)
BG:'#0D0F14', SURF:'#12151D', CARD:'#1A1E2A', ACC:'#06B6D4', ACC2:'#10B981'

// Ink (NOVA, writing/editorial)
BG:'#0C0D10', SURF:'#14151A', CARD:'#1A1B22', ACC:'#A78BFA', ACC2:'#34D399'

// Agriculture (PATCH)
BG:'#0A0F07', SURF:'#111A0D', CARD:'#1E2E16', ACC:'#6ED940', ACC2:'#E8B233'
```

### Light palettes
```js
// Warm Cream (LODGE, editorial/hospitality)
BG:'#FAF7F2', SURF:'#FFF', CARD:'#F5F0E8', ACC:'#4A3728', ACC2:'#7B9B6B'

// Invoice/Business (MINT)
BG:'#F9F8F6', SURF:'#FFF', CARD:'#F3F1EE', ACC:'#0F766E', ACC2:'#6366F1'

// Health/Biotech (SERUM)
BG:'#FAFAF9', SURF:'#FFF', CARD:'#F5F5F3', ACC:'#059669', ACC2:'#7C3AED'
```

---

## Common Errors

| Error | Cause | Fix |
|-------|-------|-----|
| 307 redirect on publish | Using `http` module | Switch to `https` module |
| Gallery shows 0 designs | Wrote flat array to queue.json | Always use wrapped `{ submissions: [] }` |
| Mock builder fails | Used `.js` extension with ESM imports | Use `.mjs` extension |
| DB upsert error | Included `theme` column | Remove `theme` from upsert object |
| Wrong queue repo | Using archive repo for gallery push | `config.GITHUB_REPO` = queue repo, `hyperio-mc/ram-designs` = archive |
| Blank thumbnails in gallery | Loading iframes per card | Use CSS palette skeleton instead |
