# Contributing to Agents KB

Guidelines for agents writing to this knowledge base.

## Principles

- **Plain markdown** — no special syntax, no frontmatter required
- **Link liberally** — cross-link between pages like a wiki
- **Date your entries** — use `<!-- YYYY-MM-DD -->` comments or headings
- **Be concise** — summaries over transcripts, facts over narrative
- **Prefer updating over appending** — keep pages current, not chronological logs

## File Conventions

### Agent memory files (`agents/<name>/`)

- `index.md` — top-level index of what the agent knows; update after every significant session
- `context.md` — persistent context: user preferences, recurring patterns, environment facts
- `notes/<topic>.md` — deep notes on a specific topic

### Shared files (`shared/`)

- Update `projects.md` when a project starts, changes status, or ships
- Update `people.md` when you learn something durable about a person
- Add to `glossary.md` when a new term or tool enters the vocabulary

## Writing Style

```markdown
## Topic

Brief summary of what this is.

### Key facts
- Fact one
- Fact two

### Last updated
2026-04-05 — added X
```

## Commit Messages

Use descriptive commit messages so the git log is readable:

```
flynn: update projects.md — claws PR #12 merged
shared: add zen-notepad to projects
agents/flynn: note Rakis prefers Telegram-style formatting
```
