# MC — Decisions

## 2026-04-08: Use agents-kb as second brain
- Decided to organize learnings into topic wikis instead of flat files
- Wiki structure: platform-engineering, agent-patterns, web-development, devops, business
- Daily cron at 4 AM EST to sync and push

## 2026-04-01: Removed HPA from Scout Live gateway
- ReadWriteOnce PVC prevents horizontal scaling — HPA tried to create 2nd replica, pod stuck in ContainerCreating
- Decision: single replica with no HPA; documented reason in k8s/gateway.yaml
- May revisit with ReadWriteMany PVC (NFS) or stateless gateway in future

## 2026-04-09: Port paths should be /_ports/ consistently
- Mounted port routers under both /_ports/ and /ports/ on gateway
- Internal pod callers use /_ports/data/... (sidecar proxy)
- External callers can now also use /_ports/data/... (was /ports/data/... only)
- This makes SDK and client code consistent regardless of where it runs

## 2026-05-01: ScoutOS API key removed from gateway
- Was burning through hyper org's free tier quota
- Agents adapter still registered but returns 401 without key
- onhyper.io ScoutOS proxy also needs key removed on Railway manually
- Decision: Remove the key entirely rather than rate-limit; free tier not sustainable for shared platform

## 2026-05-01: Port hardening roadmap priority order
- Created HARDENING_ROADMAP.md in scout-live repo
- Priority: logs port → metrics port → config/flags → llm → sql → auth
- Logs port started (spec, router, memory/redis-streams/posthog adapters)
- Removed hyper-micro adapter from blob and cache ports (deprecated)

## 2026-05-01: SRE Agent cron setup (every 10min, glm-5:cloud)
- Automated K8s cluster health monitoring: nodes, pods, gateway, resources
- Model changed from glm-4 (deprecated) to glm-5:cloud
- Reduces manual heartbeat checks for cluster health

## 2026-05-16: Marketing pivot from OnHyper to ZenBin
- Tom Wilson (twilson63) recommended shifting social marketing focus from OnHyper to ZenBin
- ZenBin now has agent payments via Stripe (Pro $4.99/mo, Enterprise $14.99/mo)
- Checkout sessions signed with agent's Ed25519 key; plans attach to signing key, not user account
- Article published: https://zenbin.org/p/zenbin-agent-payments
- Next step: X/LinkedIn intro posts about ZenBin agent payments

## 2026-05-18: Andrew Reza internship follow-up needed
- Andrew Reza (apreza2023@gmail.com) — junior at Georgia Tech, EE major, Mt Pleasant SC
- Referred by Tom Wilson via Ellen Wilson (April 4, 2026)
- Looking for local summer 2026 internship
- 6 weeks stale — needs prompt follow-up with Tom Wilson
- Pipedrive CRM still blocked by billing/paywall, can't add contact there

## 2026-06-19: LinkedIn engagement strategy — AI provider risk posts
- Commented on Abdur-Rub Atta Shahid's post about AI provider risk — highlighted LLM port pattern at OpenClaw
- Followed Abdur-Rub (Founder @ Beyond AI Cloud) — AI agents/scalable systems focus
- Embedded ZenBin promotion in all LinkedIn comments
- Pattern: When provider risk/lock-in topics appear, LLM port + OpenClaw agent boundary is the natural response

## 2026-04-14: GitHub PAT renewal needed → Completed
- Previous PAT (`ghp_x6pN...`) expired Apr 13, 2026
- New token created Apr 13, 2026 via browser automation (`mc-agent-pat-2026`)
- New PAT expires Jul 12, 2026 — set reminder ~Jul 1 for renewal
- Token stored in TOOLS.md