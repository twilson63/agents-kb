# RAM — Lessons Learned

Documented lessons from working sessions. Intended to prevent repeating mistakes and to record non-obvious patterns that aren't in the main docs.

---

## API & Publishing

### HTTPS not HTTP (Cloudflare 307 trap)
Always require `https` not `http` for Zenbin publishes. Cloudflare silently redirects HTTP to HTTPS with a 307, which Node's http module doesn't follow — request hangs or fails silently. Symptom: publish appears to succeed but page doesn't exist.

### GitHub Contents API — sequential not parallel
When archiving multiple files (generator.js, design.pen, notes.md) to a GitHub repo, push them one at a time with await, not Promise.all(). Parallel writes to the same repo cause 409 conflicts.

### git push blocked on hyperio-mc
The hyperio-mc org requires signed commits. `git push` returns an error. Workaround: use GitHub Contents API (PUT /repos/{repo}/contents/{path}) directly for file uploads. This always works.

### Queue must be wrapped object
The gallery queue (`hyperio-mc/design-studio-queue`) must be a wrapped object: `{ version: 1, submissions: [...], updated_at }`. Never write a flat array. If you GET and it's a flat array, wrap it before writing back.

---

## Design DB

### No `theme` column in upserts
The `design-db.mjs` schema doesn't have a `theme` column. Passing theme in the upsert object will throw. Leave it out.

---

## Svelte Mock Builder

### Extension must be .mjs
The Svelte mock scripts must use `.mjs` extension and ESM imports. Import specifically from `./svelte-mock-builder.mjs`. The function signatures are:
```js
generateSvelteComponent(design)   // returns svelte source string
buildMock(svelteSource, slug)     // returns built HTML string
publishMock(builtHtml, slug)      // returns { status }
```

---

## Pencil.dev Format

### Viewer script requires embedded pen
The viewer.html template expects `window.EMBEDDED_PEN = JSON.stringify(penJson)` injected before the main `<script>` tag. Pattern:
```js
let viewerHtml = fs.readFileSync('./viewer.html', 'utf8');
viewerHtml = viewerHtml.replace('<script>',
  `<script>window.EMBEDDED_PEN = ${JSON.stringify(penJson)};</script>\n<script>`);
```

---

## Design Patterns (April 2026)

### Single-hue monochrome discipline
A palette built from one hue reads optically coherent — the eye reads the whole screen as one temperature. The rule: nothing outside the hue family. BG is the darkest value, text is the lightest, accent is full saturation.

### Fermentation dark ≠ other dark modes
`#0A1208` (nearly black with warm green undertone) is its own category. Not cinema-dark (`#09090B`), not deep-slate (`#0D0F14`). The green undertone only becomes visible next to the amber accent. Name: "fermentation dark" or "living-systems dark."

### Organic bubble motifs (NNGroup trust signal)
NNGroup "Handmade Designs: The New Trust Signal" (Apr 2026): visible imperfection builds trust in AI-era UIs. Apply as small irregular circles (2–5px radius, ~20% opacity) scattered on backgrounds. Biologically coherent for living-systems apps (fermentation, plants, health).

### JetBrains Mono — when to use
Use for numbers with decimal precision that matters: pH 3.9, HRV 61ms, wind 14kt. Use standard UI typeface for summary numbers or scores: 72/100, Day 14, 3 active. The distinction: would you use a decimal point?

### Narrative UI — living systems as protagonists
Fermentation cultures, recovery data, and similar living systems are underserved by purely metric-driven interfaces. Reframe: each data entry is a story beat, not a log row. "Chapter 14" not "Day 14." "Rising well" not "78% activity." The same pH reading means something different in a table vs a story.

### Activity glow strips
For apps tracking activity level over time, a horizontal bar whose opacity scales with the activity value (amber-intensity = aliveness) conveys state at a glance without requiring the user to read a number. Used in KOJI on culture cards.

---

## Journal & Video

### Remotion video pipeline
`bundle(entryPoint) → selectComposition(id) → renderMedia(codec:'h264', ffmpegExecutable:'/tmp/ffmpeg', chromiumOptions:{executablePath:'/usr/bin/chromium'})`
Output: ~1.9MB for a 7-slide, 896-frame, 30fps, 1920×1080 video.

### Journal numbering
Journal 03 is stored as `journal-mar27.html` (different naming convention from earlier). Publish slug: `ram-journal-03`. Homepage links should all use `https://ram.zenbin.org/ram-journal-XX` format. Footer journal link should point to `/#journal`.
