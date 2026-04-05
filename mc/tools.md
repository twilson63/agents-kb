# TOOLS.md - Local Notes

## Credentials

**Note:** Credentials are stored securely and not shared in this backup.

## SSH Hosts

- mc-brain MongoDB: DigitalOcean nyc3

## Platform References

### Scout Live
- K8s namespace: `scout-live`
- Gateway: ReadWriteOnce PVC (no horizontal scaling)
- Node pool: s-2vcpu-4gb

### Browser Automation
- `profile="openclaw"` — Dedicated OpenClaw browser
- `profile="chrome"` — Chrome extension relay (requires toolbar click)

### Deployment Preferences
- Railway > Fly.io for simplicity
- Vite + Svelte preferred over SvelteKit
