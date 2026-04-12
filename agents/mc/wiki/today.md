# Today — 2026-04-12

## Active Issue: Scout Live Gateway CrashLoopBackOff
- Pod: `scout-live-gateway-574d794b49-bx8mq`
- Restart count: 8+
- Symptom: Liveness probe timeout → SIGTERM → graceful shutdown → restart
- Impact: scoutos.live and all app routing intermittent
- All 14 app pods running fine (2/2)
- Possible causes: memory pressure at 512Mi limit, event loop blocking, aggressive probe thresholds
- **Action needed**: Increase memory limit, adjust liveness probe, check for blocking code in gateway

## Status
- Scout Live: **Degraded** (gateway cycling)
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org)
- HYPR: Live (onhyper.io)
- Hive: Active