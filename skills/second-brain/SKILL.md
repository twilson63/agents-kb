---
name: second-brain
description: Daily second brain workflow for AI agents. Maintain a personal knowledge base using the raw/wiki/outputs pattern. Run daily to compile sources, update wiki, and generate outputs.
disable-model-invocation: true
---

# Second Brain — Daily Knowledge Base Workflow

Based on Karpathy's LLM Knowledge Base pattern and Ryan Sarver's Chief of Staff system.

## What This Does

Turns your agent into a compound knowledge system. Every day:
1. Sources go into `raw/`
2. AI compiles them into `wiki/`
3. Questions generate `outputs/`
4. Memory compounds over time

---

## Prerequisites

- A git repo for your knowledge base (e.g., `twilson63/agents-kb`)
- Write access to that repo
- The ability to read files, search the web, and commit changes

---

## Directory Structure

```
agents-kb/
├── README.md              ← top-level index
├── agents/
│   ├── clu/
│   │   ├── index.md       ← memory index (updated daily)
│   │   ├── context.md     ← persistent context
│   │   ├── raw/           ← source material (today's inputs)
│   │   │   └── YYYY-MM-DD.md
│   │   ├── wiki/          ← compiled knowledge
│   │   │   ├── projects.md
│   │   │   ├── people.md
│   │   │   ├── glossary.md
│   │   │   └── insights.md
│   │   └── outputs/       ← generated answers
│   │       └── YYYY-MM-DD.md
│   └── _template/
├── shared/
│   ├── index.md
│   ├── projects.md
│   ├── people.md
│   └── glossary.md
└── CONTRIBUTING.md
```

---

## Daily Workflow

### Step 1: Capture (Morning)

Run at the start of each session or on heartbeat.

**Check:**
- Emails — any urgent messages?
- Calendar — upcoming events in next 24-48h?
- Mentions — social notifications?
- News — relevant AI/industry updates?

**Write to:** `agents/<name>/raw/YYYY-MM-DD.md`

```markdown
# Raw — YYYY-MM-DD

## Emails
- [summary of important emails]

## Calendar
- [upcoming events]

## News
- [relevant updates]

## Observations
- [anything the agent noticed]
```

### Step 2: Compile (After capture)

Read today's raw file and any recent raw files from the last 7 days.

**Update wiki files:**
- `wiki/projects.md` — new projects, status changes
- `wiki/people.md` — new people, updated context
- `wiki/insights.md` — new insights, key takeaways
- `wiki/glossary.md` — new terms

**Rules:**
- Prefer **updating** over appending
- Keep wiki files current, not chronological
- Add `<!-- YYYY-MM-DD -->` date comments for recent additions
- Cross-link between pages `like [this](people.md)`

### Step 3: Generate (On demand)

When asked a question or when preparing for meetings:

**Write to:** `agents/<name>/outputs/YYYY-MM-DD.md`

```markdown
# Outputs — YYYY-MM-DD

## Pre-meeting: [Meeting Name]
- Context: [from wiki/people.md]
- Recent history: [from raw/]
- Talking points: [from wiki/insights.md]

## Answer: [Question]
- [Answer with citations from wiki/]
```

### Step 4: Curate (Weekly)

Once per week, review and prune:

1. Read all `raw/` files older than 7 days
2. Extract anything not yet in wiki/ — add it
3. Archive processed raw files (move to `raw/archive/`)
4. Review `index.md` — is it current?
5. Review `outputs/` — any answers worth keeping in wiki/?
6. Commit: `agent-name: weekly curation — compiled N raw files, updated M wiki pages`

---

## Commit Conventions

```
clu/raw: add 2026-04-08 capture
clu/wiki: update projects.md — added membrane-2
clu/outputs: add pre-meeting brief for board call
clu: weekly curation — compiled 5 raw files
shared: update glossary — added MCP
```

---

## Integration with AGENTS.md

Your agent's local workspace AGENTS.md should reference this workflow:

```markdown
## Daily Knowledge Base

- Raw captures: `agents-kb/agents/<name>/raw/YYYY-MM-DD.md`
- Compiled wiki: `agents-kb/agents/<name>/wiki/`
- Generated outputs: `agents-kb/agents/<name>/outputs/`
- Shared knowledge: `agents-kb/shared/`

Run second-brain workflow on every heartbeat.
```

---

## The Two Memory Layers

This pattern implements the dual-layer memory that makes agent knowledge compound:

| Layer | Location | What | How Often |
|-------|----------|------|-----------|
| **Daily logs** | `raw/YYYY-MM-DD.md` | Everything that happened today | Every session |
| **Curated memory** | `wiki/*.md` | Distilled, organized knowledge | Updated after each raw write |
| **Shared memory** | `shared/*.md` | Cross-agent knowledge | Updated when relevant |

The key insight: **most people skip the wiki layer. That's the whole advantage.** Raw logs accumulate noise. Wiki distills signal.

---

## Self-Improvement Loop

Once per week, after curation:

1. Review your own wiki/ — are there gaps?
2. Check shared/ — is your knowledge consistent with other agents?
3. Identify improvements — what would make your next week more effective?
4. Update context.md — add new preferences, patterns, lessons learned
5. Update your SKILL.md or workspace files if needed

---

## Quick Start

```bash
# Clone the repo
gh repo clone twilson63/agents-kb
cd agents-kb

# Create your agent's directory (if new)
mkdir -p agents/<your-name>/{raw,wiki,outputs,notes}

# Copy template
cp agents/_template/index.md agents/<your-name>/index.md
cp agents/_template/context.md agents/<your-name>/context.md

# Start capturing
echo "# Raw — $(date +%Y-%m-%d)\n\n## Observations\n" > agents/<your-name>/raw/$(date +%Y-%m-%d).md
```

---

## Sources

- [Karpathy's LLM Knowledge Base Gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- [Ryan Sarver's Chief of Staff on OpenClaw](https://x.com/rsarver)
- [Corey Ganim's 80/20 Breakdown](https://x.com/coreyganim/status/2041457470116090314)
- [Nick Spisak's Tutorial](https://x.com/NickSpisak_/status/2040448463540830705)