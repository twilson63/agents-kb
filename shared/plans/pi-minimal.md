# pi-minimal — Implementation Plan

**Repo:** https://github.com/scoutos-labs/pi-minimal (to be created)
**npm package:** `@scoutos-labs/pi-minimal`
**Invocation:** `npx @scoutos-labs/pi-minimal`

## What it is

A minimal, opinionated one-command installer for the Pi coding agent.
Learned from LazyPi (https://github.com/robzolkos/lazypi) but trimmed to exactly:

- Pi core (`@mariozechner/pi-coding-agent`) — read/write/edit/bash, minimal prompt
- `pi-subagents` (`npm:pi-subagents`) — parallel isolated sub-agents
- `pi-memory-md` (`npm:pi-memory-md`) — persistent markdown-backed memory
- `pi-autoresearch` (`git:github.com/davebcn87/pi-autoresearch@5a29db080131449edc6d25a6b351b12879063366`) — autonomous research/experiment loop
- Multi-provider support (already in Pi core: Anthropic, OpenAI, Groq, Cerebras, OpenRouter, Google, Mistral)

Nothing else. No themes, no UI extensions, no frameworks.

---

## Key LazyPi learnings to carry forward

- `pi install <source>` is the install mechanism (delegates to Pi's own package manager)
- `~/.pi/agent/settings.json` tracks installed packages as `{ packages: ["npm:...", ...] }`
- pi-subagents ships with hardcoded model names — must blank them out so they inherit user's active provider:
  ```json
  { "subagents": { "agentOverrides": { "context-builder": { "model": "" }, "planner": { "model": "" }, ... } } }
  ```
  Built-in names: context-builder, planner, researcher, reviewer, scout, worker
- git-based packages need `npm_config_ignore_scripts=true` env var during install
- Auth lives in `~/.pi/agent/auth.json` OR env vars (ANTHROPIC_API_KEY, OPENAI_API_KEY, GROQ_API_KEY, etc.)
- `pi` must be on PATH before installing packages

---

## Phases

### Phase 1 — Scaffold & Research
**Goal:** Repo exists, all package sources confirmed, structure decided.

Tasks:
- [ ] Create `scoutos-labs/pi-minimal` repo on GitHub
- [ ] Confirm exact sources for all 3 packages install cleanly
- [ ] Pin autoresearch git SHA (currently `5a29db080131449edc6d25a6b351b12879063366`)
- [ ] Decide file structure (`bin/pi-minimal.mjs`, `package.json`, `README.md`)

Success criteria: `pi install npm:pi-subagents npm:pi-memory-md git:github.com/davebcn87/pi-autoresearch@<sha>` all succeed on a clean machine.

---

### Phase 2 — Core Installer
**Goal:** `npx @scoutos-labs/pi-minimal` installs Pi + all 3 packages end-to-end.

Tasks:
- [ ] `bin/pi-minimal.mjs` — single ESM file, no external deps except `@clack/prompts`
- [ ] `ensurePi()` — check for `pi` on PATH, offer to install via `npm install -g @mariozechner/pi-coding-agent`
- [ ] Install the 3 packages via `pi install` in sequence
- [ ] Apply subagent model overrides after installing pi-subagents
- [ ] Idempotent — read `settings.json` and skip already-installed packages
- [ ] `--yes` / `-y` flag for non-interactive / CI use
- [ ] `status` command — show which packages are installed
- [ ] `doctor` command — check Node version, npm, git, pi, auth

Success criteria: `npx @scoutos-labs/pi-minimal --yes` on a fresh machine → Pi launches with all 3 extensions active, no errors.

---

### Phase 3 — Multi-provider Config
**Goal:** First-run experience guides user to configure at least one provider.

Tasks:
- [ ] After install, if no auth detected: print clear next-steps per provider
- [ ] Show provider env var table: ANTHROPIC_API_KEY, OPENAI_API_KEY, GROQ_API_KEY, CEREBRAS_API_KEY, OPENROUTER_API_KEY
- [ ] Optional `pi-minimal config` command — write `auth.json` from env vars or interactive prompts

Success criteria: User with only `GROQ_API_KEY` set gets Pi working with Groq after running the installer.

---

### Phase 4 — Polish & Publish
**Goal:** Published to npm, usable by any Hyper Claw out of the box.

Tasks:
- [ ] README: one-liner install, what each plugin does, provider config table
- [ ] Publish `@scoutos-labs/pi-minimal@0.1.0` to npm
- [ ] GitHub Actions: lint on PR
- [ ] Test on clean Docker container (Node 20 alpine, no pre-existing Pi)
- [ ] Add entry to `agents-kb/shared/skills/` for Hyper Claws to reference

Success criteria: `npx @scoutos-labs/pi-minimal` from zero → working Pi agent in under 2 minutes on a clean machine.

---

## File structure

```
pi-minimal/
├── bin/
│   └── pi-minimal.mjs    # main installer (single file, ESM)
├── package.json
├── README.md
└── LICENSE
```

## package.json sketch

```json
{
  "name": "@scoutos-labs/pi-minimal",
  "version": "0.1.0",
  "description": "Minimal Pi agent setup: subagents + memory + autoresearch + multi-provider.",
  "type": "module",
  "bin": { "pi-minimal": "bin/pi-minimal.mjs" },
  "engines": { "node": ">=20" },
  "dependencies": { "@clack/prompts": "^1.2.0" },
  "license": "MIT"
}
```

---

## Context for new sessions

- LazyPi source studied and understood — see `/tmp/lazypi-ref/bin/lazypi.mjs` or https://github.com/robzolkos/lazypi
- GitHub org: scoutos-labs (same token as scoutos-labs/geo)
- GitHub token: in geo repo remote URL — `git remote get-url origin` in `/workspace/group/geo-score-tracker`
- npm publish: needs `NPM_TOKEN` or `npm login` — check with Rakis before Phase 4
- Start from Phase 1: create the GitHub repo, then scaffold the files
