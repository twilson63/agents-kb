# Patterns & Mental Models

## RAG Retrieves, This Compounds
RAG starts fresh every query. Knowledge bases compile once, update incrementally. The difference is compounding. Applies to agent memory (MEMORY.md), personal knowledge bases (Karpathy pattern), and enterprise systems.

## The Schema File Is the Key Innovation
Not a database. Not a RAG pipeline. Just a prompt (AGENTS.md, CLAUDE.md) that tells the AI how to think about the knowledge base. Without it: scattered files. With it: a system.

## Files Over Apps
Markdown is portable, human-readable, future-proof. No vendor lock-in. This is why agents-kb uses plain markdown instead of a database.

## Two Memory Layers
Daily logs (raw, unprocessed) + curated long-term memory (distilled, organized). Both are necessary. Raw captures everything. Curated keeps what matters. The compile step (raw → wiki) is where value accrues.

## LLMs for Reasoning, Scripts for Everything Else
Separate concerns: AI handles understanding, judgment, synthesis. Deterministic code handles formatting, API calls, data transforms, git operations. Don't ask an LLM to do what a script does better.

## Memory Is the Whole Advantage
From Barrett Sharpe on Ryan Sarver's system: "The memory piece is the part everyone skips and it's the whole advantage." Most people use AI like a tool — open, query, close. Zero accumulation. The memory layer is what makes it compound.

## Lazy Load by Default
With 72+ skills in a system, token overhead matters. Lazy-load (disable-model-invocation) skills that aren't used daily. Keep the prompt lean. Skills are still discoverable via find-skills or slash commands.

## The Orchestration Gap Is the Meta-Trend (April 2026)
Every major data source (Salesforce, Google, Belitsoft, Anthropic) signals the same thing: agents are deployed but not coordinated. 12 agents per company, 50% isolated, 11% to production. This isn't a bug — it's the structural gap between adoption and infrastructure. The opportunity is in the wiring, not the agents.

## UI Bifurcation: Two Surfaces, Not One
Products now need two surfaces: the human surface (visual, verifiable, steerable) and the agent surface (structured, semantic, API-first, MCP-exposed). MCP is becoming the agent surface standard (97M March 2026 installs). Products without both surfaces lose either humans or agents.

## Expressive > Sequential Tool Calling
Most developers implement MCP as sequential request-response. Colvin (Pydantic) argues for expressive tool calling: agents compose operations, branch on intermediate results, parallelize. The control-capability trade-off: most choose control but lose speed and flexibility.

## Pipeline Velocity Beats Solo Perfection
The content-publishing pipeline produces 10+ pieces in under 2 hours. The pattern: essay first → video from essay → publish both. Each piece reinforces the others. Solo perfection on one piece can't match 10 good pieces. Volume compounds visibility.

## Rendering Is the Weakest Link in Video Production
AI writes scripts, generates avatars, composes HTML. But the final render step (Hyperframes/Remotion) consistently fails at scale. The bottleneck isn't creativity — it's infrastructure. Chunking, timeout headroom, or pre-rendered templates are the workarounds.

## Negotiation Frameworks Apply to Agent Orchestration
Peterson's Stanford negotiation principles map to agent coordination: don't need the deal too badly (don't deploy desperately), don't treat it as a chore (design orchestration thoughtfully), don't optimize for local wins (system > individual agent).

## Auth Friction Breaks Flow
External APIs that change auth requirements without migration paths break agent workflows. Zenbin's shift from open publish to Ed25519 signing required manual keypair generation and registration — no automatic path. Lesson: any external dependency needs a fallback or local cache. Auth changes are the most disruptive type of API change for automated systems.

## Taste Over Output
Agents produce output. Humans exercise taste. The gap between "acceptable" and "excellent" is a judgment call that LLMs can flag but not make. Right framing: AI researches and executes; humans judge and relate. Don't conflate evaluation (as-judge) with taste (knowing what excellent looks like).