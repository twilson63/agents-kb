# Today — 2026-05-04

## Status Summary
- Scout Live: **Stable with SRE monitoring** (gateway memory bumped to 1Gi, orphaned services cleaned, SRE cron running every 10min)
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org) — Ed25519 signed requests now required for API publishing
- HYPR: Live (onhyper.io)
- Hive: Active

## GitHub PAT
- Token: `mc-agent-pat-2026`, renewed Apr 13, expires Jul 12, 2026
- Reminder set ~Jul 1 for next renewal

## Scout Live Gateway
- **Resolved** (as of May 1): Memory limit increased from 512Mi → 1Gi
- Orphaned services cleaned (25 old test app services deleted)
- SRE Agent cron running every 10min (model: glm-5:cloud)
- CPU limits reduced: app containers 500m→200m, Kaniko builder 2CPU→1CPU

## Recent Work (May 1)
- **Env var feature**: Build API now accepts `env` query param (JSON), auto-encrypts sensitive keys
- **Port Roadmap**: HARDENING_ROADMAP.md created — logs port → metrics → config/flags → llm → sql → auth
- **MCP Essay**: "The Case for MCP" written (Minto Pyramid), but zenbin publish blocked (needs Ed25519)
- **ScoutOS API Key**: Removed from gateway deployment (was burning through hyper org's free tier)
- **Logs port started**: spec.ts, router.ts, memory/redis-streams/posthog adapters in progress

## Alerts
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack) — all 3 platforms need re-login (30+ days stale)
- PR #2 (scout-live) open since Mar 7 (58+ days)
- 4 unpublished blog posts queued, blocked by content auth expiry
- Hono XSS + auth fixes committed locally but **not yet pushed**
- Zenbin API now requires Ed25519 signed requests — skill update needed