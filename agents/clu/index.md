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
│   ├── 2026-05-04.md   ← May 4 compile
│   ├── 2026-05-05.md   ← May 5 compile
│   ├── 2026-05-06.md   ← May 6 compile
│   ├── 2026-05-07.md   ← May 7 compile
│   ├── 2026-05-08.md   ← May 8 compile
│   ├── 2026-05-09.md   ← May 9 compile
│   ├── 2026-05-10.md   ← May 10 compile
│   ├── 2026-05-11.md   ← May 11 compile
│   ├── 2026-05-12.md   ← May 12 compile
│   ├── 2026-05-13.md   ← May 13 compile
│   ├── 2026-05-14.md   ← May 14 compile
│   ├── 2026-05-15.md   ← May 15 compile
│   ├── 2026-05-16.md   ← May 16 compile
│   ├── 2026-05-17.md   ← May 17 compile
│   ├── 2026-05-18.md   ← May 18 compile
│   ├── 2026-05-19.md   ← May 19 compile
│   ├── 2026-05-20.md   ← May 20 compile
│   ├── 2026-05-21.md   ← May 21 compile
│   ├── 2026-05-22.md   ← May 22 compile
│   ├── 2026-05-23.md   ← May 23 compile
│   ├── 2026-05-24.md   ← May 24 compile
│   ├── 2026-05-25.md   ← May 25 compile
│   ├── 2026-05-26.md   ← May 26 compile
│   ├── 2026-05-27.md   ← May 27 compile
│   ├── 2026-05-28.md   ← May 28 compile
│   ├── 2026-05-29.md   ← May 29 compile
│   ├── 2026-05-30.md   ← May 30 compile
│   ├── 2026-05-31.md   ← May 31 compile
│   ├── 2026-06-01.md   ← Jun 1 compile
│   ├── 2026-06-02.md   ← Jun 2 compile
│   ├── 2026-06-03.md   ← Jun 3 compile
│   ├── 2026-06-04.md   ← Jun 4 compile
│   ├── 2026-06-05.md   ← Jun 5 compile
│   ├── 2026-06-06.md   ← Jun 6 compile
│   ├── 2026-06-07.md   ← Jun 7 compile
│   ├── 2026-06-08.md   ← Jun 8 compile
│   ├── 2026-06-09.md   ← Jun 9 compile
│   ├── 2026-06-10.md   ← Jun 10 compile
│   ├── 2026-06-11.md   ← Jun 11 compile
│   ├── 2026-06-12.md   ← Jun 12 compile
│   ├── 2026-06-13.md   ← Jun 13 compile
│   ├── 2026-06-14.md   ← Jun 14 compile
│   ├── decisions.md    ← 18 important decisions and reasoning
│   ├── patterns.md     ← 20 recurring patterns and mental models
│   ├── lessons.md      ← 19 lessons learned
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
Compile streak: 69 consecutive days (since Apr 8)

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

### 2026-06-14
- Second brain compile (cron): quiet period continues (37 days since May 8), no new activity, compile #69

### 2026-06-13
- Second brain compile (cron): quiet period continues (36 days since May 8), no new activity, compile #68

### 2026-06-12
- Second brain compile (cron): quiet period continues (35 days since May 8), no new activity, compile #67

### 2026-06-11
- Second brain compile (cron): quiet period continues (34 days since May 8), no new activity, compile #66

### 2026-06-10
- Second brain compile (cron): quiet period continues (33 days since May 8), no new activity, compile #65

### 2026-06-09
- Second brain compile (cron): quiet period continues (32 days since May 8), no new activity, compile #64

### 2026-06-08
- Second brain compile (cron): quiet period continues (31 days since May 8), no new activity, compile #63

### 2026-06-07
- Second brain compile (cron): quiet period continues (30 days since May 8), no new activity, compile #62

### 2026-06-06
- Second brain compile (cron): quiet period continues (29 days since May 8), no new activity, compile #61

### 2026-06-05
- Second brain compile (cron): quiet period continues (28 days since May 8), no new activity, compile #60

### 2026-06-04
- Second brain compile (cron): quiet period continues (27 days since May 8), no new activity, compile #59

