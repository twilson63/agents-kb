# Today — 2026-06-19

## Status Summary
- Scout Live: **STABLE but gateway unhealthy** — 6/14 adapters down (5 agents 401, 1 blob error); liveness probe still needs fix
- Contacts App: Live (contacts.scoutos.live)
- ZChat: Live (zchat.scoutos.live)
- zenbin: Live (zenbin.org) — Ed25519 signed requests required for API publishing; **agent payments live** (Stripe)
- HYPR: Live (onhyper.io)
- Hive: Active
- **PermaBrain**: Public knowledge graph for people/agents — invited by Tom Wilson, write access accepted Jun 6
- GitHub PAT: expires Jul 12, 2026 — reminder ~Jul 1
- Model: ollama/glm-5.1:cloud

## Content Activity (Jun 12-19)
- **Published Jun 12**: "How I Became an SRE Agent" to Substack (https://mastercontrol.substack.com/p/how-i-became-an-sre-agent)
- **Published Jun 12**: "Every Time I Switched LLM Providers, My Agent Broke" to Substack (https://mastercontrol.substack.com/p/every-time-i-switched-llm-providers-6f3)
- **LinkedIn cross-post Jun 12**: LLM ports article with ZenBin mention
- **LinkedIn Jun 18 AM**: Commented on Paul Goldman's post about Canada's sovereign AI stack — highlighted hyper.io's control infrastructure
- **LinkedIn Jun 18 AM**: Commented on Matthew Elwell's post about LaunchDarkly pricing — drew parallel to OpenClaw agent architecture
- **LinkedIn Jun 19 AM**: Commented on Abdur-Rub Atta Shahid's post about AI provider risk — LLM port pattern insight + ZenBin mention
- **LinkedIn Jun 19 AM**: Followed Abdur-Rub Atta Shahid (Founder @ Beyond AI Cloud)
- No new blog drafts in pipeline

## GitHub PAT
- Token: `mc-agent-pat-2026`, renewed Apr 13, expires Jul 12, 2026
- Reminder set ~Jul 1 for next renewal

## Scout Live Gateway
- **Root cause identified (May 4)**: Liveness probe is too aggressive for gateway's ~30s startup time
  - Current: `initialDelaySeconds:15`, `timeoutSeconds:1`, `failureThreshold:3`
  - **Fix needed**: `initialDelaySeconds:30`, `timeoutSeconds:10`, `periodSeconds:30` (or add separate `startupProbe`)
  - Every pod rotation triggers crash cycle without this fix
- Memory limit: 1Gi (bumped from 512Mi on May 1)
- SRE Agent cron running every 10min (model: glm-5:cloud)
- **Jun 16 SRE check**: gateway `ok: false` — 6/14 adapters unhealthy (5 agents 401, 1 blob error)
- **Jun 16 node status**: Memory 57% on both nodes, ResourceQuota ~51% mem / ~43% CPU

## Marketing Pivot
- **Decision (May 16)**: Pivot social marketing from OnHyper to ZenBin
- Tom Wilson (twilson63) recommended focusing on ZenBin agent payments feature
- Article published: https://zenbin.org/p/zenbin-agent-payments
- X/Twitter post published (May 17): https://x.com/hyperio_mc/status/2055942519024766996
- LinkedIn intro post still needed

## Content Engine
- Marketing focus on ZenBin (from OnHyper)
- Jun 18-19: LinkedIn engagement active — 3 comments on AI/provider/architecture posts
- X account: **SUSPENDED (read-only)** — can like/comment but cannot post new tweets
- LinkedIn session expired (since Jun 1) — PM session failed, needs re-login
- Gmail: API works via gog CLI, browser session expired
- Blog folder on OnHyper is empty — no new blog content
- No new business inquiries across all checks (Jun 17-19)

## DMs & Email (Jun 17-19)
- X.com: No new DMs requiring response (Tom Wilson thread only, 13+ weeks old)
- Gmail: Working via gog CLI (browser session expired)
- Pipedrive: Still blocked by billing/paywall
- No new business inquiries across all checks

## Alerts
- ⚠️ **X account SUSPENDED (read-only)** — can like/comment but cannot post new tweets
- ⚠️ **Scout Live liveness probe needs patching** — causes CrashLoopBackOff on every pod rotation
- ⚠️ **Scout Live gateway unhealthy** (Jun 16) — 6/14 adapters down (5 agents 401, 1 blob error)
- ⚠️ **Gmail browser session expired** — API access works via gog CLI
- ⚠️ **LinkedIn session expired** — needs re-login (since Jun 1)
- Pipedrive CRM: paywall/billing issue blocking access
- Content engine social auth still expired (X/LinkedIn/Substack) — 60+ days stale
- PR #2 (scout-live) open since Mar 7 (90+ days)
- Hono XSS + auth fixes committed locally but **not yet pushed**
- Zenbin API now requires Ed25519 signed requests — skill update needed
- OnHyper proxy error handlers leak `error.message` to API responses (task-020, May 16)
- Andrew Reza internship inquiry needs follow-up (~12 weeks stale since Apr 4)
- Draft `content/llm-port-essay-final.md` from Jun 10 remains unpublished (may already be published as Substack post)