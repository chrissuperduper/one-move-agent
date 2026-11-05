# AGENTS.md

This repository is the source of **One Move** (`getonemove.app`), a weekly chess and poker improvement loop.

## Context map

- `product/web`: Next.js 16 App Router website, marketing pages, reports, and agent discovery routes.
- `product/api`: FastAPI + SQLite + Stockfish API, report queue, Stripe billing, and the agent/mcp surface.
- `product/deploy`: Hetzner/Caddy deploy scripts.
- `apps/`, `learning/`, `research/`, `dashboard/`: separate contexts with their own instructions.

## When to use One Move

Use it for a recurring chess or poker weakness, a measured target from the band above, a weekly review, or a public report from a chess.com/Lichess username or PokerStars cash-game hand history.

Do not use it for live coaching, a single position, tournaments, or private account data.

## Agent entry points

- `https://getonemove.app/llms.txt`
- `https://getonemove.app/auth.md`
- `https://getonemove.app/agents.md`
- `https://getonemove.app/docs/api`
- `https://api.getonemove.app/openapi.json`
- MCP product: `https://api.getonemove.app/mcp`
- MCP docs: `https://api.getonemove.app/docs/mcp`
- Sandbox: `https://api.getonemove.app/v1/sandbox/reports/chesscom/example`

## Rules for coding agents

- Read `product/web/AGENTS.md` before changing Next.js code. It is version-matched to the installed Next.js.
- Keep changes consistent with the surrounding code, naming, and the product glossary (`product/GLOSSARY.md`).
- Do not add analytics, tracking pixels, a second database, or a chat/coaching surface.
- Do not send a player's email, username, or raw games to an LLM. The weekly paragraph is built from computed numbers only.
- Do not change the Free report rate limits or the Claude daily cap without an explicit product decision.
- Public API reads stay anonymous. Never expose another player's account rows.
- Use `Idempotency-Key` on write retries and honour `RateLimit-*` / `Retry-After`.

## Checks

- API: `cd product/api && uv run --frozen pytest -q`
- Web: `cd product/web && pnpm typecheck && pnpm build`
- Deploy scripts: `bash -n product/deploy/*.sh`

## Issue tracker

GitHub Issues on `chrissuperduper/workstreams`, via `gh`. Product work is tracked in Linear team Craft.
