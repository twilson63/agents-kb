# MC — Memory Index

Master Control (MC) is the primary OpenClaw agent running for Rakis. Primary contact: Rakis.

## Quick Reference

- [Context & preferences](context.md)
- [Notes](notes/)

## What I Know

### Environment
- Running in OpenClaw (Mac mini, arm64)
- Node v24.13.1, model: ollama/glm-5.1:cloud
- Channel: Telegram
- Workspace: `~/.openclaw/workspace/`

### Active Projects

| Project | Status | Notes |
|---------|--------|-------|
| Scout Live | Active | K8s deployment platform for agents |
| Contacts App | Live | https://contacts.scoutos.live |
| ZChat | Live | Chat app at https://zchat.scoutos.live |
| zenbin | Live | Publishing platform at zenbin.org |
| Hive | Active | Agent-to-agent communication |
| HYPR (OnHyper) | Live | https://onhyper.io — API proxy platform |

### People

- **Rakis** — primary user, communicates via Telegram, prefers concise responses
- **scoutos-labs org** — collaborators (@twilson63, @dottie-weaver, @tnez, @bryanchappell, @sark1337)
- **Bryan Chappell** — ScoutOS co-founder, reached out Feb 2026, said "not interested at the moment" but door open
- **Wail Askia** — Aethelgard, Architect & Founder. Discussing Zero-Storage Architecture partnership. Missed Architecture Sync meeting Apr 3; reschedule pending.

### Key Learnings

- [Platform Engineering](notes/platform-engineering.md) — deployment, K8s, infrastructure
- [Agent Patterns](notes/agent-patterns.md) — how agents work, communicate, and build
- [Web Development](notes/web-development.md) — frontend, backend, and full-stack lessons
- [DevOps & Operations](notes/devops.md) — deployment, monitoring, debugging
- [Business & Marketing](notes/business.md) — sales, content, social media

## Session Log

### 2026-05-20
- Second brain compile — May 19-20 daily notes reviewed
- May 19: No new DMs or business inquiries; Pipedrive still blocked
- May 20: Empty daily note, no new events at 5 AM
- Andrew Reza internship inquiry now ~7 weeks stale (since Apr 4)
- No new decisions, patterns, or lessons to capture

### 2026-05-19
- Second brain compile — May 18 daily note reviewed
- Andrew Reza internship inquiry needs follow-up (6 weeks stale since Apr 4, referred by Tom/Ellen Wilson)
- Pipedrive CRM still blocked by billing — can't add Reza as contact
- No new DMs or business inquiries
- New decision captured: Andrew Reza follow-up needed

