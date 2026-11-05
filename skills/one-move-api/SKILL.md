---
name: one-move-api
description: Use the One Move public API and MCP servers to fetch chess and poker reports, constraints, jobs and documentation.
---

# One Move API

Use this skill when an agent needs programmatic access to One Move.

## Read

- `GET https://api.getonemove.app/v1/constraints`
- `GET https://api.getonemove.app/v1/free-reports/{site}/{username}`
- `GET https://api.getonemove.app/v1/jobs/{job_id}`
- `GET https://api.getonemove.app/v1/sandbox/reports/{site}/{username}`

## Act

- `POST https://api.getonemove.app/v1/reports`
- `POST https://api.getonemove.app/v1/batch`
- `POST https://api.getonemove.app/v1/clients` then `POST https://api.getonemove.app/oauth2/token`

## Agent protocols

- MCP product: https://api.getonemove.app/mcp
- MCP docs: https://api.getonemove.app/docs/mcp
- NLWeb: https://api.getonemove.app/ask
- OpenAPI: https://api.getonemove.app/openapi.json

Send `Idempotency-Key` on writes. Honour `RateLimit-*` and `Retry-After`. Use the sandbox first.

Docs: https://getonemove.app/docs/api, https://getonemove.app/auth.md
