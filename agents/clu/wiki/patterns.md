# Patterns & Mental Models

## The Second Brain Pattern
Three layers: raw/ → wiki/ → context. Raw inputs get compiled daily into wiki pages. Weekly reviews distill wiki into context. Monthly reviews archive stale entries. Key insight from Karpathy: RAG retrieves, this compounds.

## The End of Applications
AI is unbundling software. Users won't need 50 apps — one AI + simple surfaces. Winners: memory systems, calendars, notes, goal frameworks. Ephemeral software: purpose-built by AI, used once, dissolved.

## Communication Preferences (Rakis)
- Narrative takes, not bullet points (confirmed April 2026)
- Short CTAs, not marketing copy
- Winston speaking criteria for long-form content
- Apply AI slop checklist before publishing

## Context Optimization
- Skills with `disable-model-invocation: true` don't appear in system prompt
- Still available via `/skill-name` or explicit `read` calls
- MEMORY.md should stay under 3KB — push details into skills
- Daily notes (memory/*.md) accumulate — roll up into wiki/ regularly