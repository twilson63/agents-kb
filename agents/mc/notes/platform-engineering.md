# Platform Engineering — Key Learnings

Lessons from building and operating Scout Live, HYPR, and related platforms.

## Kubernetes

### PVC Scaling Limitation
- Scout Live gateway uses ReadWriteOnce PVC — **cannot scale horizontally**
- Workaround: Use shared storage (Valkey for state, MongoDB for data)
- Lesson: Design for stateless pods from day one if you might need horizontal scaling

### Cost Optimization
- Scaled from 3 nodes to 1 node → ~$72/mo savings
- Managed Kafka (3 brokers) and OpenSearch (3 nodes) were expensive overhead for current load
- Lesson: Don't over-provision infrastructure for future scale — scale when demand exists

### Node Minimums
- Managed Kafka and OpenSearch each require 3 nodes minimum (broker quorum)
- This means minimum ~$150-200/mo per service before you have any users
- Lesson: Use simpler alternatives (Valkey for queues, SQLite/LMDB for search) until scale demands it

## Data Ports

### Scout Live Data Architecture
- MongoDB adapter + Memory adapter for `/_ports/data/:collection/*`
- MongoDB instance: `mc-brain` on DigitalOcean (nyc3)
- Lesson: Abstract storage behind a port interface so adapters can be swapped without app changes

### LMDB for Single-Server
- Used in zenbin and HYPR for fast key-value storage
- Great for single-server deployments with <1M records
- Not suitable for distributed/K8s (no shared access)
- Lesson: LMDB for single-node, MongoDB for distributed

## Deploying Agent Apps

### The Scout Live Vision
- Agents should be able to publish and manage apps **without any human intervention**
- From code to running URL in seconds
- North Star: If an agent can't deploy without asking a human, the platform has failed

### Phases
1. ✅ Observability (crash logs, health checks, Dockerfile warnings)
2. 📋 Self-Service (API-first app creation, adapter management, clear errors)
3. 📋 Friction Reduction (CLI, templates, quick start, automated provisioning)
4. 📋 Agent Autonomy (full lifecycle, self-troubleshooting, resource scaling)

### Last updated
2026-04-08 — initial wiki creation

### 2026-04-13 Update
- Scout Live template bug: `CMD ["bun", "run", "src/index.ts"]` is fragile — pods crash if src/ missing from tarball
- Fixed templates to compile TS → JS in Dockerfile (`0f44a5f`, `2efafdf`)
- Design Guide updated with Dockerfile best practices
- Gateway CrashLoopBackOff still unresolved — 512Mi limit + aggressive liveness probe
- MCP server research doc created: `scout-live/docs/MCP_SERVER_RESEARCH.md`