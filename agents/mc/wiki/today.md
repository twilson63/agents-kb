# Today — 2026-06-07

## Status Summary
- Scout Live: **STABLE but liveness probe needs fix** — probe configuration too aggressive for ~30s startup, causes CrashLoopBackOff on every pod rotation
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org) — Ed25519 signed requests now required for API publishing; **agent payments now live** (Stripe)
- HYPR: Live (onhyper.io)
- Hive: Active
- **PermaBrain (NEW)**: Public knowledge graph for people and agents — invited by Tom Wilson, write access accepted Jun 6
- GitHub PAT: expires Jul 12, 2026 — reminder ~Jul 1
- Model: ollama/glm-5.1:cloud

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

## Marketing Pivot
- **Decision (May 16)**: Pivot social marketing from OnHyper to ZenBin
- Tom Wilson (twilson63) recommended focusing on ZenBin agent payments feature
- Article published: https://zenbin.org/p/zenbin-agent-payments
- X/Twitter post published (May 17): https://x.com/hyperio_mc/status/2055942519024766996
- TODO: LinkedIn intro post still needed

## Content Engine
- Marketing focus shifted to ZenBin (from OnHyper)
- Article about ZenBin agent payments published to zenbin.org
- X/Twitter post published about ZenBin agent payments
- Jun 4: LinkedIn engagement — liked Tom Wilson's AI agent discovery post, commented with zenbin.org mention
- Jun 5-7: No new activity — all DM/email checks came back empty, no new engagements
- X account: **SUSPENDED (read-only)** — can like/comment but cannot post new tweets
- Blog folder on OnHyper is empty — no blog content published there
- Social auth still expired (X/LinkedIn/Substack) — 60+ days stale (browser automation used instead)
- Content pipeline has been blocked for direct social posting since ~May 1

## BRTN Clip Capture
- Last clip: May 11 (5th clip in RSS feed)
- RSS feed: https://zenbin.org/p/brtn-rss

## DMs & Email (Jun 6-7)
- X.com: No new DMs requiring response (Tom Wilson thread only, 11+ weeks old)
- Gmail: Requires re-authentication (password needed in openclaw browser)
- Pipedrive: Still blocked by billing/paywall
- No new business inquiries

## Alerts
- ⚠️ **X account SUSPENDED (read-only)** — can like/comment but cannot post new tweets
- ⚠️ **Scout Live liveness probe needs patching** — causes CrashLoopBackOff on every pod rotation
- ⚠️ **Gmail requires re-authentication** — password needed in openclaw browser
- ⚠️ **LinkedIn session expired** — needs re-login (since Jun 1)
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack) — 60+ days stale
- PR #2 (scout-live) open since Mar 7 (90+ days)
- Hono XSS + auth fixes committed locally but **not yet pushed**
- Zenbin API now requires Ed25519 signed requests — skill update needed
- OnHyper proxy error handlers leak `error.message` to API responses (task-020, May 16)
- Andrew Reza internship inquiry needs follow-up (~9 weeks stale since Apr 4)