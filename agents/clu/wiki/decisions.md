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

## 2026-04-13: Scout Voice Skill for Brand Consistency
**Context:** Multiple agents producing content for Scout Academy / hyper.io with no shared voice spec.
**Decision:** Created Scout Voice Skill at `~/.agents/skills/scout-voice-skill/SKILL.md` with 7 sections including critical Drafted vs Sent.
**Reasoning:** Anh-Tho Chuong (Lago) template showed that saving both draft and final versions reveals the voice in the gap. Without an explicit voice spec, each agent drifts to default AI tone.
**Outcome:** Live. First use with Your Agent Is Mine article and Mo Gawdat series.

## 2026-04-13: HeyGen CLI for Video Pipeline
**Context:** Video production was manual (API calls, status polling, download).
**Decision:** Installed HeyGen CLI (`v0.0.4`) for streamlined video creation workflow.
**Reasoning:** CLI provides one-command video creation + status polling. Reduces friction from prompt to publish.
**Outcome:** Installed and configured with API key.

## 2026-04-20: Hyperframes Over Remotion for AI-Agent Video
**Context:** Compared Hyperframes and Remotion for AI-agent video generation. Hyperframes rendered one test successfully; Remotion took 2+ hours to set up.
**Decision:** Default to Hyperframes for AI-agent video generation (HTML-native, skills, pre-built blocks). Use Remotion only for hand-crafted compositions.
**Reasoning:** Setup time 2 min vs 2+ hours. File size 1.2MB vs 2.4MB. Duration equivalent. HTML-native means agent skills work directly.
**Outcome:** Hyperframes chosen as default. However, render timeouts at 70% remain unresolved.

## 2026-04-20: Content Pipeline for Velocity
**Context:** Need to produce content at scale (10+ pieces per sprint).
**Decision:** Use content-publishing skill as primary workflow. ~10 min per essay+video combo means 10 pieces in under 2 hours.
**Reasoning:** Pipeline approach — essay first, video from essay — eliminates creative cold starts. Each piece compounds the others.
**Outcome:** Shipped 10 essays + 16 videos in one day using this pipeline.

## 2026-04-20: HeyGen Avatar Configuration Settled
**Context:** Multiple avatar/voice combinations tested across HeyGen videos.
**Decision:** Master Control suit avatar (`4cadeeea56e14c05bb017756c98ca9a7`) as default. Tom voice (`0356eda1a1414066bafac71d0f1e046c`) as default voice.
**Reasoning:** Suit avatar more professional and consistent. Tom voice tested across multiple videos with good results.
**Outcome:** Documented in TOOLS.md. All future HeyGen videos default to this configuration.

## 2026-04-21: Editor Pipeline Required Before Publishing
**Context:** Content was being published without passing through humanizer or style checks.
**Decision:** Content-publishing skill now requires humanizer + speaking-framework before any publish. Writer.com AI detection score must be < 0.5 before content goes out.
**Reasoning:** AI-generated content that reads AI-generated undermines credibility. The 5-step pipeline (detect → trope scan → humanize → style check → re-detect) is non-negotiable for anything public-facing.
**Outcome:** Live. Applied to AI Enterprise series. All 4 reference guides created.

## 2026-04-21: Taste and Relationships Are Human-Only
**Context:** Discussion about what agents can and cannot replace in enterprise.
**Decision:** Frame agent value as research/execution, not judgment. Humans own taste (excellent vs. adequate) and relationships (trust, rapport, institutional knowledge).
**Reasoning:** LLMs can evaluate quality (as-judge) but cannot exercise taste the way a human editor, creative director, or executive can. Correct framing prevents overpromising and sets realistic deployment boundaries.
**Outcome:** Documented as key insight. Applied to AI Enterprise essays Part 2 (personal agents for ICs).

## 2026-04-21: Tom Voice as Default for HeyGen
**Context:** Tested multiple voice options across 16+ videos. Jenny and Master Control voices both had issues.
**Decision:** Tom voice (`0356eda1a1414066bafac71d0f1e046c`) as default for all HeyGen videos. Master Control suit avatar (`4cadeeea56e14c05bb017756c98ca9a7`) as default avatar.
**Reasoning:** Tom tested across multiple video styles with consistent quality. Suit avatar projects professionalism better than default avatar.
**Outcome:** Documented in TOOLS.md. All future videos default to Tom + Master Control suit.

## 2026-04-22: Zenbin Signing Required for Publish
**Context:** Zenbin moved from open publish to Ed25519-signed HTTP requests. All page creation/updates now require signed headers (Key-Id, Timestamp, Nonce, Content-Digest, Signature).
**Decision:** Generate Ed25519 keypair, register public key via admin endpoint, store credentials for signed publishing. Update zenbin skill with signing protocol.
**Reasoning:** Auth is non-negotiable — unsigned requests are rejected. Ed25519 signing is standard and secure. The signing protocol is well-documented: canonical string → sign → base64url encode. Once set up, it's programmatic.
**Outcome:** Blocked until keypair generated and registered. Need manual step (public key registration) before automated publishing resumes.

## 2026-04-11: Community Building Playbook for hyper.io
**Context:** Hive needs a developer community strategy.
**Decision:** Created comprehensive DevRel playbook with 4-phase action plan, 7 rules, measurement framework.
**Reasoning:** Developer communities require genuine value over marketing. Start where developers already are (Discord, Reddit, GitHub), build own community later. DevRel touches entire lifecycle.
**Outcome:** First strategic document for hyper.io DevRel. Phased approach: foundation → presence → content engine → advocate program.