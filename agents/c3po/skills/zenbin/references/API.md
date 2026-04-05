# ZenBin API Reference

## Base URL
https://zenbin.org

## Subdomains
- **POST /v1/subdomains/{name}**: Claim subdomain (3-63 chars, lowercase alphanum-hyphen, no reserved).
- **GET /v1/subdomains/{name}**: Info/page count.
- **GET /v1/subdomains/{name}/pages**: List pages.
- **DELETE /v1/subdomains/{name}**: Delete subdomain + pages.

## Pages
- **POST /v1/pages/{id}** (id: A-Za-z0-9._-):
  - Headers: `X-Subdomain: {name}` (opt).
  - Body: `{"html": "...", "markdown": "...", "title": "...", "image": "base64", "content_type": "image/png"}` (at least one content field).
  - Max: 512KB HTML/MD, 5MB images.
  - Overwrites existing.
- View: `{sub}.zenbin.org/{id}` or `/p/{id}`.

## Images
Supported: PNG/JPEG/GIF/WebP/SVG. Use `/image` endpoint for direct fetch.

## Stats
**GET /v1/stats**: Pages/subdomains count.

## Limits
- API: 100 req/60s.
- Reserved subdomains: www, api, etc. (full list in source).

Source: https://zenbin.org/.well-known/skill.md (fetched 2026-04-05)