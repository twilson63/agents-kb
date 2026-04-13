# Glossary

## Tools & Services

**NanoClaw** — the Claude agent platform Flynn runs on. Handles scheduling, Telegram integration, Hive messaging.

**Hive** — internal messaging system at `http://host.docker.internal:7373`. Channels include `#general` (`channel_mmt8g799lforvh4x`).

**Zenbin** — publishing platform at `zenbin.org`. Publish HTML pages via `POST /v1/pages/{id}?overwrite=true`.

**LMDB** — Lightning Memory-Mapped Database. Used in hyper63/claws for persistent storage.

**Claws** — AI-powered Telegram bot instances provisioned by Claws Cloud (hyper63/claws).

**OpenClaw** — the runtime container that runs each Claw in Kubernetes.

**DOCKET** — a design theme from ram.zenbin.org/gallery. Used in Zen Notepad. Dark: `#1C1A16` bg, `#C95A2C` accent (burnt sienna).

## Patterns

**URL-safe base64** — standard base64 with `+`→`-`, `/`→`_`, stripped `=` padding. Used for Zen Notepad share links.

**Heartbeat task** — Flynn's recurring 2-hour check: Hive mentions → GitHub issues/PRs → post to #general → alert Rakis if actionable.

**VITE_ prefix** — Vite replaces `import.meta.env.VITE_*` at build time. These values are NOT available as `process.env.VITE_*` to Node.js at runtime.

**Scout Live** — deployment platform at scoutos.live. Deploys Vite + ScoutOS apps to K8s. Data ports provide MongoDB/Memory adapters at `/_ports/data/:collection/*`.

**HYPR / OnHyper** — API proxy platform at onhyper.io. Users store API keys server-side; apps call proxy endpoints. Supports OpenAI, Anthropic, OpenRouter, ScoutOS, Ollama.

**ScoutOS Agents** — AI agent runtime by ScoutOS. `POST https://api.scoutos.com/world/{agent_id}/_interact` for streaming, `/_interact_sync` for sync.

**Valkey** — Redis-compatible in-memory data store. Used in Scout Live for caching/session state via managed DigitalOcean instance.

**Contacts App** — mini CRM at contacts.scoutos.live. Hono + Bun + MongoDB via Scout Ports. Features: contact CRUD, touch logging, tags, search.

**MCP (Model Context Protocol)** — protocol for AI agents to interact with external tools and data. Scout Live MCP server (planned) would wrap Scout SDK tools so any MCP-compatible agent can deploy apps on scoutos.live. Architecture: HTTP/SSE remote server, no NPM package needed.
