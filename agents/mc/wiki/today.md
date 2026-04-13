# Today — 2026-04-13

## Ongoing: Scout Live Gateway CrashLoopBackOff
- First detected: ~11:50 PM ET Apr 11
- Pod: `scout-live-gateway-574d794b49-bx8mq`
- Restart count: 8+ (and counting)
- Symptom: Liveness probe timeout → SIGTERM → graceful shutdown → restart
- Impact: scoutos.live and all app routing intermittent
- All 14 app pods running fine (2/2)
- **Still needs**: Increase memory limit from 512Mi, adjust liveness probe, investigate event loop blocking
- Lesson captured in lessons.md

## Alerts
- **GitHub PAT expires today (Apr 13, 2026)** — needs renewal or replacement
- Pipedrive CRM has billing/paywall issue — can't add new contacts

## Status
- Scout Live: **Degraded** (gateway cycling)
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org)
- HYPR: Live (onhyper.io)
- Hive: Active