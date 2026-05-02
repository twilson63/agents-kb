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

## Hono XSS Vulnerability (Apr 26)
- Hono `^4.12.0` had an XSS vulnerability — patched in `^4.12.14`
- Bumped dependency in Scout Live, lint and TS compilation pass
- Lesson: Keep dependencies updated; even mature frameworks can have security patches in minor versions

## GitHub PAT Expiry
- PATs expire silently — no advance warning from GitHub
- Set calendar reminders 1-2 weeks before expiry
- Expired tokens cause `gh` CLI auth failures and push failures
- Lesson: Track token expiry dates proactively

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

## Scout Live Gateway Fix (May 1)
- Increasing memory limit from 512Mi → 1Gi resolved CrashLoopBackOff
- Also: reduced CPU limits on app containers (500m→200m) and Kaniko builder (2CPU→1CPU)
- Cleaned up 25 orphaned test app services that were consuming resources
- Lesson: ResourceQuota creep from orphaned resources is a silent killer — periodically audit

## Env Var Feature (May 1)
- Build API now accepts env vars at deploy time via `env` query param (JSON object)
- Sensitive key names (containing "key", "secret", "token", "password") auto-encrypted in vault
- Crash diagnostics now detect missing env vars and surface hints
- Lesson: Env var injection should happen at build/deploy time, not as a separate step

## Zenbin Ed25519 Auth Change (May 1)
- Zenbin API now requires Ed25519 signed requests for publishing
- Blocked "The Case for MCP" essay from being published directly
- Lesson: API auth changes can silently break agent workflows — need skill updates when APIs change requirements

## SCP API Key Quota Management (May 1)
- ScoutOS API key was burning through hyper org's free tier (200 agent messages, 50 workflow runs/month)
- Removed key entirely rather than trying to rate-limit — free tier not sustainable for shared platform use
- Lesson: Shared platform API keys on free tiers will exhaust quickly; either upgrade or remove

## MCP Server Research (Apr 6)
- Created comprehensive research doc: `scout-live/docs/MCP_SERVER_RESEARCH.md`
- Architecture: scouts.live (MCP server) → scoutos.live (REST API) — MCP is just another client
- No NPM package needed — just remote HTTP/SSE server
- Tools: deploy_template, list_apps, set_env, get_logs, etc.
- ~26 hours estimated implementation