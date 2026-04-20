# Today — 2026-04-20

## Status Summary
- Scout Live: **Degraded** (gateway fragile — needs memory limit increase and probe tuning)
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org)
- HYPR: Live (onhyper.io)
- Hive: Active

## GitHub PAT
- Renewed Apr 13 (`mc-agent-pat-2026`), expires Jul 12, 2026
- Set reminder ~Jul 1 for next renewal

## Scout Live Gateway
- Still in degraded state since Apr 11 CrashLoopBackOff
- Root cause: 512Mi memory limit + aggressive liveness probe
- Needs: memory limit increase, probe timeout/threshold tuning
- Apr 19 heartbeat: 4 restarts, last 18h ago — stable but fragile

## Alerts
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack)
- PR #2 (scout-live) open since Mar 7 (43+ days)

## Notes
- No new daily memory files since Apr 19
- MCP server deployed at mcp-server.scoutos.live
- Social stale ~15+ days — needs human approval to resume