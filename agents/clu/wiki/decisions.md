# Decisions Log

## 2026-04-08: Context Window Optimization
**Context:** Session context was running out quickly due to 72 skills pre-loaded + verbose MEMORY.md
**Decision:** Trimmed MEMORY.md to essentials, created 4 reference skills, set 13 user skills to lazy-load via `disable-model-invocation: true`
**Reasoning:** 72 skills × ~74 tokens each ≈ 5,400 tokens just for skill descriptions. MEMORY.md was 13KB. Together these consumed significant context.
**Outcome:** Saved ~11KB per session (~3-4k tokens). Context now starts lean and loads skill content only when needed.

## 2026-04-08: Essay Format — Narrative Over Bullets
**Context:** AI link roundup for Scout Academy
**Decision:** Write narrative takes instead of bullet point lists
**Reasoning:** Rakis prefers narrative storytelling style — each section reads as a story with a point, not just a list of links
**Outcome:** More engaging, readable format. Published 3 versions (full, summary, thread).

## 2026-04-06: Essay Edits — Winston Speaking Framework
**Context:** "Adaptation of Agentic AI" essay review
**Decision:** Added empowerment promise, slogan, verbal punctuation, surprise ending per Patrick Winston's framework
**Reasoning:** Essay was missing these key elements — opened without purpose, had no memorable slogan, no checkpoint summaries, functional ending
**Outcome:** Score improved from 6/10 to 9/10 on Winston criteria.

## 2026-04-06: ScoutOS CTA Shortened
**Context:** Essay had long ScoutOS marketing section at the end
**Decision:** Shortened to one sentence + link
**Reasoning:** Rakis wanted simple statement, not marketing copy
**Outcome:** Cleaner, more confident ending.