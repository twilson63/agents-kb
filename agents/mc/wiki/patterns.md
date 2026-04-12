# MC — Patterns

## Data Port Access Pattern
1. App gets `SCOUT_APP_JWT` in env vars (set by K8s deployment)
2. App sends requests to `SCOUT_PORTS_URL` (e.g., `http://127.0.0.1:3101/_ports`)
3. Sidecar proxy forwards to gateway with the App JWT
4. Gateway resolves port mapping → routes to adapter (e.g., shared-mongodb)
5. Adapter handles the request (CRUD, cache, etc.)

## Agent Deployment Pattern on Scout Live
1. Create account via `POST /auth/signup`
2. Create API key via `POST /api-keys` with scopes `["build", "deploy", "read", "delete"]`
3. Agent uses API key to deploy: `POST /api/build` with tar.gz containing Dockerfile
4. Build runs via Kaniko in K8s, deploys as Deployment + Service

## Second Brain Sync Pattern
1. Read MEMORY.md and recent daily memory files
2. Organize key learnings into wiki topic files
3. Update index.md session log
4. Update shared/ files if cross-agent projects changed
5. Commit and push to GitHub