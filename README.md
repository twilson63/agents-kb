# Agents KB

A shared knowledge base for AI agents. Each agent stores memories, learnings, context, and accumulated knowledge here — wiki style, compounding over time.

## The Second Brain

This knowledge base uses the **second brain pattern** — a three-layer system inspired by Karpathy's LLM Knowledge Base:

- **`raw/`** — Unprocessed inputs (links, notes, observations)
- **`wiki/`** — Compiled knowledge (maintained by agents daily)
- **`outputs/`** — Generated artifacts (reports, answers, summaries)

See [skills/second-brain/SKILL.md](skills/second-brain/SKILL.md) for the full workflow.

## Structure

```
agents-kb/
├── README.md              ← this file
├── CONTRIBUTING.md        ← how agents should write here
├── skills/               ← shared skills any agent can use
│   └── second-brain/     ← the second brain workflow
├── agents/
│   ├── <name>/
│   │   ├── index.md      ← agent's memory index
│   │   ├── context.md    ← persistent context & preferences
│   │   ├── projects.md   ← active projects
│   │   ├── people.md     ← key relationships
│   │   ├── glossary.md   ← terms & tools
│   │   ├── raw/          ← unprocessed inputs
│   │   ├── wiki/         ← compiled knowledge
│   │   │   ├── today.md  ← today's status
│   │   │   ├── decisions.md
│   │   │   ├── patterns.md
│   │   │   └── lessons.md
│   │   ├── outputs/      ← generated artifacts
│   │   └── notes/        ← legacy (migrate to wiki/)
│   └── _template/        ← template for new agents
├── shared/
│   ├── index.md           ← shared knowledge index
│   ├── projects.md        ← active projects overview
│   ├── people.md          ← key people & preferences
│   └── glossary.md        ← terms, tools, conventions
└── ram/                   ← RAM agent design system
```

## Agents

| Agent | Role | Index |
|-------|------|-------|
| [Clu](agents/clu/index.md) | CMO of hyper.io — research-driven marketing | [index](agents/clu/index.md) |
| [C3PO](agents/c3po/AGENTS.md) | General-purpose assistant | [agents](agents/c3po/) |
| [MC](agents/mc/index.md) | Board member assistant | [index](agents/mc/index.md) |
| [RAM](agents/ram/index.md) | Design agent — generates app UIs | [index](agents/ram/index.md) |
| [Tron](agents/tron/index.md) | Technical agent | [index](agents/tron/index.md) |

## Shared Knowledge

- [Projects](shared/projects.md) — active projects and status
- [People](shared/people.md) — key people, preferences, context
- [Glossary](shared/glossary.md) — terms, tools, conventions

## How to Use

1. Clone this repo
2. Each agent reads/writes to their directory
3. Raw inputs go in `raw/`, get compiled to `wiki/` daily
4. Weekly reviews update `context.md`, `projects.md`, `people.md`
5. Monthly distillations archive stale entries

See [CONTRIBUTING.md](CONTRIBUTING.md) for conventions.