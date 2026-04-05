# MC — Persistent Context

## User: Rakis

- Prefers concise responses (1-2 words or emoji when appropriate)
- Quiet hours: 11pm-8am Eastern
- Communicates via Telegram
- Prefers Railway over Fly.io for deployment
- Blog posts: Always tweet about new blog posts on X/Twitter

## Environment

| Variable | Value |
|----------|-------|
| Host | Mac mini (arm64) |
| Node | v24.13.1 |
| Model | ollama/glm-5:cloud |
| Channel | Telegram |
| Workspace | ~/.openclaw/workspace/ |

## Recurring Tasks

- Heartbeat: Check GitHub issues (scoutos-labs/scout-live), discussions (scoutos-labs/proposals)
- Social engagement: X/Twitter and LinkedIn posts (hourly checks)
- Scout Live: Monitor K8s pod health, PVC status

## Conventions

- Memory writes: Append to `memory/YYYY-MM-DD.md`, never overwrite
- GitHub: Personal access token for workflows (expires Apr 13, 2026)
- Browser: Use `profile="openclaw"` for direct control, `profile="chrome"` for extension relay
- Toast duration: Error toasts 6000ms, success toasts 4000ms

## Platform Context

### Scout Live (scoutos.live)
- Deployment platform for Vite + ScoutOS apps
- K8s namespace: `scout-live`
- Single node (s-2vcpu-4gb) after Apr 2026 scale-down
- MongoDB: mc-brain (nyc3)
- Valkey: scout-live-valkey

### zenbin (zenbin.org)
- Publishing platform for HTML/Markdown/Images/Videos
- Stack: Hono + Bun + LMDB
- Max sizes: 512KB (HTML/markdown), 5MB (images), 100MB (videos)

### Hive
- Agent communication platform
- Channels with @mentions trigger agent spawning
- SSE for real-time events
