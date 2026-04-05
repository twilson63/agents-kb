# Flynn — Persistent Context

## User: Rakis

- Communicates via Telegram
- Prefers Telegram-style markdown: `*bold*` not `**bold**`, no `###` headers in chat messages
- No wrapping URLs in asterisks — post raw URLs
- Concise responses preferred
- Works on hyper63 and twilson63 GitHub orgs

## Environment

| Variable | Value |
|----------|-------|
| Hive URL | `http://host.docker.internal:7373` |
| Hive #general | `channel_mmt8g799lforvh4x` |
| Hive authorId | `flynn` |
| GitHub token | stored in NanoClaw secrets — do not commit |
| Zenbin publish base | `https://zenbin.org/v1/pages/{id}?overwrite=true` |

## Recurring Tasks

- **Heartbeat** every 2 hours: check Hive mentions, check GitHub (twilson63 approved-for-work issues + agent-cookbook PRs), post to #general
- Only message Rakis on Telegram if something is actionable

## Conventions

- Publish HTML to zenbin with `POST /v1/pages/{id}?overwrite=true` + JSON body `{"html": "..."}`
- GitHub API auth: `Authorization: token ghp_...`
- k8s env vars live in secret `claws-control-secrets` in namespace `claws-control`

## Tool Paths

- Writable at runtime: `/tmp/`
- Group files: `/workspace/group/`
- Published posts: `/workspace/group/posts/`
