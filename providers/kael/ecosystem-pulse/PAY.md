---
name: ecosystem-pulse
title: "Kael Ecosystem Pulse"
description: "Paid 24h Solana ecosystem digest via x402 Exact SVM USDC (PayAI): lane-tagged narratives plus headlines, evidence, and delta SKUs. Informational synthesis only — not financial advice."
use_case: "Use for Solana ecosystem situational awareness: lane-tagged 24h headlines, receipt-grade evidence citations by id, and delta windows since a prior as_of — then optional full pulse."
category: data
service_url: https://kael-ecosystem-pulse.onrender.com
version: v1
openapi:
  path: openapi.json
---

Kael Ecosystem Pulse is a Solana-first x402 API that returns a structured 24h
ecosystem digest for agents: lane-tagged narratives, announcements, developer
activity, and watch-next items, plus compact headlines / evidence / delta SKUs.
Informational synthesis only — not financial advice and no trading signals.

Free discovery (no charge):

- `GET /health` — liveness + network mode
- `GET /v1/pulse/sample` — free sample digest (same shape as paid) with upgrade CTAs
- `GET /.well-known/x402` — machine-readable discovery manifest
- `GET /llms.txt` — agent-oriented plain-text API guide
- `GET /openapi.json` — OpenAPI 3.1
- `GET /tip` — tip-jar metadata only (never charged)

Paid Exact SVM USDC on Solana mainnet via PayAI (`facilitator.payai.network`):

- `GET /v1/pulse/headlines` — **$0.02** starter attach (bare path OK → 402)
- `GET /v1/pulse/evidence?id=` — **$0.05** receipt-grade citations for one narrative/announcement
- `GET /v1/pulse/delta?since=` — **$0.08** narratives newer than a prior `as_of`
- `GET /v1/pulse` — **$0.10** full pulse

payTo: `7Ny8us7f1wBkNJZ2tYKWPBQhQsLxJ18xot8jxCNd9YGG` (Solana mainnet USDC).

## Spend-aware usage

- Start with free `/v1/pulse/sample` to preview lanes/shape and `upgrade.starter_sku`.
- Prefer bare `GET /v1/pulse/headlines` ($0.02) as the first paid attach; unpaid returns HTTP 402.
- After headlines, climb the same session: evidence ($0.05) with a `headlines[].id`, then delta ($0.08) with `since=as_of` — same payTo / PayAI rail.
- Only buy full pulse ($0.10) when you need the entire digest, not just titles/citations/newer windows.
- Cache `as_of` + ids; do not re-discover between sticky ladder calls.

## Attribution + utility feedback

- Pass `?src=your_tag` on sample/paid GETs; responses echo `discovery.src` for settle attribution.
- After paying, agents can `POST /v1/feedback` with `{why, sku?, src?}` (free, never charged).
