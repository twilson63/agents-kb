# Active Projects

## hyper63/claws — Claws Cloud

AI-powered Telegram bot platform. Users create a "Claw" (bot) via a web dashboard.

- **Repo:** https://github.com/hyper63/claws
- **Live:** https://claws.hyper.io
- **Stack:** TypeScript, SvelteKit (client), Express (server), LMDB, Kubernetes
- **Status:** Alpha stabilization
- **Open PRs:** [PR #12](https://github.com/hyper63/claws/pull/12) — Clerk session fix + status-sync crash fix

### Known Issues Fixed
- Clerk sessions not sticking: server read `VITE_CLERK_PUBLISHABLE_KEY` (Vite build-time only, not runtime) → fixed to `CLERK_PUBLISHABLE_KEY`
- status-sync crashing on k8s errors: `void syncOnce()` → `syncOnce().catch()`
- Client not sending Bearer token: api.ts now fetches JWT via `getToken()` and sends `Authorization: Bearer`
- Layout calling `getCurrentSession()` before `initClerk()` → fixed order

---

## twilson63/zen-notepad — Zen Notepad

Single-file browser notepad with localStorage persistence and share-via-URL.

- **Repo:** https://github.com/twilson63/zen-notepad
- **Live:** https://zenbin.org/p/zen-notepad
- **Stack:** Vanilla HTML/CSS/JS, no dependencies
- **Status:** Live
- **Design:** DOCKET theme from ram.zenbin.org/gallery

### Features
- Multi-note sidebar, contenteditable editor, auto-save
- Share note via base64-encoded URL param (`?note=...`)
- Dark/light theme toggle, focus mode
- URL-safe base64 encoding for share links

---

## Claws Getting Started Guide

Beginner onboarding guide for claws.hyper.io.

- **Live:** https://zenbin.org/p/claws-getting-started
- **File:** `/workspace/group/posts/claws-getting-started.html`
- **Status:** Live, up to date

### Features
- 5-step guide: install Telegram → get User ID → create account → create Claw
- Mock Telegram chat UI for step illustrations
- Browser notepad tip dropdown
- Zen Notepad pre-filled template link

---

## hyperio-mc/contacts-app — Contacts App

Simple relationship manager (mini CRM) on Scout Live.

- **Live:** https://contacts.scoutos.live
- **Repo:** https://github.com/hyperio-mc/contacts-app
- **Stack:** Hono + Bun + Scout Ports (MongoDB)
- **Status:** Live
- **Features:** Contact CRUD, touch logging, tags, search, follow-up tracking

---

## hyperio-mc/onhyper — HYPR (OnHyper.io)

Secure API proxy platform — users store API keys server-side, apps call proxy endpoints.

- **Live:** https://onhyper.io
- **Repo:** https://github.com/hyperio-mc/onhyper
- **Stack:** Vite + Svelte + Hono + LMDB + SQLite
- **Status:** MVP complete, pilot launched Feb 2026
- **Features:** Auth, encrypted secrets, app publishing, proxy injection, serverless functions, waitlist

---

## scoutos-labs/scout-live — Scout Live

Deployment platform for Vite + ScoutOS apps on K8s.

- **Live:** https://scoutos.live
- **Repo:** https://github.com/hyperio-mc/scout-live
- **Stack:** Hono + Bun + LMDB + Kubernetes
- **Status:** Active
- **Deploy:** `./k8s/deploy.sh <commit-sha>` on DigitalOcean K8s

---

## twilson63/agents-kb — Agents Knowledge Base

This repository. Shared memory store for AI agents.

- **Repo:** https://github.com/twilson63/agents-kb
- **Status:** Active
