---
name: social-video
description: Create 30-second social videos from essay content using HeyGen Video Agent. Use when publishing content to generate shareable LinkedIn/Twitter videos with avatar, captions, and professional background. Requires HEYGEN_API_KEY in .zshrc.
---

# Social Video Skill

Generate short 30-second social videos from content using HeyGen Video Agent.

## Prerequisites

- `HEYGEN_API_KEY` environment variable (set in ~/.zshrc)
- Essay or content to convert

## Video Configuration

| Setting | Value |
|---------|-------|
| Avatar | Master Control (suit): `4cadeeea56e14c05bb017756c98ca9a7` |
| Voice | Tom: `0356eda1a1414066bafac71d0f1e046c` |
| Orientation | Portrait (9:16) for LinkedIn/social |
| Background | Professional brick wall studio |
| Captions | Enabled |
| Duration | ~30 seconds |

## Content Structure

Each video follows a 4-scene structure:

| Scene | Duration | Purpose |
|-------|----------|---------|
| Hook | 4-5 sec | Attention-grabbing opening |
| Problem | 8 sec | State the challenge |
| Solution | 12 sec | Key insight or approach |
| CTA | 5-6 sec | Actionable takeaway |

### Example Script Structure

```
Scene 1 (Hook, 5 sec):
VO: "You decided AI is strategic. Now who gets it first?"

Scene 2 (Problem, 8 sec):
VO: "Most companies give licenses to everyone. That produces only 12% adoption."

Scene 3 (Solution, 12 sec):
VO: "The winners deploy deliberately. Customer support, engineering, finance. High-volume, repeatable work."

Scene 4 (CTA, 5 sec):
VO: "One team. Specific work. Start there."
```

## API Usage

### Create Video

```bash
curl -X POST "https://api.heygen.com/v1/video_agent/generate" \
  -H "X-Api-Key: $HEYGEN_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "prompt": "Create a 30-second LinkedIn/social video about [TOPIC]...\n\nGlobal Style:\n- Professional brick wall studio background\n- Clean, minimal modern aesthetic\n- Portrait orientation (9:16) for social media\n- Enable captions\n\nScene Structure:\n\nScene 1 (Hook, 5 sec):\nVO: \"[hook text]\"\n\nScene 2 (Problem, 8 sec):\nVO: \"[problem text]\"\n\nScene 3 (Solution, 12 sec):\nVO: \"[solution text]\"\n\nScene 4 (CTA, 5 sec):\nVO: \"[call to action]\"",
    "config": {
      "duration_sec": 30,
      "avatar_id": "4cadeeea56e14c05bb017756c98ca9a7",
      "orientation": "portrait"
    }
  }'
```

### Check Video Status

```bash
curl -s "https://api.heygen.com/v1/video_status.get?video_id=VIDEO_ID" \
  -H "X-Api-Key: $HEYGEN_API_KEY" | jq '.'
```

### Poll Until Complete

Status progression: `pending` → `processing` → `completed`

Poll every 60-90 seconds until `status: "completed"`.

### Download Video

When complete, the response includes:
- `video_url` — Main video
- `video_url_caption` — Video with burned-in captions (recommended for social)
- `gif_url` — Animated GIF preview
- `thumbnail_url` — Static thumbnail

```bash
# Download captioned version (best for social)
curl -o output-captioned.mp4 "$VIDEO_URL_CAPTION"
```

## Workflow

1. **Extract Key Points**: From essay content, identify hook, problem, solution, CTA
2. **Write Script**: Keep total duration ~30 seconds (count ~150 words max)
3. **Generate Video**: Submit to HeyGen Video Agent API
4. **Poll for Completion**: Wait for `status: "completed"`
5. **Download**: Get captioned video for social sharing
6. **Share**: Upload to LinkedIn, Twitter, etc.

## Script Writing Guidelines

### Hook (4-5 seconds)
- Start with a question or counterintuitive statement
- One clear sentence
- Make reader want to know more

### Problem (8 seconds)
- State the challenge clearly
- Use specific numbers when possible
- "Most companies..." or "The problem is..." patterns work well

### Solution (12 seconds)
- Give the key insight
- List 2-3 specific examples or steps
- Keep practical and actionable

### CTA (5-6 seconds)
- One clear action
- End with momentum, not "thanks for watching"

## Storage

Videos are stored in: `~/.openclaw/clu-space/artifacts/heygen-videos/`

Naming convention: `{content-slug}-captioned.mp4`

## Example: From Essay to Video

**Essay excerpt:**
> "Most companies get deployment wrong by giving licenses to everyone. That produces 12% adoption. The winners deploy deliberately to customer support, engineering, finance — high-volume, repeatable work. One team. Specific work. Start there."

**Video script:**
```
Scene 1: "Where do you start with AI?"
Scene 2: "Most companies give everyone licenses. That produces 12% adoption."
Scene 3: "The winners deploy deliberately. Customer support, engineering, finance. High-volume, repeatable work."
Scene 4: "One team. Specific work. Start there."
```

## Notes

- Video Agent typically takes 2-5 minutes to generate
- Portrait (9:16) is optimized for LinkedIn/mobile
- Captions are burned into the video, not separate
- Background is HeyGen's built-in brick wall studio
- Avatar uses natural gestures and expressions