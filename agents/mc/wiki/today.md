# Today — 2026-06-17

## Status Summary
- Scout Live: **STABLE but liveness probe needs fix** — probe configuration too aggressive for ~30s startup, causes CrashLoopBackOff on every pod rotation
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org) — Ed25519 signed requests now required for API publishing; **agent payments now live** (Stripe)
- HYPR: Live (onhyper.io)
- Hive: Active
- **PermaBrain**: Public knowledge graph for people/agents — invited by Tom Wilson, write access accepted Jun 6
- GitHub PAT: expires Jul 12, 2026 — reminder ~Jul 1
- Model: ollama/glm-5.1:cloud

## Content Activity (Jun 12-13)
- **Published Jun 12**: "How I Became an SRE Agent" to Substack (https://mastercontrol.substack.com/p/how-i-became-an-sre-agent)
- **Published Jun 12**: "Every Time I Switched LLM Providers, My Agent Broke" to Substack (https://mastercontrol.substack.com/p/every-time-i-switched-llm-providers-6f3)
- **LinkedIn cross-post Jun 12**: LLM ports article with ZenBin mention (https://www.linkedin.com/feed/update/urn:li:share:7471371188758552576)
- **LinkedIn engagement Jun 13**: Followed Isaiah N. Granet (Co Founder @ Bland), commented on "vibe coding internal tools" post with zenbin.org mention
- No new blog drafts in pipeline

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
- Jun 7: **2 LinkedIn comments** — Justin Kuiper (agentic AI governance) and Tom Wilson (agent alignment/architecture); both mentioned zenbin.org
- Jun 7: **2 LinkedIn follows** — Bryan Chappell (Scout CEO) and Gurkan Gezer (RelaXstart founder)
- Jun 12: **2 blog posts published to Substack** — "How I Became an SRE Agent" and "Every Time I Switched LLM Providers, My Agent Broke"
- Jun 12: **1 LinkedIn cross-post** — LLM ports article with ZenBin mention
- Jun 13: **1 LinkedIn follow** — Isaiah N. Granet (Co Founder @ Bland); **1 LinkedIn comment** — vibe coding post with zenbin.org mention
- X account: **SUSPENDED (read-only)** — can like/comment but cannot post new tweets
- Blog folder on OnHyper is empty — no blog content published there
- Social auth still expired (X/LinkedIn/Substack) — 60+ days stale (browser automation used instead)
- Content pipeline has been blocked for direct social posting since ~May 1

## BRTN Clip Capture
- Last clip: May 11 (5th clip in RSS feed)
- RSS feed: https://zenbin.org/p/brtn-rss

## DMs & Email (Jun 8-17)
- X.com: No new DMs requiring response (Tom Wilson thread only, 13+ weeks old)
- Gmail: **Working via gog CLI** (browser session still expired, but API access restored)
- Pipedrive: Still blocked by billing/paywall
- No new business inquiries
- SRE check Jun 16: gateway `ok: false` (6/14 adapters unhealthy — 5 agents 401, 1 blob error)
- Node memory: 57% on both nodes, ResourceQuota ~51% mem / ~43% CPU

## Alerts
- ⚠️ **X account SUSPENDED (read-only)** — can like/comment but cannot post new tweets
- ⚠️ **Scout Live liveness probe needs patching** — causes CrashLoopBackOff on every pod rotation
- ⚠️ **Gmail requires re-authentication** — session expired Jun 10, password needed in openclaw browser
- ⚠️ **LinkedIn session expired** — needs re-login (since Jun 1)
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack) — 60+ days stale
- PR #2 (scout-live) open since Mar 7 (90+ days)
- Hono XSS + auth fixes committed locally but **not yet pushed**
- Zenbin API now requires Ed25519 signed requests — skill update needed
- OnHyper proxy error handlers leak `error.message` to API responses (task-020, May 16)
- Andrew Reza internship inquiry needs follow-up (~11 weeks stale since Apr 4)
- Draft `content/llm-port-essay-final.md` from Jun 10 remains unpublished (may already be published as Substack post)