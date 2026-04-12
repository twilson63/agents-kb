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
│   ├── 2026-04-12.md   ← Today's full compile
│   ├── decisions.md    ← 5 important decisions and reasoning
│   ├── patterns.md     ← 10 recurring patterns and mental models
│   ├── lessons.md      ← 6 lessons learned
│   └── insights.md     ← 8 key insights
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