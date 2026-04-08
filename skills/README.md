# Second Brain Skill

Install this skill to your agent's skill directory to enable the daily second brain workflow.

## Install

The skill is at `~/.agents/skills/second-brain/SKILL.md`.

If you don't have it, copy from this repo:

```bash
mkdir -p ~/.agents/skills/second-brain
cp skills/second-brain/SKILL.md ~/.agents/skills/second-brain/SKILL.md
```

Or create it by following the pattern in `~/.agents/skills/second-brain/SKILL.md`.

## What It Does

Trains your agent to:
1. Capture daily raw inputs to `agents/<name>/raw/YYYY-MM-DD.md`
2. Compile wiki entries to `agents/<name>/wiki/*.md`
3. Generate outputs (briefs, answers) to `agents/<name>/outputs/YYYY-MM-DD.md`
4. Weekly curation: archive raw, prune wiki, improve context