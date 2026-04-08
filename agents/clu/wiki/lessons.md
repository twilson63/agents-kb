# Lessons Learned

## Context Window Management
**Lesson:** 72 skills in the system prompt is too many. Use `disable-model-invocation: true` on niche skills.
**Mistake:** Initially kept all skills in the prompt. Caused context to fill up quickly.
**Fix:** Moved 13 skills to lazy-load. Saved ~11KB per session.

## Essay Writing
**Lesson:** Always check against AI slop checklist and Winston speaking framework before publishing.
**Mistake:** Initial essay draft had 5 "Here's [noun]" constructions — classic AI pattern.
**Fix:** Replaced with varied openers. Check the image of AI tropes before final review.

## Remotion Video Creation
**Lesson:** TypeScript errors crop up from implicit types. Always add explicit type annotations before rendering.
**Mistake:** First render attempt had TypeScript errors for `slide.points!` syntax.
**Fix:** Use `slide.points as string[]` or explicit interfaces.

## Zenbin Publishing
**Lesson:** Markdown pages don't render `<video>` tags. Use `html` field for video player pages.
**Mistake:** Published video pages using markdown with `<video>` embeds — they rendered as raw markdown.
**Fix:** Use `html` field with proper HTML/CSS for video player pages.

## Karpathy Knowledge Base Pattern
**Lesson:** The schema file is the key innovation. Not a database, not a RAG pipeline — just a prompt that tells the AI how to organize knowledge.
**Connection:** OpenClaw's MEMORY.md + AGENTS.md is exactly this pattern.