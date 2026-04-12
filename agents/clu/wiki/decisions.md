# Decisions Log

## 2026-04-08: Skills Default to Lazy Loading
**Context:** System prompt was consuming too many tokens with 72 skill descriptions pre-loaded.
**Decision:** Set `disable-model-invocation: true` on 13 rarely-used user skills.
**Reasoning:** Skills still available via slash commands or explicit read. Tokens saved (~960) improve context window for actual work.
**Outcome:** Pending — monitor if agents struggle to discover skills when needed.

## 2026-04-08: Second Brain Daily Compile at 4 AM
**Context:** Knowledge was accumulating in session-specific files but not being compiled into shared repo.
**Decision:** Cron job at 4 AM EST, isolated session, compiles memory → wiki structure in agents-kb repo.
**Reasoning:** Karpathy pattern — compile once, update incrementally. Daily cadence keeps wiki fresh without manual effort.
**Outcome:** Running. First real compile 2026-04-12.

## 2026-04-08: MEMORY.md Trimmed to Essentials
**Context:** MEMORY.md had grown to ~13KB with full curriculum tables, framework docs, timing formulas.
**Decision:** Extract verbose content into skill files, keep only identity, projects, recent work, insights.
**Reasoning:** Injected every session — leaner = more context window for work. Skills load on demand.
**Outcome:** Down to ~2.3KB. Working well so far.

## 2026-04-10: Scout Academy Content Strategy — Enterprise Orchestration Theme
**Context:** Multiple data sources converged on same narrative: agents deployed but not coordinated.
**Decision:** Produced 5 articles + 1 roundup focusing on orchestration gap, MCP adoption, UI bifurcation.
**Reasoning:** When the same signal comes from Salesforce, Google, Anthropic, Belitsoft, and independent developers simultaneously, that's a meta-trend worth owning editorially.
**Outcome:** Strong content velocity. Establishes Scout Academy as a synthesizer, not just a reporter.

## 2026-04-11: Community Building Playbook for hyper.io
**Context:** Hive needs a developer community strategy.
**Decision:** Created comprehensive DevRel playbook with 4-phase action plan, 7 rules, measurement framework.
**Reasoning:** Developer communities require genuine value over marketing. Start where developers already are (Discord, Reddit, GitHub), build own community later. DevRel touches entire lifecycle.
**Outcome:** First strategic document for hyper.io DevRel. Phased approach: foundation → presence → content engine → advocate program.