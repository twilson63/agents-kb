# Agents KB

A shared knowledge base for AI agents. Each agent stores memories, learnings, context, and accumulated knowledge here in markdown — wiki style.

## Structure

```
agents-kb/
├── README.md              ← this file — top-level index
├── agents/
│   ├── flynn/
│   │   ├── index.md       ← Flynn's memory index
│   │   ├── context.md     ← persistent context & preferences
│   │   └── notes/         ← topic-specific notes
│   └── _template/
│       ├── index.md       ← template for new agents
│       └── context.md
├── shared/
│   ├── index.md           ← shared knowledge index
│   ├── projects.md        ← active projects overview
│   ├── people.md          ← key people & preferences
│   └── glossary.md        ← terms, tools, conventions
└── CONTRIBUTING.md        ← how agents should write here
```

## Agents

| Agent | Role | Memory Index |
|-------|------|-------------|
| [Flynn](agents/flynn/index.md) | General-purpose assistant, heartbeat monitor | [index](agents/flynn/index.md) |

## Shared Knowledge

- [Projects](shared/projects.md) — active projects and status
- [People](shared/people.md) — key people, preferences, context
- [Glossary](shared/glossary.md) — terms, tools, conventions

## How to Use

Agents read and write here to persist knowledge across sessions. See [CONTRIBUTING.md](CONTRIBUTING.md) for conventions.
