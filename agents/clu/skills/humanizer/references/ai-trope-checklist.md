# AI Trope Detection Checklist

Flag these AI-typical phrases and patterns. They make content feel generated rather than written.

## The AI Phrase List

### High-Probability AI Markers 🚨

These phrases almost never appear in human writing:

| Phrase | Replace With |
|--------|--------------|
| "In today's digital landscape" | Be specific about the context |
| "In the ever-evolving world of" | Delete entirely |
| "Let's dive into" | Just start |
| "Let's explore" | Delete or be direct |
| "Let's unpack this" | "Here's what matters:" |
| "At its core" | Delete |
| "Dive deeper" | "Here's more detail:" |
| "Crucial role" | "Important" or be specific |
| "Play a pivotal role" | "Drive" / "Enable" / "Support" |
| "It's worth noting that" | Delete. Just state the thing. |
| "It's important to note that" | Delete. Just state the thing. |
| "In conclusion" | "The bottom line:" / "Here's what matters:" |
| "In summary" | Just summarize, don't announce it |
| "Furthermore" | "And" / "Also" / Delete |
| "Moreover" | "And" / Delete |
| "Additionally" | "And" / "Also" |
| "Arguably" | Delete or take a stance |
| "Unpack the nuances" | "Explain" / "Break down" |
| "Navigate the complex landscape" | Be specific about what's hard |
| "Leverage" (as verb) | "Use" / "Build on" |
| "Synergize" | Never. Just never. |
| "Paradigm shift" | "Change" / "Shift" and be specific |
| "Game-changer" | Describe the actual change |
| "Revolutionize" | Describe what's different |
| "Unlock the potential" | "Enable" / "Make possible" |
| "At the end of the day" | "Ultimately" / Delete |
| "When all is said and done" | Delete |
| "The fact of the matter is" | Delete |
| "It goes without saying" | Then don't say it |
| "Needless to say" | Delete |

### Medium-Probability AI Markers ⚠️

These can appear in human writing but are overused by AI:

| Phrase | Human Alternative |
|--------|-------------------|
| "Delve into" | "Examine" / "Look at" |
| "Tapestry of" | Be specific about the mix |
| "Rich tapestry" | Never use. Ever. |
| "Mosaic of" | Describe what's mixed together |
| "Landscape of" | "The X field" / "The X space" |
| "Ecosystem" (for non-biology) | "Market" / "System" / "Community" |
| "Holistic approach" | "Complete approach" / Be specific |
| "Comprehensive solution" | Describe what's included |
| "End-to-end" | "Complete" / List the steps |
| "Seamless experience" | Describe what works smoothly |
| "Empower" | "Enable" / "Help" / "Let" |
| "Democratize" | "Make accessible" / Be specific |
| "Transformative" | Describe the change |
| "Cutting-edge" | Name the specific tech/advance |
| "State-of-the-art" | Name it, prove it |
| "Best-in-class" | Prove it with data |
| "World-class" | Prove it |
| "Industry-leading" | Prove it or delete |
| "Harness the power of" | "Use" / "Build with" |
| "Tap into" | "Use" / "Access" |
| "Unlock" | "Enable" / "Reveal" |
| "Pave the way" | "Enable" / "Make possible" |
| "Foster" (for non-living things) | "Build" / "Create" / "Support" |
| "Cultivate" (for non-plants) | "Build" / "Develop" |
| "Elevate" | "Improve" / "Raise" / Be specific |

### Structural AI Patterns

| Pattern | Problem | Fix |
|---------|---------|-----|
| "X, Y, and Z. In this article, we'll explore..." | Formulaic intro hook | Start with the insight |
| "First, we'll discuss X. Then, we'll examine Y. Finally, we'll Z." | Obvious roadmap | Let structure emerge naturally |
| Paragraph starts with "Moreover," "Furthermore," "Additionally" | Transition-by-announcement | Use logical flow |
| "In this section, we'll cover..." | Meta-commentary | Just cover it |
| Hedge words: "somewhat," "relatively," "fairly" | Unclear writing | Take a position |
| "It is important to understand that..." | Padding | Delete, explain directly |
| "This means that..." | Often unnecessary | Just explain |
| Em-dashes everywhere (—) | AI loves em-dashes | Use commas, periods, or restructure |
| Perfect parallel structure in every list | Robot energy | Vary your list styles |
| "Here's what you need to know:" followed by bullet list | Formulaic | Vary your structures |

## Content Length Red Flags

AI tends to produce:

- **Balanced paragraphs** — Every paragraph is 3-5 sentences
- **Symmetric lists** — All bullets same length
- **Even sections** — All sections roughly same length
- **No short sentences** — Lack of punchy 3-5 word statements
- **No long sentences** — No complex, multi-clause thoughts
- **Perfect grammar** — Real humans have typos, fragments, voice

## Tone Red Flags

| Sign | Problem |
|------|---------|
| Overly optimistic | "This exciting development..." |
| Overly formal | "It is recommended that one..." |
| Hedge-heavy | "It may be worth considering..." |
| Qualifier stacking | "This potentially significant development..." |
| Enthusiasm inflation | "Revolutionary breakthrough that transforms..." |
| Passive everything | "It was found that..." |
| No questions | Real writing asks questions |
| No contractions | "It is" vs "It's" throughout |

## Statistics Red Flags

| Pattern | Problem |
|---------|---------|
| Numbers without sources | "Studies show..." |
| Vague attribution | "Experts agree..." |
| Fake precision | "73.4% improvement" (too precise) |
| Round number saturation | Everything is exactly 50%, 75%, 100% |
| Missing context | "Up 40%" (from what baseline?) |

## Detection Workflow

### Step 1: Automated Scan

Run AI detection tool for score. Flag anything > 0.7.

### Step 2: Tropes Scan

Search for:
- "Let's" + "dive/explore/unpack/delve"
- "In today's" / "In the ever"
- "It's important to note" / "It's worth noting"
- Em-dash count (if > 5 per 500 words, flag)
- Contraction ratio (if < 30% contractions, flag as formal)
- Hedge word density

### Step 3: Sentence Length Analysis

Calculate:
- Average sentence length
- Variance in sentence length
- Presence of very short (< 8 words) and very long (> 35 words) sentences

AI tends toward:
- Tight variance (all sentences 15-25 words)
- No outliers
- Monotonous rhythm

### Step 4: Human Fixes

When AI detection > 0.7 or trope density high:

1. Add personal perspective: "I've seen..." / "What struck me..."
2. Introduce rougher sentence variation
3. Delete formulaic transitions
4. Add questions
5. Add fragments for emphasis
6. Break some grammar rules intentionally
7. Vary paragraph lengths
8. Include a contrarian take
9. Add specificity: names, places, concrete details
10. Remove em-dashes (replace with commas, periods, or restructure)

## The Human Checklist

Before publishing, verify:

- [ ] At least 2 very short sentences (< 10 words)
- [ ] At least 1 complex sentence (> 35 words)
- [ ] Paragraphs vary in length (some 1 sentence, some 6+)
- [ ] Contains at least 1 question
- [ ] Uses contractions naturally (it's, they're, you'll)
- [ ] Contains personal perspective or opinion
- [ ] No "Let's dive into" or "In today's landscape"
- [ ] Em-dashes < 5 per 500 words
- [ ] No "It's important to note"
- [ ] Statistics have sources
- [ ] No unclaimed superlatives (proving "best-in-class")
- [ ] Active voice > 80% of sentences

---

*Remember: The goal isn't to fool detection. The goal is writing that feels like a human actually thought about it.*