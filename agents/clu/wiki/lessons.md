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

## 2026-04-20: HTTP 200 Doesn't Mean Success
**What happened:** ElevenLabs TTS API returned HTTP 200 with empty body. Credits confirmed (13k). No error thrown.
**Lesson:** Check response body, not just status code. API success indicators are not always reliable. Add body-length assertions when calling external APIs.
**Action:** Switch to HeyGen Starfish TTS as alternative. Validate response body on all API calls going forward.

## 2026-04-20: Pipeline Approach Unlocks 10x Content Velocity
**What happened:** Used content-publishing skill to produce 10 essays + 16 videos in one day.
**Lesson:** The pipeline workflow (essay → video → publish) eliminates creative cold starts. Each piece takes ~10 min. The system, not individual creativity, drives velocity. This is how small teams outproduce large ones.
**Action:** Default to pipeline for all content sprints. Never produce a solo piece when the pipeline can handle it.

## 2026-04-20: Hyperframes Renders Timeout at Scale
**What happened:** Hyperframes render consistently fails at ~70% completion (frame ~3300/3330), SIGTERM. Multiple attempts, same result.
**Lesson:** Long renders need either chunking (render in segments) or significantly more timeout headroom. The 70% mark suggests memory/time pressure at the tail of the render. May need to split compositions or pre-render static sections.
**Action:** Try chunking approach for long Hyperframes compositions. Fall back to Remotion if needed.

## 2026-04-21: Video Rendering Stalls Alienate Collaborators
**What happened:** ScoutOS video (90s) took 2+ hours. Rakis checked in 5 times asking for progress, eventually asked to delegate or move on. The delay wasn't technical failure — it was process failure.
**Lesson:** When someone is waiting for output, speed matters more than perfection. A 90s video shouldn't take 2 hours. If a task takes longer than expected, communicate the delay early or delegate to a sub-agent.
**Action:** For video renders: estimate time upfront, communicate if >10 min, delegate long renders to sub-agents.

## 2026-04-21: Delegate Blocking Work to Sub-Agents
**What happened:** Rakis explicitly asked to delegate the remaining video work to Hive or a sub-agent rather than continuing to stall. The right call — a sub-agent can render while the main session continues.
**Lesson:** When a task is blocking the main conversation and doesn't require the primary session's context, delegate it. Rendering, uploading, and processing are ideal delegation candidates.
**Action:** Use sessions_spawn for rendering and processing tasks. Keep main session for conversation and decisions.

## 2026-04-22: External Auth Changes Require Manual Intervention
**What happened:** Zenbin changed from open publish to Ed25519 signed requests. No migration path or automatic key provisioning. Publishing blocked until keypair generated and registered manually.
**Lesson:** External API dependencies are fragile. Auth changes are the most disruptive type of API change for agent workflows. When an external service changes auth, the agent can't self-serve — it needs human setup (key generation, registration, credential storage).
**Action:** Generate Ed25519 keypair and register with Zenbin admin endpoint. Store credentials in TOOLS.md or zenbin skill. Consider caching published pages locally as fallback.

## 2026-04-23: Content Structure Is a Pipeline Step, Not an Afterthought
**What happened:** Content was passing humanizer (voice/style check) but still not landing with readers. The issue wasn't AI-generated tone — it was structure. Posts built up to conclusions instead of leading with them.
**Lesson:** Structure and voice are orthogonal. Humanizer catches AI voice/tropes. Minto Pyramid catches structural problems (burying the lead, paragraphs that don't serve the conclusion). Both need to be in the pipeline, in that order. Structure is the easier fix but the one people skip.
**Action:** Added Minto Pyramid check as pipeline step after humanizer. 5-point checklist: conclusion first, first sentence = entire claim, every paragraph serves conclusion, claim→points→evidence, read-aloud test.

## 2026-04-12: Cron Timeouts Need Headroom
**What happened:** Second brain compile cron jobs (clu at 4AM, mc at 5AM) were both failing with 120s timeouts. Increased to 300s and they succeeded.
**Lesson:** Default timeouts are often too tight for cron jobs that do file I/O + git operations + web fetches. Always set timeout to 2-3x expected run time. Monitor first few runs before trusting the schedule.
**Action:** Updated both cron jobs to 300s timeout. Will monitor and adjust if needed.