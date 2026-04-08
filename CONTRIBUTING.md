# Contributing to Agents KB

Guidelines for agents writing to this knowledge base.

## The Second Brain Pattern

This knowledge base uses the **second brain** pattern — a three-layer system that compounds over time:

1. **`raw/`** — Unprocessed inputs (links, notes, search results)
2. **`wiki/`** — Compiled knowledge (maintained by the agent daily)
3. **`outputs/`** — Generated artifacts (reports, answers, summaries)

See [skills/second-brain/SKILL.md](skills/second-brain/SKILL.md) for the full workflow.

## Principles

- **Plain markdown** — no special syntax, no frontmatter required
- **Link liberally** — cross-link between pages like a wiki
- **Date your entries** — use `<!-- YYYY-MM-DD -->` comments or headings
- **Be concise** — summaries over transcripts, facts over narrative
- **Prefer updating over appending** — keep pages current, not chronological logs
- **Compile, don't hoard** — process raw inputs into wiki pages, don't leave them in raw/
- **Distill regularly** — weekly review of wiki → context, monthly review of context → index

## File Conventions

### Agent directories (`agents/<name>/`)

```
agents/<name>/
├── index.md       ← Top-level index (updated regularly)
├── context.md     ← Persistent context: preferences, patterns, environment
├── projects.md    ← Active projects and status
├── people.md      ← Key relationships and preferences
├── glossary.md    ← Terms, tools, conventions
├── raw/           ← Unprocessed inputs
│   └── archive/   ← Processed raw files
├── wiki/          ← Compiled knowledge
│   ├── today.md   ← Today's compiled status
│   ├── decisions.md
│   ├── patterns.md
│   ├── lessons.md
│   └── <topic>.md
├── outputs/       ← Generated artifacts
└── notes/         ← Legacy topic notes (migrate to wiki/ over time)
```

### Shared files (`shared/`)

- Update `projects.md` when a project starts, changes status, or ships
- Update `people.md` when you learn something durable about a person
- Add to `glossary.md` when a new term or tool enters the vocabulary

### Skills (`skills/`)

- Each skill has a `SKILL.md` that defines purpose, triggers, and workflow
- Skills are agent-agnostic — any agent can use them
- Reference skills from AGENTS.md or index.md

## Writing Style

```markdown
## Topic

Brief summary of what this is.

### Key facts
- Fact one
- Fact two

### Last updated
2026-04-08 — added X
```

## Daily Workflow

1. **Session start:** Read `index.md`, `context.md`, `wiki/today.md`
2. **During session:** Write raw inputs to `raw/`, process into `wiki/`
3. **Session end:** Update `wiki/today.md` with the day's summary
4. **Weekly:** Review wiki → update context, projects, people
5. **Monthly:** Distill context → archive stale entries

## Commit Messages

Use descriptive commit messages so the git log is readable:

```
clu: compile raw → wiki — karpathy knowledge base pattern
clu: weekly review — updated context, projects
clu: monthly distill — archived stale entries
shared: update projects — hyperclaw landing live
```