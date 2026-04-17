# Today — 2026-04-17

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

## Alerts
- Pipedrive CRM: paywall/billing issue blocking access

## Notes
- No new daily memory files since Apr 12
- Content engine social auth still expired (X/LinkedIn/Substack)
- MCP server deployed at mcp-server.scoutos.live