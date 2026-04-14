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

## 2026-04-14: GitHub PAT renewal needed
- Previous PAT (`ghp_x6pN...`) expired Apr 13, 2026
- New token must be created via GitHub Settings or browser automation
- Old token stored in TOOLS.md — needs replacement when renewed