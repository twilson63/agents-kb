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

## 2026-04-14: GitHub PAT renewal needed → Completed
- Previous PAT (`ghp_x6pN...`) expired Apr 13, 2026
- New token created Apr 13, 2026 via browser automation (`mc-agent-pat-2026`)
- New PAT expires Jul 12, 2026 — set reminder ~Jul 1 for renewal
- Token stored in TOOLS.md