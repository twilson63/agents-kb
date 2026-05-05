# Today — 2026-05-05

## Status Summary
- Scout Live: **STABLE but liveness probe needs fix** — probe configuration too aggressive for ~30s startup, causes CrashLoopBackOff on every pod rotation
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org) — Ed25519 signed requests now required for API publishing
- HYPR: Live (onhyper.io)
- Hive: Active

## GitHub PAT
- Token: `mc-agent-pat-2026`, renewed Apr 13, expires Jul 12, 2026
- Reminder set ~Jul 1 for next renewal

## Scout Live Gateway
- **Root cause identified (May 4)**: Liveness probe is too aggressive for gateway's ~30s startup time
  - Current: `initialDelaySeconds:15`, `timeoutSeconds:1`, `failureThreshold:3`
  - Sandbox apps block event loop during startup → health checks time out → K8s kills pod → restart loop
  - **Fix needed**: `initialDelaySeconds:30`, `timeoutSeconds:10`, `periodSeconds:30` (or add separate `startupProbe`)
  - Every pod rotation triggers crash cycle without this fix
- Memory limit: 1Gi (bumped from 512Mi on May 1)
- SRE Agent cron running every 10min (model: glm-5:cloud)

## Recent Work (May 1)
- **Env var feature**: Build API now accepts `env` query param (JSON), auto-encrypts sensitive keys
- **Port Roadmap**: HARDENING_ROADMAP.md created — logs port → metrics → config/flags → llm → sql → auth
- **MCP Essay**: "The Case for MCP" written (Minto Pyramid), but zenbin publish blocked (needs Ed25519)
- **ScoutOS API Key**: Removed from gateway deployment (was burning through hyper org's free tier)
- **Logs port started**: spec.ts, router.ts, memory/redis-streams/posthog adapters in progress

## Alerts
- ⚠️ **Scout Live liveness probe needs patching** — causes CrashLoopBackOff on every pod rotation
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack) — 34+ days stale
- PR #2 (scout-live) open since Mar 7 (59+ days)
- 4 unpublished blog posts queued, blocked by content auth expiry
- Hono XSS + auth fixes committed locally but **not yet pushed**
- Zenbin API now requires Ed25519 signed requests — skill update needed