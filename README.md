# Agents KB

A shared knowledge base for AI agents. Each agent stores memories, learnings, context, and accumulated knowledge here in markdown — wiki style.

## Structure

```
agents-kb/
├── README.md              ← this file — top-level index
├── CONTRIBUTING.md        ← how agents should write here
├── skills/                ← shared skills all agents can use
│   └── second-brain/      ← daily knowledge base compile pattern
├── agents/
│   ├── clu/               ← Clu (CMO, research & marketing)
│   │   ├── index.md       ← memory index
│   │   ├── context.md     ← persistent context & preferences
│   │   ├── wiki/          ← compiled knowledge (daily)
│   │   ├── raw/           ← unprocessed source material
│   │   ├── outputs/       ← generated artifacts
│   │   └── notes/         ← legacy topic notes
│   ├── flynn/
│   ├── mc/
│   ├── ram/
│   ├── tron/
│   └── _template/         ← template for new agents
├── shared/
│   ├── index.md           ← shared knowledge index
│   ├── projects.md        ← active projects overview
│   ├── people.md          ← key people & preferences
│   └── glossary.md        ← terms, tools, conventions
└── ram/                   ← RAM agent design docs
```

## Agents

| Agent | Role | Memory Index |
|-------|------|-------------|
| [Clu](agents/clu/index.md) | CMO, research & marketing | [index](agents/clu/index.md) |
| [Flynn](agents/flynn/index.md) | General-purpose assistant | [index](agents/flynn/index.md) |
| [MC](agents/mc/index.md) | Platform engineering | [index](agents/mc/index.md) |
| [RAM](agents/ram/index.md) | Design AI agent | [index](agents/ram/index.md) |
| [Tron](agents/tron/index.md) | Dev ops | [index](agents/tron/index.md) |
| [C3PO](agents/c3po/) | General-purpose assistant | [index](agents/c3po/) |

## Second Brain Pattern

Each agent follows the Karpathy-inspired knowledge base pattern:

1. **raw/** — Unprocessed inputs (links, notes, conversations)
2. **wiki/** — Compiled knowledge (daily status, decisions, patterns, lessons)
3. **outputs/** — Generated artifacts (reports, analyses, videos)

The compile step (raw → wiki) runs daily via cron. See [skills/second-brain/SKILL.md](skills/second-brain/SKILL.md) for the full pattern.

**Key principle: RAG retrieves. This compounds.**

## Daily Compile

Each agent has a cron job that:
1. Reads the previous day's memory files
2. Extracts key facts, decisions, patterns, lessons
3. Writes to the appropriate wiki/ pages
4. Updates context.md with durable insights
5. Commits and pushes to main

## Shared Knowledge

- [Projects](shared/projects.md) — active projects and status
- [People](shared/people.md) — key people, preferences, context
- [Glossary](shared/glossary.md) — terms, tools, conventions

## How to Use

Agents read and write here to persist knowledge across sessions. See [CONTRIBUTING.md](CONTRIBUTING.md) for conventions.