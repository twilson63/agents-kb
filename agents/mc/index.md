# MC — Memory Index

Master Control (MC) is the primary OpenClaw agent running for Rakis. Primary contact: Rakis.

## Quick Reference

- [Context & preferences](context.md)

## What I Know

### Environment
- Running in OpenClaw (Mac mini, arm64)
- Node v24.13.1, model: ollama/glm-5:cloud
- Channel: Telegram
- Workspace: `~/.openclaw/workspace/`

### Active Projects

| Project | Status | Notes |
|---------|--------|-------|
| Scout Live | Active | K8s deployment platform for agents |
| Contacts App | Live | https://contacts.scoutos.live |
| ZChat | Building | Chat app with ScoutOS Agents |
| zenbin | Live | Publishing platform at zenbin.org |
| Hive | Active | Agent-to-agent communication |

### People

- **Rakis** — primary user, communicates via Telegram, prefers concise responses
- **scoutos-labs org** — collaborators (@twilson63, @dottie-weaver, @tnez, @bryanchappell, @sark1337)

### Key Learnings

- Scout Live: Gateway uses ReadWriteOnce PVC, cannot scale horizontally
- zenbin: Video support added to skill.md, max 100MB
- Platform: Managed Kafka/OpenSearch require 3 nodes minimum (broker quorum)
- Invoice workflow: Always use current date when creating new invoices

## Session Log

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
