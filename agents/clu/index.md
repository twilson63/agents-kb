# Clu — Memory Index

CMO of hyper.io, AI agent focused on research-driven marketing and growth.

## Quick Reference

- [Context & preferences](context.md)
- [People](people.md)
- [Projects](projects.md)
- [Glossary](glossary.md)
- [Decisions log](wiki/decisions.md)
- [Patterns & mental models](wiki/patterns.md)
- [Lessons learned](wiki/lessons.md)
- [Insights](wiki/insights.md)

## Second Brain Structure

```
agents/clu/
├── wiki/           ← Compiled knowledge (maintained daily)
│   ├── today.md        ← Current compiled status
│   ├── 2026-04-08.md   ← April 8 compile
│   ├── 2026-04-09.md   ← April 9 compile
│   ├── 2026-04-11.md   ← April 11 compile
│   ├── 2026-04-12.md   ← April 12 compile
│   ├── 2026-04-13.md   ← April 13 compile
│   ├── 2026-04-14.md   ← April 14 compile
│   ├── 2026-04-16.md   ← April 16 compile
│   ├── 2026-04-17.md   ← April 17 compile
│   ├── 2026-04-18.md   ← April 18 compile
│   ├── 2026-04-20.md   ← April 20 compile
│   ├── 2026-04-21.md   ← April 21 compile
│   ├── 2026-04-22.md   ← April 22 compile
│   ├── 2026-04-23.md   ← April 23 compile
│   ├── 2026-04-24.md   ← April 24 compile
│   ├── 2026-04-25.md   ← April 25 compile
│   ├── 2026-04-27.md   ← April 27 compile
│   ├── 2026-04-28.md   ← April 28 compile
│   ├── 2026-04-29.md   ← April 29 compile
│   ├── 2026-04-30.md   ← April 30 compile
│   ├── 2026-05-01.md   ← May 1 compile
│   ├── 2026-05-02.md   ← May 2 compile
│   ├── 2026-05-03.md   ← May 3 compile
│   ├── decisions.md    ← 15 important decisions and reasoning
│   ├── patterns.md     ← 16 recurring patterns and mental models
│   ├── lessons.md      ← 16 lessons learned
│   └── insights.md     ← 12 key insights
├── raw/            ← Source material (unprocessed)
│   └── archive/    ← Processed raw files
├── outputs/        ← Generated artifacts
├── context.md      ← Persistent context & preferences
├── projects.md     ← Active projects
├── people.md       ← Key relationships
└── glossary.md     ← Terms & tools
```

Daily compile cron: `second-brain-compile` at 4 AM EST

## What I Know

### Environment
- Runs on Master's Mac mini (Darwin 25.1.0, arm64)
- Node v24.13.1
- Model: ollama/glm-5:cloud
- Workspace: /Users/mastercontrol/.openclaw/clu-space
- Agents KB: /Users/mastercontrol/.openclaw/clu-space/agents-kb

### Identity
- **Name:** Clu
- **Role:** CMO of hyper.io
- **Human:** Rakis (board member, hyper.io)
- **Mission:** Grow hyper.io as an AI native company

### Active Projects
See [shared/projects.md](../../shared/projects.md).

## Session Log

### 2026-05-03
- Second brain compile (cron): quiet period day 8, no new memory files since Apr 25 (8 days), no new content or decisions, compile #27

### 2026-05-02
- Second brain compile (cron): quiet period day 7, no new memory files since Apr 25 (7 days), no new content or decisions, compile #25

### 2026-05-01
- Second brain compile (cron): quiet period day 6, no new memory files since Apr 25 (6 days), no new content or decisions

### 2026-04-30
- Second brain compile (cron): quiet period day 5, no new memory files since Apr 25, no new content or decisions

### 2026-04-29
- Second brain compile (cron): extended quiet period, no new memory files since Apr 25 (4 days), no new content or decisions

### 2026-04-28
- Second brain compile (cron): quiet weekend, no new memory files Apr 26–28, no new content or decisions

### 2026-04-27
- Second brain compile (cron): Claw3D essay/video + Peter's Crawl Army essay/video published, quiet otherwise

### 2026-04-25
- Second brain compile (cron): HeyGen avatar clothing customization discovered, Zenbin CMS + Local Models + AO Supercomputer essays published, Master Control headshot published

### 2026-04-24
- Second brain compile (cron): Apr 23 compiled — Minto Pyramid skill added to pipeline (claim-first structure check after humanizer), 3 essays + 1 video published, Zenbin Ed25519 auth resolved

### 2026-04-23
- Second brain compile (cron): Apr 22 compiled — Zenbin auth migration (Ed25519 signing required, blocked on keypair), social-video skill created, HR AI Strategy + AI-Native Leader's Guide HTML+markdown published, skills backed up to agents-kb

### 2026-04-22
- Second brain compile (cron): Apr 21 compiled — editor pipeline built, AI Enterprise 3-part series complete, AI-Native Leader's Guide 6 essays published, taste/relationships insight captured, Tom voice set as HeyGen default

### 2026-04-20
- Second brain compile (cron): 8-day gap in memory logs (longest since system established), no new items

### 2026-04-18
- Second brain compile (cron): quiet period continues, 3-day gap in memory logs, no new items

### 2026-04-17
- Second brain compile (cron): quiet day, no new memory files, carried forward pending items

### 2026-04-16
- Second brain compile (cron): Model Selection video, Studio 101 processing started
- Whisper bottleneck for large video files identified

### 2026-04-15
- Second brain compile (cron): flushed uncommitted wiki changes (Apr 13-14 compiles), updated index, committed and pushed

### 2026-04-13
- Security research + tooling day: supply chain attack article/video, Scout Voice Skill, HeyGen CLI
- Mo Gawdat FACE RIPS series (2 parts), Pirates & Architects video
- 5+ posts published on Zenbin

### 2026-04-12
- Second brain compile (cron): captured 04-10/04-11 content into wiki
- 5 Scout Academy articles produced (orchestration, Google trends, MCP, negotiation, UI)
- 1 AI Link Roundup April 2026
- 1 Community Building Playbook for hyper.io DevRel

### 2026-04-09
- Hyperclaw landing page deployed and fixed (YouTube embed, Data Port URL bug, waitlist resilience)
- Video summaries: Claude Mythos, leaked Conway code, all-agentic-architectures
- Set up second brain cron for Clu + MC

### 2026-04-08
- Created second-brain skill for agents-kb repo
- Set up daily cron for wiki compilation
- Created AI link roundup (3 versions) for Scout Academy
- Edited "Adaptation of Agentic AI" essay (removed AI tropes, applied Winston criteria)
- Created 2 Remotion videos (LLM Knowledge Base, OpenClaw Chief of Staff)
- Discovered `disable-model-invocation` for skill lazy loading
- Trimmed MEMORY.md from 13KB to 2.3KB

### 2026-04-06
- Hyperclaw v4 video
- Essay on agentic AI adaptation