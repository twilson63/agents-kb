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
