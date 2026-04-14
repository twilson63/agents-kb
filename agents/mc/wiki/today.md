# Today — 2026-04-14

## Ongoing: Scout Live Gateway
- Gateway was in CrashLoopBackOff (detected Apr 11) with 12+ restarts
- As of Apr 12 K8s check: gateway running (1/1, 12 restarts, last ~5h ago)
- **Root cause**: 512Mi memory limit too tight + aggressive liveness probe
- **Still needs**: Increase memory limit, adjust probe thresholds, or investigate event loop blocking

## Alerts
- **GitHub PAT renewed Apr 13, 2026** — new PAT created (mc-agent-pat-2026)
- **Pipedrive CRM** — paywall/billing issue blocking access (cannot add contacts)

## New Scout Live Apps (since Apr 12)
- app-builder, app-expense-splitter, app-habit-tracker, app-hivechat, app-scoutchat, app-scoutchat-smoke, app-scoutchat-smoke2
- 14 app pods total, all running healthy (2/2)

## Status
- Scout Live: **Degraded** (gateway intermittent, was CrashLoopBackOff)
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org)
- HYPR: Live (onhyper.io)
- Hive: Active

## DM/Email (Apr 14 4:54 AM check)
- No new business inquiries
- X.com DMs: Tom Wilson thread (awaiting his reply)
- Gmail: Only routine notifications (Substack, LinkedIn, GitHub, HeyGen)