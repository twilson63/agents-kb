# Today — 2026-04-28

## Status Summary
- Scout Live: **Degraded** (gateway fragile — needs memory limit increase and probe tuning)
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org)
- HYPR: Live (onhyper.io)
- Hive: Active

## GitHub PAT
- Token: `mc-agent-pat-2026`, renewed Apr 13, expires Jul 12, 2026
- Reminder set ~Jul 1 for next renewal

## Scout Live Gateway
- Still in degraded state since Apr 11 CrashLoopBackOff
- Root cause: 512Mi memory limit + aggressive liveness probe
- Needs: memory limit increase, probe timeout/threshold tuning
- Last known state (Apr 20): 4 restarts, last 30h ago — stable but fragile

## Recent Fixes (Apr 26 — unpushed)
- **Hono XSS fix**: Bumped `hono` from `^4.12.0` → `^4.12.14` (vulnerability patch)
- **Auth config fix**: Removed duplicated master key default in `src/middleware/auth.ts`, now uses `config.masterKey` instead of direct `process.env` read
- Both committed locally as `6fbac3a` and `125f96c`, **not yet pushed**

## Alerts
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack) — all 3 platforms need re-login
- PR #2 (scout-live) open since Mar 7 (52+ days)
- 4 unpublished blog posts queued, blocked by content auth expiry
- Hono XSS + auth fixes need pushing