# Today — 2026-04-21

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
- Apr 20 heartbeat: 4 restarts, last 30h ago — stable but fragile

## Alerts
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack)
- PR #2 (scout-live) open since Mar 7 (45+ days)

## Notes
- No daily memory file for Apr 21 yet (early morning compile)
- Last daily memory: Apr 20 (heartbeat check — PR #2 still open, social stale 16 days)
- No new decisions, patterns, or lessons since last compile