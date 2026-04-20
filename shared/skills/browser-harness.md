---
name: browser-harness
description: Self-healing browser automation via direct CDP. Use for complex browser tasks — multi-step flows, shadow DOM, cross-origin iframes, SPAs. Falls back to writing missing helpers on the fly. Prefer this over agent-browser for tasks that require real interaction or where DOM snapshots are unreliable.
allowed-tools: Bash(uv:*), Bash(curl:*), Bash(chromium:*), Bash(pkill:*)
---

# browser-harness

Self-healing browser automation that connects directly to Chrome/Chromium via CDP (Chrome DevTools Protocol). No Playwright abstraction — one websocket to Chrome. When a helper function is missing, the agent writes it into `helpers.py` and continues.

Repo: https://github.com/browser-use/browser-harness

---

## Setup (first time in a sandbox)

### 1. Install uv

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
export PATH="$HOME/.local/bin:$PATH"
```

uv is a fast Python package manager (Rust-based, by Astral). Not npm — standalone install.

### 2. Clone and install browser-harness

```bash
git clone https://github.com/browser-use/browser-harness /tmp/browser-harness
cd /tmp/browser-harness
uv tool install -e .
export PATH="$HOME/.local/bin:$PATH"
```

### 3. Start Chromium with remote debugging

In OpenClaw sandboxes, Chromium is at `/usr/bin/chromium`. No display needed — headless works:

```bash
mkdir -p /tmp/chrome-profile
/usr/lib/chromium/chromium \
  --headless=new \
  --no-sandbox \
  --disable-gpu \
  --disable-dev-shm-usage \
  --remote-debugging-port=9222 \
  --user-data-dir=/tmp/chrome-profile \
  --window-size=1280,800 \
  >/tmp/chromium.log 2>&1 &
sleep 4
```

### 4. Get the CDP websocket URL

```bash
WS=$(curl -s http://127.0.0.1:9222/json/version | python3 -c "import sys,json; print(json.load(sys.stdin)['webSocketDebuggerUrl'])")
echo "CDP WS: $WS"
```

### 5. Run a quick smoke test

```bash
export BU_CDP_WS="$WS"
cd /tmp/browser-harness
uv run browser-harness <<'PY'
new_tab("https://example.com")
wait_for_load()
print(page_info())
screenshot("/tmp/test.png")
PY
```

If you see `{'url': 'https://example.com', ...}` — you're connected.

---

## Day-to-day usage

Always set the env var pointing at the running CDP websocket:

```bash
export PATH="$HOME/.local/bin:$PATH"
export BU_CDP_WS="ws://127.0.0.1:9222/devtools/browser/<id>"
cd /tmp/browser-harness
```

### Navigation

```bash
uv run browser-harness <<'PY'
new_tab("https://example.com")   # always use new_tab for first nav — goto clobbers active tab
wait_for_load()
print(page_info())
PY
```

### Screenshot + click

```bash
uv run browser-harness <<'PY'
screenshot("/tmp/before.png")   # see what's there
click(640, 360)                  # coordinate clicks pass through iframes/shadow DOM
wait_for_load()
screenshot("/tmp/after.png")    # verify
PY
```

### Fill a form

```bash
uv run browser-harness <<'PY'
click(183, 434)     # click the field first
type_text("Flynn")  # type without clearing
click(267, 514)
type_text("flynn@example.com")
click(267, 576)     # submit button
wait_for_load()
screenshot("/tmp/result.png")
PY
```

### Extract data

```bash
uv run browser-harness <<'PY'
result = js("document.querySelector('h1').textContent")
print(result)

# For bulk HTTP (no browser overhead)
pages = http_get("https://api.example.com/data")
print(pages)
PY
```

### Raw CDP (advanced)

```bash
uv run browser-harness <<'PY'
result = cdp("Runtime.evaluate", expression="document.title")
print(result)
PY
```

---

## Self-healing in action

If a helper like `upload_file()` doesn't exist in `helpers.py`, the agent notices the `AttributeError`, writes the function into `helpers.py`, and retries — all within the same run. This is the core feature.

After a self-healing edit, the updated `helpers.py` is used immediately on the next `browser-harness` invocation too (since it's installed as an editable package).

---

## Recovering from a stale session

If you see `no close frame received or sent`:

```bash
cd /tmp/browser-harness
uv run python3 - <<'PY'
from admin import restart_daemon
restart_daemon()
PY
```

If that also hangs, kill Chrome and restart:

```bash
pkill -f "chromium.*9222"
# re-run the Chromium launch command from Setup step 3
```

---

## Known limitations in sandboxes

### Cloudflare Turnstile blocks headless

Any page behind Cloudflare's "Verify you are human" checkbox will block headless Chromium — this affects browser-harness, Playwright, and any other headless tool equally. The CAPTCHA detects the headless user-agent.

*Affected*: `accounts.hyper.io` (Clerk auth), `console.agentmail.to` signup, and most SaaS auth flows.

*Workarounds*:
1. Use a pre-authenticated session (save cookies after a human login, load them in the harness)
2. Use Browser Use cloud remote browsers — real browser fingerprints that pass CF: `BROWSER_USE_API_KEY=<key> start_remote_daemon("work")`
3. Disable Cloudflare bot protection in Clerk/auth settings for dev environments
4. Call the service's API directly (bypassing the browser auth flow entirely)

### DevToolsActivePort on Chrome 144+

Chrome 144+ doesn't serve `/json/version` at `chrome://inspect`. The harness reads `DevToolsActivePort` instead. If you need to set it manually:

```bash
WS_PATH=$(curl -s http://127.0.0.1:9222/json/version | python3 -c "import sys,json; d=json.load(sys.stdin); print(d['webSocketDebuggerUrl'].split('9222')[1])")
echo "9222\n${WS_PATH}" > /tmp/chrome-profile/DevToolsActivePort
```

---

## vs agent-browser

| | agent-browser | browser-harness |
|---|---|---|
| Approach | Playwright + accessibility tree | Direct CDP + screenshots |
| Iframes / shadow DOM | Limited | ✅ coordinate clicks pass through |
| Self-healing | No | ✅ writes missing helpers |
| Setup | Zero (built-in) | ~2 min first time |
| Cloudflare | Same limitation | Same limitation |
| Best for | Simple nav, forms, structured pages | Complex SPAs, multi-step flows, research tasks |

Use `agent-browser` for quick/simple tasks. Use `browser-harness` when the DOM is tricky or the task requires real interaction patterns.
