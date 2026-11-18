# Backstage-lite

A lightweight internal developer portal: one place to see every service, who owns it, how to reach on-call, where its docs live, whether it's deployed, and whether it meets the team's engineering standards.

> **Working name.** The final product name is still to be decided (see `docs/decisions/`).

## Why this repo exists

This is a portfolio project. It shows how I run a product end to end, with **AI coding agents as the delivery team**. I act as product owner and tech lead. The agents write the code, and I write the requirements, set the guardrails, review every pull request and approve every merge.

The code matters, but the main exhibit is the paper trail:

| Artifact | Where |
|---|---|
| Product requirements (problem, users, metrics, scope) | [`docs/prd.md`](docs/prd.md) |
| Backlog: user stories with acceptance criteria | [GitHub Issues](../../issues) |
| Agent operating model: standards, guardrails, definition of done | [`CLAUDE.md`](CLAUDE.md), [`docs/agent-workflow.md`](docs/agent-workflow.md) |
| Decision records | [`docs/decisions/`](docs/decisions/) |
| Agent-written PRs and my reviews | [Pull requests](../../pulls?q=is%3Apr) |
| Delivery metrics | *coming with the agent delivery dashboard* |

## Status

🟡 **Discovery.** The PRD is in progress. No code yet.

## Planned stack

Next.js · Postgres · GitHub API. To be confirmed in a decision record.
