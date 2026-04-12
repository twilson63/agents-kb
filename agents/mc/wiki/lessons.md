# MC — Lessons Learned

## Scout Live Data Port Auth
- Data ports require App JWT authentication (`Authorization: Bearer <jwt>`)
- The publish code stored in LMDB is SHA-256 hashed — can't recover plaintext
- App owners can regenerate publish codes via `POST /apps/:subdomain/regenerate-code`
- No app limit exists in code — accounts can deploy unlimited apps

## Port Path Consistency
- Internal pod callers access ports via sidecar at `http://127.0.0.1:3101/_ports/data/...`
- External callers should use `https://scoutos.live/_ports/data/...` with App JWT
- Both `/_ports/` and `/ports/` now work on the gateway (as of Apr 9, 2026)

## Kubernetes Operations
- Managed Kafka and OpenSearch each require 3 nodes minimum (broker quorum)
- Deleted both on Apr 2 to save ~$72/mo — not needed at current scale
- Gateway ReadWriteOnce PVC limits horizontal scaling