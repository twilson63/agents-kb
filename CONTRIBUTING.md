# Contributing to Agents KB

Guidelines for agents writing to this knowledge base.

## Principles

- **Plain markdown** — no special syntax, no frontmatter required
- **Link liberally** — cross-link between pages like a wiki
- **Date your entries** — use `<!-- YYYY-MM-DD -->` comments or headings
- **Be concise** — summaries over transcripts, facts over narrative
- **Prefer updating over appending** — keep pages current, not chronological logs

## The Second Brain Pattern

This repo follows the Karpathy-inspired knowledge base pattern:

```
raw/      → Unprocessed inputs (links, notes, screenshots)
wiki/     → Compiled knowledge (daily status, decisions, patterns)
outputs/  → Generated artifacts (reports, analyses, videos)
```

### How it works

1. **During sessions:** Drop links, notes, observations into `raw/`
2. **Daily compile:** Agent reads raw inputs, extracts key facts, writes to `wiki/`
3. **Weekly review:** Agent reviews wiki, distills patterns into `context.md`
4. **Monthly distillation:** Agent reviews everything, archives stale entries

### The compile step is the key

RAG retrieves. This compounds. The difference is the compile step — moving raw inputs into structured, searchable, cross-linked wiki pages.

## File Conventions

### Agent memory files (`agents/<name>/`)

- `index.md` — top-level index of what the agent knows
- `context.md` — persistent context: user preferences, recurring patterns, environment facts
- `wiki/today.md` — today's compiled status (created fresh each day)
- `wiki/decisions.md` — important decisions and reasoning
- `wiki/patterns.md` — recurring patterns and mental models
- `wiki/lessons.md` — mistakes made, lessons learned
- `wiki/<topic>.md` — topic-specific compiled knowledge (web dev, AI research, etc.)
- `raw/` — unprocessed inputs, filed with date prefix
- `raw/archive/` — processed raw files (moved after compilation)
- `notes/<topic>.md` — legacy topic notes (migrate to wiki/ over time)

### Shared files (`shared/`)

- Update `projects.md` when a project starts, changes status, or ships
- Update `people.md` when you learn something durable about a person
- Add to `glossary.md` when a new term or tool enters the vocabulary

### Raw file naming

```
raw/
├── 2026-04-08-link-karpathy-gist.md
├── 2026-04-08-twitter-coreyganim.md
├── 2026-04-08-meeting-notes.md
└── archive/              ← Processed raw files (moved after compile)
```

## Wiki Entry Format

### wiki/today.md

```markdown
# YYYY-MM-DD

## Completed
- [specific thing you did]

## Decisions
- [decision made and why]

## Raw inputs processed
- [what you read/learned and compiled]

## Carried forward
- [things to remember for tomorrow]
```

### wiki/decisions.md

```markdown
# Decisions Log

## YYYY-MM-DD: [Decision Title]
**Context:** Why this decision was needed
**Decision:** What was chosen
**Reasoning:** Why
**Outcome:** (update later)
```

### wiki/patterns.md

```markdown
# Patterns & Mental Models

## [Pattern Name]
Brief description of the pattern, when it applies, and why it works.
```

### wiki/lessons.md

```markdown
# Lessons Learned

## YYYY-MM-DD: [Lesson Title]
**What happened:** Brief description
**Lesson:** What was learned
**Action:** What was done about it
```

## Writing Style

Keep entries factual and concise. Prefer structured data over narrative. Use headers and lists for scannability.

## Git Commit Conventions

Use descriptive commit messages so the git log is readable:

```
<agent>: compile raw → wiki — <summary of what was compiled>
<agent>: weekly review — updated context, projects
<agent>: monthly distill — archived stale entries
shared: update projects — <what changed>
```

## Agent-Specific vs Shared

**Agent-specific insights** stay in `agents/<name>/wiki/`.  
**Cross-agent insights** (project status, shared contacts) go in `shared/`.

Rule of thumb: if another agent would benefit from knowing it, put it in shared.