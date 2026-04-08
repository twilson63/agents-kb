# DevOps & Operations — Key Learnings

Lessons from deploying, monitoring, and maintaining production systems.

## Railway

### Preferred Deployment Platform
- Rakis prefers Railway over Fly.io for simplicity
- Push-to-deploy workflow (connect GitHub repo → auto-deploy on push)
- Use `railway.toml` with `[[volume]]` config for persistent storage

### Common Issues
- **Stale Docker builds**: Railway Docker layer caching can serve old code even with correct SHA
  - Fix: Force rebuild via redeploy, or delete/recreate service
- **Missing COPY in Dockerfile**: Always `COPY` runtime-needed folders
  - Example: Forgot `COPY blog/` → markdown blog routes 404'd
- **Volumes**: Must use `railway.toml` with `[[volume]]` for persistent storage

## Kubernetes (DigitalOcean)

### Scout Live K8s
- Namespace: `scout-live`
- Deploy: `./k8s/deploy.sh <commit-sha>`
- Single node (s-2vcpu-4gb) after cost optimization
- Gateway uses ReadWriteOnce PVC → no horizontal scaling

### Monitoring
- `kubectl get pods -n scout-live`
- `kubectl logs deployment/scout-live-gateway -n scout-live --tail=20`
- Check for orphaned PVCs: `kubectl get pvc -n scout-live`

### Lesson: K8s for Agents
- Full K8s is overkill for most agent workloads
- Consider simpler deployment targets (Railway, Fly.io) first
- Reserve K8s for when you need multi-app orchestration or custom networking

## Authentication & Security

### JWT Verification
- Had a bug in contacts app JWT verification — always test auth flows end-to-end
- Scout Live admin auth middleware requires production secret validation

### API Key Management
- ScoutOS API key: `secret_mIDCpkqg0LOAHUpVvIoNLFSeX2DNxVfe3tA_DCGasAY=` (Free tier)
- GitHub PAT: expires Apr 13, 2026
- PostHog: `phc_Rmreg0D8BwNcOzOMUXoUW8B0ilMzR1hw1Kk0Y8jKt9q` (Project 314488)
- Lesson: Track expiry dates and rotate before they expire

## Monitoring & Observability

### Health Checks
- Scout Live has a cron-based health check that reports: node status, pod health, PVC status, gateway probes
- Gateway probes occasionally timeout — needs investigation but not critical

### Analytics
- PostHog for pageviews, login, signup, app creation, waitlist signups
- Lesson: Instrument early — you can't analyze what you don't track

### Last updated
2026-04-08 — initial wiki creation