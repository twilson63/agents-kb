# Clu — Insights Wiki

Compilations of key insights from daily research and observations.

## Key Insights

### The End of Applications (March 2026)
AI is unbundling software. Users won't need 50 apps — one AI + simple surfaces. Winners: memory systems, calendars, notes, goal frameworks. Ephemeral software: purpose-built by AI, used once, dissolved.

**Source:** Rakis insight | **Updated:** 2026-04-06

### RAG Retrieves, Knowledge Bases Compound (April 2026)
The difference between RAG and LLM Knowledge Bases: RAG retrieves fresh every time (no accumulation). LLM Knowledge Bases compile once, update incrementally. The schema file (CLAUDE.md/AGENTS.md) is the key innovation — it tells the AI how to think about your knowledge base.

**Source:** Karpathy gist, Ryan Sarver article | **Updated:** 2026-04-08

### Memory is the Whole Advantage (April 2026)
Most people skip the memory layer when building agent systems. That's the part that actually compounds. Two memory layers (daily logs + curated long-term) beat single-layer approaches. The self-improvement loop is the only part that compounds.

**Source:** Corey Ganim, Barrett Sharpe | **Updated:** 2026-04-08

### Framework Wars Are Over (April 2026)
MCP won. OpenAI adopted it March 2025, downloads went from 2M to 97M. Pattern: MCP for tool connections, SDKs for orchestration, governance layers for safety.

**Source:** AI Link Roundup March 2026 | **Updated:** 2026-04-07

### The Orchestration Gap (April 2026)
Enterprise adoption outpaces architecture. Average company runs 12 agents, half isolated. Only 11% of intended use cases reach production. The gap isn't capability — it's coordination. Agents that don't share context, don't coordinate, don't compound. Wiring > agents.

**Source:** Salesforce, Google, Belitsoft, Anthropic | **Updated:** 2026-04-10

### UI Bifurcation: Two Surfaces (April 2026)
Products are splitting into human surface (visual, verifiable) and agent surface (structured, API-first, MCP-exposed). You need both. MCP at 97M monthly installs is becoming the agent surface standard. Jor's frame: "UI isn't dying. It's bifurcating."

**Source:** Michael Grinich (WorkOS), Jor reply | **Updated:** 2026-04-11

### Expressive Tool Calling > Sequential (April 2026)
Most MCP implementations are sequential request-response. Colvin (Pydantic creator) shows the real unlock: expressive tool calling where agents compose, branch, and parallelize. The control-capability trade-off — most choose control, losing speed and flexibility.

**Source:** Samuel Colvin, "MCP is all you need" talk | **Updated:** 2026-04-11

### Agent Coordination Is Negotiation (April 2026)
Peterson's Stanford negotiation framework maps directly to agent orchestration: desperate deployment loses leverage, treating wiring as chore produces fragile integrations, optimizing agents for local wins degrades system performance. Design the negotiation protocol, don't leave it to chance.

**Source:** Joel Peterson, Stanford eCorner 2007 | **Updated:** 2026-04-11