# Bamaboy101 — AI Automation Portfolio

Four recruiter-ready, independently deployable AI automation MVPs. Each application is live and accessible from any browser without login or installation.

## Live Applications

| Project | Live App | Backend API | GitHub Repo |
|---------|----------|-------------|-------------|
| **[MarketMesh AI](https://bamaboy101.github.io/marketmesh-ai/)** | [Open Dashboard →](https://bamaboy101.github.io/marketmesh-ai/) | [API](https://marketmesh-api.marketmesh-api.workers.dev) | [Repo](https://github.com/Bamaboy101/marketmesh-ai) |
| **[AgentGuard AI](https://bamaboy101.github.io/agentguard-ai/)** | [Open Dashboard →](https://bamaboy101.github.io/agentguard-ai/) | [API](https://agentguard-api.marketmesh-api.workers.dev) | [Repo](https://github.com/Bamaboy101/agentguard-ai) |
| **[ActionFlow AI](https://bamaboy101.github.io/actionflow-ai/)** | [Open Demo →](https://bamaboy101.github.io/actionflow-ai/) | [API](https://actionflow-api.marketmesh-api.workers.dev) | [Repo](https://github.com/Bamaboy101/actionflow-ai) |
| **[BusinessFlow AI](https://bamaboy101.github.io/businessflow-ai/)** | [Open Dashboard →](https://bamaboy101.github.io/businessflow-ai/) | [API](https://businessflow-api.marketmesh-api.workers.dev) | [Repo](https://github.com/Bamaboy101/businessflow-ai) |

## What Each Project Does

### MarketMesh AI — Unified Market Intelligence Dashboard

Multi-asset watchlist (crypto, stocks, commodities) with explainable, rule-based signals (RSI-14 threshold and moving-average cross). Signal events include rule version, input hash, UTC timestamp, and evidence. Stale-data fail-safe suppresses signals on stale data. Idempotent alert previews with n8n webhook payload. No live trading, no broker connections.

**Stack:** TypeScript, React, Cloudflare Workers, D1, Binance public API (read-only demo)

### AgentGuard AI — Agent Monitoring & Incident Recovery

Service registry with heartbeat intake and last-seen health tracking. Missed-heartbeat and burst-failure detection with deduplication. Incident lifecycle: open → acknowledge → resolve, with audit trail (actor/time/reason). Demo simulator to start/stop/fail heartbeat emitters. No remote shell, reboot, or production restart — recovery requires explicit approval.

**Stack:** TypeScript, React, Cloudflare Workers, D1

### ActionFlow AI — Document Processing & Task Automation

Paste-text and PDF document ingestion with deterministic extraction of dates, times, tasks, parties, and requirements. Timezone and ambiguity flags — no guessed timezones. Review/edit/approve/reject each suggested action. Local ICS calendar export or task-checklist download. Idempotent export; no export of unreviewed actions. No automatic sending without consent.

**Stack:** TypeScript, React, Cloudflare Workers, D1, PDF text extraction

### BusinessFlow AI — Customer Inquiry & Approved Replies

Customer inquiry intake with intent classification (sales/support/billing/escalation). Policy/FAQ lookup with source IDs and revision. Grounded draft replies citing matched policy; unsupported claims flagged. Approve/escalate with operator audit trail. Sandbox CRM activity (deduplicated); simple queue metrics. No live CRM mutation or customer email send by default.

**Stack:** TypeScript, React, Cloudflare Workers, D1

## Architecture (All Four Projects)

- **Frontend:** React + Tailwind CSS, hosted on GitHub Pages
- **Backend:** Cloudflare Workers (Hono) + D1 databases (one per project)
- **Authentication:** None — anonymous, isolated demo sessions
- **Data:** D1 SQLite (persistent, isolated per project)
- **Live data:** MarketMesh uses public Binance API (read-only, labeled demo/live)
- **Cost:** $0/month (all free tiers)

## Security & Data Principles

- **No credentials stored** — `.env.example` files contain placeholder values only
- **No live trading** — MarketMesh is read-only market data
- **No external communications** — ActionFlow and BusinessFlow require explicit user approval before any export/send
- **No remote shell or reboot** — AgentGuard recovery requires explicit approval
- **Demo data labeled** — all data marked `demo: true` or `rights_tag: 'demo'`
- **Deterministic rules only** — no claimed live AI inference

## Repositories

Each repo contains: source code, README, architecture docs, installation guide, sample configuration, tests, screenshots, license, and release notes.

- **MarketMesh AI:** https://github.com/Bamaboy101/marketmesh-ai
- **AgentGuard AI:** https://github.com/Bamaboy101/agentguard-ai
- **ActionFlow AI:** https://github.com/Bamaboy101/actionflow-ai
- **BusinessFlow AI:** https://github.com/Bamaboy101/businessflow-ai

## How to Run Locally

```bash
# Any project (ports 4001-4004)
cd <project>/apps/api
npm install
npx tsx src/index.ts   # local Express backend
# Or deploy to Cloudflare Workers:
# npx wrangler deploy
```

## License

MIT License — see individual repository LICENSE files.
