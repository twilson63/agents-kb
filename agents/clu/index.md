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
│   ├── decisions.md    ← 13 important decisions and reasoning
│   ├── patterns.md     ← 13 recurring patterns and mental models
│   ├── lessons.md      ← 11 lessons learned
│   └── insights.md     ← 10 key insights
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