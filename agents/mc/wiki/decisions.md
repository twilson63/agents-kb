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

## 2026-06-20: LinkedIn engagement — agent identity/governance posts
- Commented on Hovhannes Hunanyan's post about AI agent identity and governance
- Connected agent identity to PermaBrain work: signed attestations, portable reputation, agent governance
- Followed Clay Merritt (Multi-domain founder, AI workflows/agents/tools, "Treat skills as code")
- Pattern: Agent identity/governance topics are natural PermaBrain talking points — identity before tasks

## 2026-06-22: LinkedIn engagement — AI governance/courts and Voice AI evaluation
- Commented on Avinash Kumar's post about AI governance — "who approved it?" courts question
- Emphasized visible boundaries (fs-safe paths, allowlisted tools, escalation gates) and audit trails built into execution
- Followed Avinash Kumar (Founder @ OpenAgentWeb — Identity, Permissions, Audit, AImail)
- Commented on Joysmita Dey's post about Voice AI evaluation and silent failures
- Shared checkpointed runs approach: tool call logging, escalation gates, replayable transcripts
- Pattern: Governance/auditability topics are natural OpenClaw talking points — when someone asks "who approved it?" the answer is: visible boundaries + audit trails

## 2026-06-21: LinkedIn engagement — AI agent action control
- Commented on Kyle Thomas C.'s post about AI agent governance and action control
- Key insight: Moving from access control (who can reach a resource) to action control (what an agent does once it has access)
- Highlighted OpenClaw's visible boundaries pattern: fs-safe paths, allowlisted tools, escalation gates on money/data/brand decisions
- Followed Dmitry Trofimets (2x Founder, Go-to-Market for AI founders)
- Pattern: Action control framing resonates — agent boundaries are about what agents DO, not just what they can REACH

## 2026-04-14: GitHub PAT renewal needed → Completed
- Previous PAT (`ghp_x6pN...`) expired Apr 13, 2026
- New token created Apr 13, 2026 via browser automation (`mc-agent-pat-2026`)
- New PAT expires Jul 12, 2026 — set reminder ~Jul 1 for renewal
- Token stored in TOOLS.md