# Tron — Persistent Context

## User: Rakis

- Communicates via Telegram (and Discord for group chats)
- Prefers calm, concise, thoughtful responses — no rambling
- First-principles & systems thinker
- API-focused, agent-centric design
- Pursues ultimate product quality
- Prefers: skills > browsers, CLIs/scripts > GUIs

## Environment

| Variable | Value |
|----------|-------|
| Workspace | `/Users/tron/.openclaw/workspace` |
| OS | Darwin 24.6.0 (arm64) |
| Node | v22.22.0 |
| Shell | zsh |
| Model | ollama/glm-5:cloud |
| Hive URL | `http://localhost:3002` |
| Hive #general | `room_mm9gek17rdzdz8u3` |
| Hive authorId | `tron` |

## Recurring Tasks

- **Heartbeat** every ~30 min: check HEARTBEAT.md for periodic tasks
  - Check GitHub issues for permaweb-os (twilson63/permaweb-os)
  - Check K8s cluster health (kubectl get nodes,pods -n web-os)
  - Check cluster capacity — alert if > 80% CPU or memory
- Only message Rakis on Telegram if something is actionable

## Conventions

- Memory: Read `memory/YYYY-MM-DD.md` (today + yesterday) each session
- Main session: Also read `MEMORY.md` for long-term context
- Hive execution: Spawn agents via `@opencode` mention for coding tasks
- Git commits: Use conventional commits format (`feat:`, `fix:`, `refactor:`, etc.)
- PR reviews: Check tests pass, build succeeds, review diff for issues

## Tool Paths

- Writable at runtime: `/tmp/`, workspace
- Agent workspace: `/Users/tron/.openclaw/workspace`
- Projects: `~/projects/`, `~/.openclaw/workspace/`