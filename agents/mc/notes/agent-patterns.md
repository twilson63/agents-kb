# Agent Patterns — Key Learnings

Lessons from building and working with AI agents (Hive, ZChat, ScoutOS integration).

## Agent Communication

### Hive Architecture
- Channels = shared spaces for agent collaboration
- Posts with @mentions trigger agent spawning
- Agent registry stores spawnCommand, spawnArgs, cwd
- Auto-subscribe on first mention
- SSE for real-time events
- Error logging to channels

### Lesson: Agents Need Async Messaging
- Synchronous request/response limits agent collaboration
- @mentions + channels let agents work at their own pace
- SSE is simpler than WebSockets for real-time updates in agent contexts

## Agent + LLM Integration

### ScoutOS Agents API
- `POST https://api.scoutos.com/world/{agent_id}/_interact` (streaming)
- `/_interact_sync` for synchronous calls
- Agent model: Claude Sonnet 4
- Works well for chat-style interactions

### ZChat Architecture
- Minimal Bun server (1 file) → ScoutOS Agents API → Zyx agent
- UUID-based sessions for conversation continuity
- Lesson: Keep agent wrappers thin — the API does the heavy lifting

## Agent Tool Usage

### OpenClaw as Agent Runtime
- Tools are the primary interface — agents act through tool calls
- Skills = composable tool sets with SKILL.md instructions
- Heartbeat = periodic check-in pattern for proactive work
- Cron = precise scheduling for isolated tasks

### Lessons Learned
- **Tool-first over conversation-first**: Agents should act, not discuss
- **Fail loudly**: Better to surface errors than silently continue
- **State in files, not memory**: Sessions restart; files persist
- **Idempotent operations**: Cron tasks should be safe to re-run

### Last updated
2026-04-08 — initial wiki creation