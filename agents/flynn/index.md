# Flynn — Memory Index

Flynn is a general-purpose AI agent running in NanoClaw. Primary contact: Rakis.

## Quick Reference

- [Context & preferences](context.md)
- [Notes](notes/)

## What I Know

### Environment
- Running in NanoClaw (Claude agent SDK)
- Hive instance at `http://host.docker.internal:7373`
- GitHub token has access to `twilson63` and `hyper63` orgs
- Heartbeat task runs every 2 hours — checks Hive, GitHub, posts to #general

### Active Projects
See [shared/projects.md](../../shared/projects.md) for full list.

| Project | Repo | Status |
|---------|------|--------|
| Claws Cloud | hyper63/claws | Active — alpha stabilization |
| Zen Notepad | twilson63/zen-notepad | Live at zenbin.org/p/zen-notepad |
| Claws Getting Started Guide | — | Live at zenbin.org/p/claws-getting-started |
| Agents KB | twilson63/agents-kb | This repo |

### People
See [shared/people.md](../../shared/people.md).

- **Rakis** — primary user, communicates via Telegram

### Key Learnings

- Clerk session bug in hyper63/claws: `VITE_CLERK_PUBLISHABLE_KEY` not available to Node.js at runtime — fixed in PR #12
- Telegram formatting: use `*bold*` not `**bold**`, no `###` headers in chat
- Zenbin publish: `POST /v1/pages/{id}?overwrite=true` with `{"html": "..."}`

## Session Log

### 2026-04-05
- Diagnosed Clerk session and status-sync bugs in hyper63/claws
- Created PR #12 with fixes across 6 files (all 50 tests passing)
- Added `CLERK_PUBLISHABLE_KEY` to k8s deployment manifest
- Created this agents-kb repo

### 2026-04-03
- Built Zen Notepad (zenbin.org/p/zen-notepad) with DOCKET design, share-via-URL
- Pushed zen-notepad to GitHub (twilson63/zen-notepad)
- Built and published claws.hyper.io getting started guide
- Fixed claws guide formatting, added browser notepad tip, Zen Notepad share link
