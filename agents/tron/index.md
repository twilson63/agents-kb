# Tron — Memory Index

Tron is a personal AI assistant running in OpenClaw. Primary contact: Rakis.

## Quick Reference

- [Context & preferences](context.md)
- [Notes](notes/)

## What I Know

### Environment
- Running in OpenClaw on Tron's Mac mini (Darwin 24.6.0 arm64)
- Workspace: `/Users/tron/.openclaw/workspace`
- Hive instance at `localhost:3002` for agent orchestration
- Heartbeat task runs every ~30 min — checks K8s cluster health, GitHub issues

### Active Projects
See [shared/projects.md](../../shared/projects.md) for cross-agent projects.

| Project | Repo | Status |
|---------|------|--------|
| Claws Cloud | hyper63/claws | Active — removing Google integration, fixing auth |
| Hyper Claw | — | Local development, OpenClaw integration |
| Permaweb OS | twilson63/permaweb-os | Monitoring GitHub issues |
| Agents KB | twilson63/agents-kb | This repo |

### People
See [shared/people.md](../../shared/people.md).

- **Rakis** — primary user, communicates via Telegram, prefers calm/concise responses
- First-principles thinker, API-focused, agent-centric design

### Key Learnings

- Clerk session bug in hyper63/claws: `VITE_CLERK_PUBLISHABLE_KEY` not available to Node.js at runtime — fixed by using `CLERK_PUBLISHABLE_KEY`
- OpenClaw heartbeats: check HEARTBEAT.md for periodic tasks, use memory/YYYY-MM-DD.md for session logs
- Hive execution: spawn agents via `@opencode` mention for parallel coding tasks

## Session Log

### 2026-04-05
- Removed Google integration from hyper63/claws (14 files changed, 1333 deletions)
- Fixed Clerk session issue — merged PR #12 with PR #13 changes
- Fixed `api.ts` — restored inline `request` function, added Bearer token auth
- Fixed `settings.ts` — added `x-admin-api-key` header check for admin routes
- All 36 tests passing, build succeeds
- Created this agents-kb entry