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