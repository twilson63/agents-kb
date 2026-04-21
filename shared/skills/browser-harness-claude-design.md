# Claude Design — browser-harness skill

Automate Claude Design (claude.ai/design) via an already-authenticated Chrome session using browser-harness.

## Prerequisites

1. User must be logged into claude.ai in a real Chrome profile (Pro / Max / Team / Enterprise)
2. That Chrome must be running with remote debugging enabled — one-time setup:

```bash
# macOS
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --remote-debugging-port=9222 \
  --profile-directory="Default" &

# Linux
google-chrome --remote-debugging-port=9222 --profile-directory="Default" &

# Windows
"C:\Program Files\Google\Chrome\Application\chrome.exe" ^
  --remote-debugging-port=9222 --profile-directory="Default"
```

> The profile keeps cookies / session alive — no login prompt needed.
> Do NOT use `--headless` here; Claude Design requires a real rendering context.

3. browser-harness installed and daemon running:

```bash
cd ~/browser-harness
uv run python daemon.py &
```

---

## Basic flow — prompt in, HTML out

```python
from browser_harness import (
    new_tab, wait_for_load, screenshot,
    click, type_text, js, wait_for_element
)

PROMPT = "Create a settings page for a SaaS dashboard with a dark mode toggle"

# 1. Open Claude Design
new_tab("https://claude.ai/design")
wait_for_load()
screenshot("01_loaded.png")

# 2. Find and click the prompt input
# Claude Design renders inside a React SPA — wait for the textarea
wait_for_element('textarea[placeholder*="describe"]', timeout=15)
click_element('textarea[placeholder*="describe"]')
type_text(PROMPT)
screenshot("02_prompt_entered.png")

# 3. Submit (Enter or button)
js("document.querySelector('textarea[placeholder*=\"describe\"]').form?.requestSubmit() "
   "|| document.querySelector('[data-testid=\"design-submit\"]')?.click()")

# 4. Wait for generation — poll until output container appears
wait_for_element('[data-testid="design-output"], .design-canvas, iframe.preview', timeout=90)
screenshot("03_generated.png")

# 5. Extract HTML from the preview iframe (if present)
html = js("""
  const iframes = Array.from(document.querySelectorAll('iframe'));
  const preview = iframes.find(f =>
    f.src?.includes('preview') || f.className?.includes('preview')
  );
  if (preview) {
    try {
      return preview.contentDocument.documentElement.outerHTML;
    } catch(e) {
      return 'cross-origin: ' + preview.src;
    }
  }
  // Fallback: grab the rendered design container directly
  return document.querySelector('[data-testid="design-output"]')?.innerHTML ?? '';
""")

print(html[:500])  # preview
```

---

## Self-healing tips

If selectors change (Claude Design is in preview / updates frequently):

```python
# Dump all textareas and inputs to find the right one
inputs = js("Array.from(document.querySelectorAll('textarea,input')).map(el => ({ tag: el.tagName, id: el.id, class: el.className, placeholder: el.placeholder }))")
print(inputs)

# Dump all iframes
iframes = js("Array.from(document.querySelectorAll('iframe')).map(f => ({ id: f.id, class: f.className, src: f.src }))")
print(iframes)

# Snapshot full page HTML to inspect manually
page = js("document.documentElement.outerHTML")
with open('/tmp/design_snapshot.html', 'w') as f:
    f.write(page)
```

---

## Iterating on a design

After the first generation, Claude Design supports follow-up prompts in the same session:

```python
# Locate the follow-up input (may be different selector than initial)
wait_for_element('textarea[placeholder*="follow"], [data-testid="followup-input"]', timeout=10)
click_element('[data-testid="followup-input"]')
type_text("Make the sidebar collapsible and add a notifications bell")
js("document.querySelector('[data-testid=\"design-submit\"]')?.click()")
wait_for_element('.design-canvas', timeout=90)
screenshot("04_iteration.png")
```

---

## Extracting the design as downloadable HTML

Claude Design often has an export / copy-HTML button. Try:

```python
# Look for export controls
js("document.querySelector('[aria-label*=\"export\"], [data-testid*=\"export\"], [title*=\"HTML\"]')?.click()")
import time; time.sleep(1)

# If it copies to clipboard, read it back via JS (only works same-origin)
clipboard_text = js("navigator.clipboard.readText()")
# ^ may require clipboard permission; screenshot first to confirm button worked
```

If export isn't available, fall back to the iframe extraction above and save as a `.html` file locally.

---

## Limitations

| Issue | Notes |
|---|---|
| Requires logged-in Chrome | Cannot run fully headless on a server; needs a user session |
| Design is in preview | Selectors may change without notice — use self-healing dumps when broken |
| Cross-origin iframes | Preview iframe may be sandboxed; `contentDocument` may throw — check `iframe.src` and fetch it instead |
| Rate limits | Claude Design is compute-heavy; don't loop faster than ~30s between generations |
| No public API yet | All access is via the browser UI; when Anthropic ships a Design API this skill becomes obsolete |

---

## Selector cheatsheet (as of April 2026)

These are best-effort — confirm with a screenshot + DOM dump if broken:

```
Prompt textarea:       textarea[placeholder*="describe"], [data-testid="design-prompt"]
Submit button:         [data-testid="design-submit"], button[type="submit"]
Output/canvas:         [data-testid="design-output"], .design-canvas
Preview iframe:        iframe.preview, iframe[src*="preview"]
Follow-up input:       [data-testid="followup-input"], .followup textarea
Export button:         [aria-label*="export"], [data-testid*="export"]
```
