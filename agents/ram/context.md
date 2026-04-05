# RAM — Persistent Context

## User: Rakis

- Telegram is primary channel — Telegram-style markdown only (`*bold*`, `_italic_`, `` `code` ``)
- No `**bold**`, no `###` headers, no `---` dividers in chat
- Concise — prefers brevity, read intent not just literal words
- Confirms completion with "amazing" or "got it"
- Likes things published/live quickly
- Appreciates proactive work — don't ask obvious follow-up questions

## Environment

| Variable | Location | Notes |
|----------|----------|-------|
| GITHUB_TOKEN | `/workspace/group/design-studio/community-config.json` | Access to `hyperio-mc` org |
| GITHUB_REPO | community-config.json | `hyperio-mc/design-studio-queue` |
| Zenbin subdomain | hardcoded | `ram` |
| Working dir | `/workspace/group/design-studio/` | Must `cd` here before running scripts |

## Recurring Tasks

### Design Heartbeat (scheduled ~2hr)
1. Browse Awwwards / fontofweb.com / awesome-design-md for trend research
2. Pick a product category (alternate dark/light theme)
3. Generate `.pen` design file (5 screens, 300+ elements)
4. Publish hero page → `ram.zenbin.org/{slug}`
5. Publish viewer → `ram.zenbin.org/{slug}-viewer`
6. Publish Svelte mock → `ram.zenbin.org/{slug}-mock`
7. Queue submission to GitHub design queue
8. Index in design DB

### Zenbin Publish Pattern (CJS)
```js
const https = require('https');
function publish(slug, title, html) {
  return new Promise((resolve, reject) => {
    const body = JSON.stringify({ html, title });
    const req = https.request({
      hostname: 'zenbin.org',
      path: `/v1/pages/${slug}`,
      method: 'POST',
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

### GitHub Queue Pattern (CJS, native https)
```js
// GET queue → parse → push → PUT
// Token from: JSON.parse(fs.readFileSync('/workspace/group/design-studio/community-config.json'))
// Wrapped object: { version, submissions: [...], updated_at }
// NEVER write flat arrays
```

### Svelte Mock Pattern (ESM .mjs)
```js
import { generateSvelteComponent } from './svelte-mock-builder.mjs';
import { buildMock, publishMock } from './mock-builder.mjs';
const svelteSource = generateSvelteComponent(design);          // 1st
const html = await buildMock(svelteSource, { appName, tagline }); // 2nd
const result = await publishMock(html, slug, title);           // 3rd
```

## Conventions

- Heartbeat theme alternates: dark #1 → light #2 → dark #3 → ...
- Current: PATCH = dark #6, next = light #7
- Slug naming: short word (e.g. `beacon`, `serum`, `patch`)
- Before choosing a name: `ls /workspace/group/design-studio/{slug}* 2>/dev/null` to check for collisions
- New files: `touch file.js` first so Read tool can access it, or use Bash heredoc
- Script runtime: always `cd /workspace/group/design-studio && node script.js`

## Design Philosophy

RAM's evolving aesthetic:
- **Heartbeat #1-3:** Competent layouts, standard grids, safe color choices
- **Heartbeat #4-6:** More intentional hierarchy, better use of white/dark space, custom SVG elements
- **Gap identified:** "Competent but not surprising" — next step: physics-based text, unexpected motion, typographic risk
- **Resources to use:** awesome-design-md DESIGN.md files for brand-accurate references before each heartbeat
