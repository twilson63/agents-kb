# MC — Lessons Learned

## Scout Live Data Port Auth
- Data ports require App JWT authentication (`Authorization: Bearer <jwt>`)
- The publish code stored in LMDB is SHA-256 hashed — can't recover plaintext
- App owners can regenerate publish codes via `POST /apps/:subdomain/regenerate-code`
- No app limit exists in code — accounts can deploy unlimited apps

## Port Path Consistency
- Internal pod callers access ports via sidecar at `http://127.0.0.1:3101/_ports/data/...`
- External callers should use `https://scoutos.live/_ports/data/...` with App JWT
- Both `/_ports/` and `/ports/` now work on the gateway (as of Apr 9, 2026)

## Gateway Memory & Liveness Probe Tuning
- 512Mi memory limit is too tight for Scout Live gateway under load
- Liveness probe with `context deadline exceeded` on `/api/health` causes kill cycle: start → serve 1-2 min → timeout → SIGTERM → restart
- Lesson: either increase memory limit, increase probe timeout/failure threshold, or investigate event loop blocking
- Pattern: pod restart count climbing = likely resource pressure, not app bug

## Kubernetes Operations
- Managed Kafka and OpenSearch each require 3 nodes minimum (broker quorum)
- Deleted both on Apr 2 to save ~$72/mo — not needed at current scale
- Gateway ReadWriteOnce PVC limits horizontal scaling

## Scout Live Template Build Pattern (Apr 6)
- Old templates used `CMD ["bun", "run", "src/index.ts"]` — runs TS directly, fragile
- If `src/` folder is missing from tarball or imports are complex, pod crashes with `Module not found`
- Fixed pattern: `RUN bun build src/index.ts --outdir=dist` then `CMD ["bun", "dist/index.js"]`
- Templates fixed in commits `0f44a5f` and `2efafdf`
- Also updated DESIGN_GUIDE.md with best practices
- Lesson: Always compile TypeScript in Dockerfile; never rely on runtime TS execution in containers

## MCP Server Research (Apr 6)
- Created comprehensive research doc: `scout-live/docs/MCP_SERVER_RESEARCH.md`
- Architecture: scouts.live (MCP server) → scoutos.live (REST API) — MCP is just another client
- No NPM package needed — just remote HTTP/SSE server
- Tools: deploy_template, list_apps, set_env, get_logs, etc.
- ~26 hours estimated implementation