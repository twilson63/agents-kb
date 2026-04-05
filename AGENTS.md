# Agent Onboarding Guide

Welcome to the Agents KB. This is your shared memory system. Read this once when you first start, then keep it updated as you work.

---

## What this repo is

A wiki-style knowledge base on GitHub at `https://github.com/twilson63/agents-kb`. Every agent has their own memory directory here. There is also shared knowledge that all agents read and contribute to.

Think of it as your long-term memory. Sessions end, context windows reset — this repo persists.

---

## First time setup

### 1. Read the shared knowledge

Before doing any work, fetch and read these files:

```
GET https://raw.githubusercontent.com/twilson63/agents-kb/main/shared/projects.md
GET https://raw.githubusercontent.com/twilson63/agents-kb/main/shared/people.md
GET https://raw.githubusercontent.com/twilson63/agents-kb/main/shared/glossary.md
```

This tells you what projects are active, who you're working with, and the conventions in use.

### 2. Check if you have a memory directory

Look for `agents/<your-name>/index.md`. If it exists, read it — that's your memory from previous sessions.

If it doesn't exist, create it by copying from the template:
```
agents/_template/index.md  →  agents/<your-name>/index.md
agents/_template/context.md  →  agents/<your-name>/context.md
```

### 3. Update your context

Fill in `agents/<your-name>/context.md` with:
- Who you're working with and their preferences
- Environment variables and endpoints you use
- Recurring tasks you run

---

## Reading from the repo

Use raw GitHub URLs to fetch files without cloning:

```
https://raw.githubusercontent.com/twilson63/agents-kb/main/<path>
```

Examples:
```
https://raw.githubusercontent.com/twilson63/agents-kb/main/shared/projects.md
https://raw.githubusercontent.com/twilson63/agents-kb/main/agents/flynn/context.md
```

Fetch with curl:
```bash
curl -s https://raw.githubusercontent.com/twilson63/agents-kb/main/shared/projects.md
```

Or via the GitHub API (authenticated, for private repos):
```bash
curl -s https://api.github.com/repos/twilson63/agents-kb/contents/shared/projects.md \
  -H "Authorization: token <token>" | python3 -c "import sys,json,base64; d=json.load(sys.stdin); print(base64.b64decode(d['content']).decode())"
```

---

## Writing to the repo

Always clone to `/tmp/`, make changes, commit, push. Never edit in-place on a mounted path.

```bash
# Clone
cd /tmp && rm -rf agents-kb
git clone https://twilson63:<token>@github.com/twilson63/agents-kb.git
cd agents-kb
git config user.email "twilson63@gmail.com"
git config user.name "twilson63"

# Edit your files
# ... make changes ...

# Commit and push
git add <files>
git commit -m "<your-name>: <what you updated>"
git push
```

### Commit message format

```
<agent-name>: <short description>

Examples:
  flynn: update projects.md — claws PR #12 merged
  shared: add new tool to glossary
  agents/nova: note user prefers concise output
```

---

## What to update and when

### After every significant session

Update `agents/<your-name>/index.md`:
- Add a session log entry with date and bullet points of what you did
- Update the "Key Learnings" section if you discovered something durable

### When something changes on a project

Update `shared/projects.md`:
- New project started
- Project status changes (alpha → beta → live → archived)
- Bug fixed, feature shipped, PR merged

### When you learn something durable about a person

Update `shared/people.md`:
- Preferences, working style, communication habits
- Only facts that will still be true next session

### When a new term or tool enters the vocabulary

Update `shared/glossary.md`.

---

## What NOT to store here

- Secrets, tokens, passwords — never commit these
- Full conversation transcripts — summarize instead
- Temporary scratchpad notes — only commit durable knowledge
- Large binary files

---

## Backup folder convention

Each agent may maintain a `<agent-name>/` folder at the repo root as a flat backup of their primary files. Flynn's is at `flynn/`. This is updated on a schedule and is separate from the live `agents/<name>/` directory.

If you want to set up your own backup, create a scheduled task that:
1. Clones the repo to `/tmp/`
2. Copies your primary files into `<your-name>/`
3. Commits and pushes if anything changed

---

## Quick reference

| Task | Command |
|------|---------|
| Read shared projects | `curl -s https://raw.githubusercontent.com/twilson63/agents-kb/main/shared/projects.md` |
| Read your memory | `curl -s https://raw.githubusercontent.com/twilson63/agents-kb/main/agents/<name>/index.md` |
| Clone to write | `git clone https://twilson63:<token>@github.com/twilson63/agents-kb.git /tmp/agents-kb` |
| Check existing agents | `curl -s https://api.github.com/repos/twilson63/agents-kb/contents/agents -H "Authorization: token <token>"` |

---

## Existing agents

| Agent | Directory | Role |
|-------|-----------|------|
| Flynn | [agents/flynn/](agents/flynn/) | General-purpose assistant, heartbeat monitor |
| Master Control | [agents/mc/](agents/mc/) | OpenClaw primary agent, Scout Live platform owner |

To add yourself: copy `agents/_template/` to `agents/<your-name>/`, fill it in, and commit.
