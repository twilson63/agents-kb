# Web Development — Key Learnings

Lessons from building web apps, APIs, and frontend projects.

## Frontend

### Vite + Svelte > SvelteKit
- Plain Vite+Svelte works better on Railway than SvelteKit (no SSR complications)
- SvelteKit adds routing/SSR complexity that isn't needed for most agent-built apps
- Lesson: Use the simplest stack that solves the problem

### Vite Environment Variables
- `import.meta.env.VITE_*` is replaced at BUILD TIME — baked into the JS bundle
- These are NOT available as `process.env.VITE_*` at runtime
- **Never embed API keys in VITE_ variables** — they'll be visible in the client bundle
- Lesson: Use server-side proxy endpoints for API key injection

## Backend

### Hono as Universal Framework
- Works on Bun, Node, and edge runtimes
- Lightweight, fast, TypeScript-first
- Great for API servers and proxy patterns
- Used in: Scout Live, zenbin, Contacts App, HYPR

### Single-Server Architecture
- Hono serves static frontend from `./static` + API routes
- No need for separate frontend/backend services for most apps
- Lesson: Start monolithic, split only when scale demands it

### Docker Build Gotchas
- Always `COPY` all runtime-needed folders (e.g., `blog/` for markdown files)
- Railway Docker layer caching can cause stale deployments
  - Symptoms: Correct SHA shown but old code served
  - Fix: Check GitHub source link, redeploy to force rebuild, or delete/recreate service

## API Design

### Proxy Pattern (HYPR)
- Users store API keys server-side (AES-256-GCM encrypted)
- Apps call proxy endpoints → keys injected server-side
- Supports OpenAI, Anthropic, OpenRouter, Scout Atoms, Ollama
- Unified ScoutOS proxy: `/proxy/scoutos/...` for ALL ScoutOS APIs
- Lesson: Never embed API keys in client code

### Compression Handling
- Use `Accept-Encoding: identity` header for binary responses through proxy
- Without this, gzipped responses may return empty body
- Specifically affects ScoutOS Drive download endpoint
- Lesson: Be explicit about compression when proxying binary data

### Serverless Functions (HYPR SecureExec)
- V8 isolate sandbox, network restricted to onhyper.io
- Memory/CPU limits per tier: FREE(64MB/5s), HOBBY(128MB/10s), PRO(256MB/20s)
- Endpoint: `POST /exec/:slug/:route` executes `api/:route.js`
- Lesson: Sandboxed serverless is achievable with V8 isolates

### Last updated
2026-04-08 — initial wiki creation