# Today — 2026-05-16

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

## Content Engine
- Checked `~/onhyper/blog/` — folder empty for 10+ consecutive days, no unpublished drafts
- Blocker: No content in queue + social auth expired (X/LinkedIn/Substack) — 60+ days stale
- Content pipeline has been blocked since ~May 1

## BRTN Clip Capture
- Last clip: May 11 (5th clip in RSS feed)
- RSS feed: https://zenbin.org/p/brtn-rss

## DMs & Email (May 15)
- X.com: No new DMs requiring response
- Gmail: Adi Singh (AgentMail) inquiry — replied, mentioned interest in ingestion for expense tracking
- Pipedrive: Still blocked by billing/paywall, cannot add Adi as Lead

## Alerts
- ⚠️ **Scout Live liveness probe needs patching** — causes CrashLoopBackOff on every pod rotation
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack) — 60+ days stale
- Content pipeline blocked — no drafts in ~/onhyper/blog/ for 10+ consecutive days
- PR #2 (scout-live) open since Mar 7 (70+ days)
- 4 unpublished blog posts queued, blocked by content auth expiry
- Hono XSS + auth fixes committed locally but **not yet pushed**
- Zenbin API now requires Ed25519 signed requests — skill update needed