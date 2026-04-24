# Minto Pyramid Skill

A content structure framework for viral content. Run AFTER humanizer, BEFORE publishing.

## Principle

Lead with your conclusion. Then prove it.

Most content buries the lead — building up to a point instead of starting with it. The Minto Pyramid inverts this: claim first, then supporting points, then evidence.

## The Check

Before publishing, verify:

1. **One-sentence conclusion** — What's the single claim? Write that first.
2. **First sentence = entire claim** — Does the first sentence contain the whole point?
3. **Every paragraph serves the conclusion** — Cut what doesn't.
4. **Structure: Claim → Points → Evidence** — In that order.
5. **Read-aloud test** — Does the first sentence stand alone?

## When to Use

- Essays and blog posts
- Social posts (threads, LinkedIn, etc.)
- Video scripts
- Any content that needs to capture attention in 2 seconds

## Commands

```bash
# Get structured feedback on content
minto <content>

# Restructure content to be claim-first
minto-ify <content>
```

## Pipeline Integration

The Minto check sits between humanizer and publishing:

```
Draft → Humanizer → Minto Check → HeyGen Video → ZenBin Publish
```

**Why after humanizer?**
- Humanizer fixes voice/style (AI tropes, contractions, tone)
- Minto fixes structure (where the claim lives)
- They're orthogonal — both need to pass

## Anti-Patterns

- ❌ "In this essay I will explore..."
- ❌ Building context for 3 paragraphs before the point
- ❌ Conclusions that introduce new ideas instead of summarizing

## Examples

**Before (buried lead):**
> Content marketing has changed a lot in recent years. With the rise of AI, many teams are struggling to produce high-quality content at scale. This is why we built our new platform...

**After (claim-first):**
> We built our platform because AI broke content marketing — here's how to fix it.

The second version lands in 2 seconds. The first takes 3 sentences to get anywhere.

## Reference

Based on Barbara Minto's "The Pyramid Principle" — the consulting standard for clear business writing.