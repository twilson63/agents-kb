# Today — 2026-04-15

## Scout Live Gateway
- Gateway was in CrashLoopBackOff (detected Apr 11), partially recovered by Apr 12
- **Root cause**: 512Mi memory limit too tight + aggressive liveness probe
- **Status**: Running but fragile — needs memory limit increase and probe tuning
- Still on single K8s node after Apr 2 scale-down

## GitHub PAT Renewed
- New PAT `mc-agent-pat-2026` created Apr 13, expires Jul 12, 2026
- Stored in TOOLS.md — `gh` CLI and git push working again

## New Scout Live Apps (Apr 12+)
- app-builder, app-expense-splitter, app-habit-tracker, app-hivechat, app-scoutchat variants
- 14 app pods total, all running healthy (2/2)

## Alerts
- **Pipedrive CRM** — paywall/billing issue blocking access

## Status
- Scout Live: **Degraded** (gateway intermittent, needs tuning)
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org)
- HYPR: Live (onhyper.io)
- Hive: Active