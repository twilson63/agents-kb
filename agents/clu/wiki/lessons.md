# Lessons Learned

## 2026-04-08: Token Budget Matters
**What happened:** System prompt was consuming too many tokens with all skill descriptions pre-loaded.
**Lesson:** Default to lazy-loading. Measure token cost of skills, MEMORY.md, and AGENTS.md. Every ~100 tokens of injected context reduces available conversation context.
**Action:** Set `disable-model-invocation: true` on 13 skills. Trimmed MEMORY.md from 13KB to 2.3KB.

## 2026-04-08: Karpathy Pattern Applies to Agent Memory
**What happened:** Studied Karpathy's LLM Knowledge Base gist and Ryan Sarver's OpenClaw chief of staff setup.
**Lesson:** The three-folder pattern (raw/wiki/outputs) with a schema file maps directly to what we already do with memory/*.md + MEMORY.md + AGENTS.md. The compile step is what we were missing — the daily cron job that moves raw → wiki.
**Action:** Created second-brain skill and cron job to formalize the compile step.

## 2026-04-08: Narrative Over Bullets
**What happened:** Rakis asked for narrative takes instead of bullet lists in the AI roundup.
**Lesson:** Bullet points are easier to write but narrative is more engaging and memorable. Winston's "How to Speak" framework applies to written content too — empowerment promises, slogans, surprising endings.
**Action:** Rewrote roundup as narrative. Applied same principle to essay editing.

## 2026-04-06: Winston Criteria for Essays
**What happened:** Reviewed "Adaptation of Agentic AI" essay against AI trope checklist and Patrick Winston's "How to Speak" framework.
**Lesson:** Essays need: (1) empowerment promise at start, (2) memorable slogan, (3) verbal punctuation/checkpoints, (4) surprising ending (not "thanks for reading"), (5) cycling through ideas 3-5 times with different support.
**Action:** Added all missing elements to the essay. Stored as skill (speaking-framework) for future use.

## 2026-04-10: When Multiple Sources Converge, Own the Synthesis
**What happened:** Salesforce connectivity report, Google agent trends, Belitsoft data, and Anthropic coding trends all landed in the same week pointing at the orchestration gap.
**Lesson:** When independent sources converge on the same signal, that's a meta-trend. Don't just report each one — synthesize them into a narrative. The synthesis is more valuable than any single data point.
**Action:** Produced 5 Scout Academy articles threading the orchestration theme. Each article stands alone but they reinforce each other editorially.

## 2026-04-11: Developer Communities Require Daily Practice, Not Campaigns
**What happened:** Compiled DevRel research into community building playbook for hyper.io.
**Lesson:** DevRel isn't a project with a start and end date. It's a daily practice. "Go where developers already are" beats "build it and they will come" every time. Content that helps developers NOW builds trust; marketing-speak kills it.
**Action:** 4-phase plan: foundation → presence → content engine → advocate program. Start in existing communities, build Hive's own later.

## 2026-04-12: Missing Daily Logs = Lost Context
**What happened:** No memory/2026-04-10.md or 2026-04-11.md files existed, despite significant content production.
**Lesson:** Content can be produced without leaving memory traces. If I don't log daily, later compiles have to infer from file timestamps rather than reading direct notes. The daily log discipline matters even during productive stretches.
**Action:** Need to ensure daily logs are created even on busy days. Consider adding a reminder or habit trigger.

## 2026-04-12: Cron Timeouts Need Headroom
**What happened:** Second brain compile cron jobs (clu at 4AM, mc at 5AM) were both failing with 120s timeouts. Increased to 300s and they succeeded.
**Lesson:** Default timeouts are often too tight for cron jobs that do file I/O + git operations + web fetches. Always set timeout to 2-3x expected run time. Monitor first few runs before trusting the schedule.
**Action:** Updated both cron jobs to 300s timeout. Will monitor and adjust if needed.