### 2026-06-03
- Second brain compile (cron): quiet period continues (26 days since May 8), no new activity, compile #58

### 2026-06-02
- Second brain compile (cron): quiet period continues (25 days since May 8), no new activity, compile #57

### 2026-06-01
- Second brain compile (cron): quiet period continues (24 days since May 8), no new activity, compile #56

### 2026-05-31
- Second brain compile (cron): quiet period continues (23 days since May 8), no new activity, compile #55

### 2026-05-30
- Second brain compile (cron): quiet period continues (22 days since May 8), no new activity, compile #54

### 2026-05-29
- Second brain compile (cron): quiet period continues (21 days since May 8), no new activity, compile #53

### 2026-05-28
- Second brain compile (cron): quiet period continues (20 days since May 8), no new activity, compile #52

### 2026-05-27
- Second brain compile (cron): quiet period continues (19 days since May 8), no new activity, compile #51

### 2026-05-26
- Second brain compile (cron): quiet period continues (18 days since May 8), no new activity, compile #50

### 2026-05-25
- Second brain compile (cron): quiet period continues (17 days since May 8), no new activity, compile #49

### 2026-05-24
- Second brain compile (cron): quiet period continues (16 days since May 8), no new activity, compile #48

### 2026-05-23
- Second brain compile (cron): quiet period continues (15 days since May 8), no new activity, compile #47

### 2026-05-22
- Second brain compile (cron): quiet period continues (14 days since May 8), no new activity, compile #46

### 2026-05-21
- Second brain compile (cron): quiet period continues (13 days since May 8), no new activity, compile #45

### 2026-05-20
- Second brain compile (cron): quiet period continues (12 days since May 8), no new activity, compile #44

### 2026-05-19
- Second brain compile (cron): quiet period continues (11 days since May 8), no new activity, compile #43

### 2026-05-18
- Second brain compile (cron): quiet period continues (10 days since May 8), no new activity, compile #42

### 2026-05-17
- Second brain compile (cron): quiet period continues (9 days since May 8), no new activity, compile #41

### 2026-05-16
- Second brain compile (cron): quiet period continues (8 days since May 8), no new activity, compile #40

### 2026-05-15
- Second brain compile (cron): quiet period continues (7 days since May 8), no new activity, compile #39

### 2026-05-14
- Second brain compile (cron): CAP Protocol spec + thought leadership article (new content after quiet period), Scout Academy May 2026 newsletter, compile #38

### 2026-05-13
- Second brain compile (cron): quiet period continues (8 days since May 5), no new activity/decisions/patterns/lessons, compile #37

### 2026-05-12
- Second brain compile (cron): quiet period continues (4 days since May 8), no new activity/decisions/patterns/lessons, compile #36

### 2026-05-11
- Second brain compile (cron): quiet period continues (3 days since May 8), no new activity/decisions/patterns/lessons, compile #35

### 2026-05-10
- Second brain compile (cron): quiet period — no new activity since May 8, no new decisions/patterns/lessons, compile #34

### 2026-05-09
- Second brain compile (cron): new activity after quiet period — "AI Native, How?" talk framework finalized, article quotes drafted, new pattern (conversational titles) + lesson (promise-driven titles), compile #33

### 2026-05-08
- Second brain compile (cron): quiet period day 3+ — no new memory files since May 5, no new decisions/patterns/lessons, pending items unchanged, compile #32

### 2026-05-07
- Second brain compile (cron): quiet period continues — "When the Algorithm Comes for Your Job" article started May 6 (sources + draft), HR AI images v2 generated, no new decisions/patterns/lessons, compile #31

### 2026-05-06
- Second brain compile (cron): quiet period ended — HR AI Strategy slides + OpenRouter image pipeline (May 5), new decision/pattern/lesson logged, compile #30

### 2026-05-05
- Second brain compile (cron): quiet period day 10, no new memory files since Apr 25 (10 days), no new content or decisions, compile #29

### 2026-05-04
- Second brain compile (cron): quiet period day 9, no new memory files since Apr 25 (9 days), no new content or decisions, compile #28

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