### 2026-05-18
- Second brain compile — May 17 daily note reviewed
- X/Twitter post published about ZenBin agent payments (URL: https://x.com/hyperio_mc/status/2055942519024766996)
- OnHyper blog folder empty, no Substack cross-post yet
- Pipedrive CRM still blocked by billing
- No new DMs or business inquiries
- No new decisions, patterns, or lessons to capture

### 2026-05-17
- Second brain compile — May 16-17 daily notes reviewed
- Marketing pivot: social focus shifting from OnHyper to ZenBin (Tom Wilson recommendation)
- ZenBin agent payments article published at https://zenbin.org/p/zenbin-agent-payments
- OnHyper code review found task-020: proxy error handlers leak internal error.message (medium severity)
- Pipedrive CRM still blocked by billing
- No new DMs or business inquiries
- New decision: marketing pivot to ZenBin
- New lesson: OnHyper proxy error message leak

### 2026-05-16
- Second brain compile — May 15 daily note reviewed (Adi Singh inquiry, PR #185 merged)
- Content pipeline blocked 10+ days, social auth 60+ days stale, PR #2 now 70+ days
- Pipedrive CRM still blocked by billing
- No new decisions, patterns, or lessons to capture

### 2026-05-15
- Second brain compile — May 15 daily note: Adi Singh (AgentMail) inquiry, replied with interest in ingestion
- PR #185 (hyper63/claws) merged — self-hosted local dev support with k3d
- Pipedrive CRM still blocked by billing — cannot add Adi Singh as Lead
- Content pipeline blocked 9+ days, social auth 59+ days stale, PR #2 now 69+ days
- BRTN: last clip May 11, RSS feed running
- No new decisions, patterns, or lessons to capture

### 2026-05-14
- Second brain compile — no new daily notes since May 11, status unchanged
- Status: content pipeline blocked 8+ days, social auth 58+ days stale, PR #2 now 68+ days
- BRTN: last clip May 11, RSS feed running
- No new decisions, patterns, or lessons to capture

### 2026-05-13
- Second brain compile — no new daily notes since May 11
- Status: content pipeline blocked 6+ days, social auth 53+ days stale, PR #2 now 67+ days
- BRTN: last clip May 11, RSS feed running
- Fixed context.md Node version (v25.6.1 → v24.13.1)
- No new decisions, patterns, or lessons to capture

### 2026-05-12
- Second brain compile — no new daily notes since May 11, status unchanged
- BRTN: last clip captured May 11 (5th in RSS), automated pipeline running
- Content pipeline: blocked 5+ consecutive days, social auth 50+ days stale
- PR #2 now 66+ days open
- No new decisions, patterns, or lessons to capture

### 2026-05-11
- Second brain compile — May 11 daily note: BRTN clip captured (5th clip in RSS), published to zenbin
- Updated today.md: content pipeline 4+ days blocked, PR #2 now 65+ days
- No new decisions, patterns, or lessons to capture

### 2026-05-10
- Second brain compile — May 10 daily note: content engine still blocked (empty blog folder), social auth 50+ days stale
- Updated today.md: content pipeline blocked 3+ days, social auth 50+ days, PR #2 64+ days
- No new decisions, patterns, or lessons to capture

### 2026-05-09
- Second brain compile — no new daily notes since May 8, status unchanged
- Updated today.md: social auth stale 49+ days, PR #2 now 63+ days
- No new decisions, patterns, or lessons to capture

### 2026-05-08
- Second brain compile — May 8 daily note: content engine ran but blog folder empty, social auth 48+ days stale
- Updated today.md: social auth stale count bumped, content engine status section added
- No new decisions, patterns, or lessons to capture

### 2026-05-07
- Second brain compile — no new daily notes since May 4
- Updated today.md: PR #2 now 61+ days open, social auth 47+ days stale
- No new decisions, patterns, or lessons to capture

### 2026-05-06
- Second brain compile — no new daily notes since May 4
- Updated today.md: PR #2 now 60+ days open, social auth 36+ days stale
- No new decisions, patterns, or lessons to capture

### 2026-05-05
- Second brain compile — captured May 4 daily note (liveness probe root cause)
- New lesson: Scout Live gateway liveness probe too aggressive for ~30s startup, causes CrashLoopBackOff on every pod rotation
- Updated today.md: probe fix needed, PR #2 59+ days, social auth 34+ days stale
- No new decisions or patterns

### 2026-05-04
- Second brain compile — no new daily notes since May 1, status unchanged
- Updated today.md: PR #2 now 58+ days open, social auth stale 30+ days
- No new decisions, patterns, or lessons to capture

### 2026-05-03
- Second brain compile — no new daily notes since May 1, status unchanged
- Updated today.md: PR #2 now 57+ days open, social auth stale 30+ days
- No new decisions, patterns, or lessons to capture

### 2026-05-02
- Second brain compile — captured May 1 daily note (significant cluster ops day)
- New decisions: ScoutOS API key removed, port hardening roadmap, SRE cron setup
- New patterns: Env var injection pattern for Scout Live deploys
- New lessons: gateway fix (memory→1Gi), env var feature, zenbin Ed25519 auth change, ScoutOS quota management
- Gateway now stable with SRE monitoring; 25 orphaned services cleaned
- Port hardening roadmap created (logs→metrics→config→llm→sql→auth)

### 2026-05-01
- Second brain compile — no new daily notes since Apr 26, status unchanged
- Updated today.md: PR #2 now 55+ days open, all alerts persist
- No new decisions, patterns, or lessons to capture

### 2026-04-30
- Second brain compile — no new daily notes since Apr 26, status unchanged
- Updated today.md: PR #2 now 54+ days open, all alerts persist
- No new decisions, patterns, or lessons to capture

### 2026-04-28
- Second brain compile — Apr 26 daily note captured: Hono XSS fix (v4.12.14) + auth config fix
- Both fixes committed locally but not yet pushed
- Updated today.md: PR #2 now 52+ days open, all alerts persist
- No new decisions, patterns, or lessons to capture

### 2026-04-26
- Second brain compile — no new daily notes since Apr 21, status unchanged
- Updated today.md: PR #2 now 50+ days open
- Gateway still fragile, content auth still expired (all 3 platforms)
- No new decisions, patterns, or lessons to capture

### 2026-04-25
- Second brain compile — no new daily notes since Apr 21, status unchanged
- Updated today.md date to 2026-04-25, PR #2 now 49+ days open
- Gateway still fragile, content auth still expired (all 3 platforms)
- No new decisions, patterns, or lessons to capture

### 2026-04-24
- Second brain compile — no new daily notes since Apr 21, status unchanged
- Updated today.md date to 2026-04-24, PR #2 now 48+ days open
- Gateway still fragile, content auth still expired (all 3 platforms)
- No new decisions, patterns, or lessons to capture

### 2026-04-23
- Second brain compile — no new daily notes since Apr 21, status unchanged
- Updated today.md: PR #2 now 47+ days open, all alerts persist
- Gateway still fragile, content auth still expired (all 3 platforms)
- No new decisions, patterns, or lessons to capture

### 2026-04-22
- Second brain compile — no new daily notes since Apr 21
- Updated today.md: content auth alert refined (all 3 platforms expired), 4 blog posts queued
- Gateway still fragile, PR #2 open 46+ days, social stale 18+ days
- No new decisions, patterns, or lessons to capture

### 2026-04-21
- Second brain compile — daily note: content engine fully blocked (all platform sessions expired)
- 4 unpublished posts queued, social stale 16+ days
- Gateway still fragile (4 restarts, last 30h ago)
- PR #2 open 45+ days
- No new decisions, patterns, or lessons to capture

### 2026-04-20
- Second brain compile — no new daily notes since Apr 19, status unchanged
- Gateway still fragile (4 restarts, last 18h ago at check time)
- PR #2 open 43+ days; social stale 15+ days
- No new decisions, patterns, or lessons to capture

### 2026-04-19
- Second brain compile — no new daily notes since Apr 12, status unchanged
- Gateway still degraded, content auth still blocked
- No new decisions, patterns, or lessons to capture

### 2026-04-18
- Second brain compile — no new daily notes since Apr 12, status unchanged
- Gateway still degraded, content auth still blocked
- No new decisions, patterns, or lessons to capture

### 2026-04-17
- Second brain compile — no new daily notes since Apr 12, status unchanged
- Updated today.md date to 2026-04-17
- Gateway still degraded, MCP server live, content auth still blocked

### 2026-04-16
- Second brain compile — no new daily notes since Apr 12, status unchanged
- Scout Live gateway still degraded, needs memory/probe tuning
- GitHub PAT renewed and working (expires Jul 12, 2026)
- No new decisions, patterns, or lessons to capture

### 2026-04-15
- Second brain compile — GitHub PAT renewal confirmed (new token expires Jul 12, 2026)
- Gateway still fragile, needs memory/probe tuning
- Pipedrive CRM blocked by paywall issue

### 2026-04-14
- Second brain compile — GitHub PAT expired, flagged for renewal
- Gateway CrashLoopBackOff partially resolved (was running at check time, still fragile)
- New Scout Live apps appeared: app-builder, app-expense-splitter, app-habit-tracker, app-hivechat, app-scoutchat variants
- DM/email check: no new inquiries, Tom Wilson thread still awaits reply
- Captured lesson: GitHub PATs expire silently — track proactively

### 2026-04-13
- Second brain compile — gateway CrashLoopBackOff still unresolved
- GitHub PAT expires today (Apr 13, 2026) — flagged for renewal
- Captured lesson: Scout Live template build pattern (compile TS in Dockerfile)
- Captured lesson: MCP server research doc created for Scout Live

### 2026-04-12
- Scout Live gateway CrashLoopBackOff — 512Mi memory limit too tight, liveness probe killing pod
- Captured lesson: gateway needs resource/probe tuning

### 2026-04-08
- Set up agents-kb as second brain with wiki structure
- Created daily cron at 4 AM EST to sync and organize memories

### 2026-04-05
- Added hasVideo to trackPageCreated type in zenbin
- Updated zenbin skill.md with video documentation
- Created PR for zenbin video support

### 2026-04-02
- Scaled down Scout Live from 3 K8s nodes to 1 (cost savings ~$72/mo)
- Deleted managed Kafka (scout-live-queue) and OpenSearch (scout-live-search)
- Removed Kafka/OpenSearch credentials from K8s secrets
- Fixed zenbin TypeScript error for hasVideo property

### 2026-04-01
- Created March 2026 invoice (FOR-invoice-026.docx)
- Published April Fools 2026 blog to zenbin.org with hyperlinks
- Fixed JWT verification bug in contacts app
- Built and pushed Docker image contacts-app:v1.1.2