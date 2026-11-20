# 0004: Read-only Jira integration in the MVP; MVP moves to 2026-12-08

- **Status:** Accepted
- **Date:** 2026-11-17
- **Decider:** John Collins

## Context
Platform leads judge service health by standards compliance and by open defect load. Most engineering orgs track that load in Jira. Without it, the standards overview shows only half the risk picture. The MVP was scoped for 2026-12-01 without Jira.

## Options considered
1. **Defer Jira to v1:** protects 12-01, but the MVP's platform-lead story is weaker.
2. **Jira in the MVP, scope trimmed** (counts only, drop polish): keeps 12-01, but cuts features already promised.
3. **Jira in the MVP at full scope, MVP moves one week to 12-08:** keeps a complete story and an honest date.
4. **Everything by 12-01:** high risk of missing the date.

## Decision
We chose **option 3**: read-only Jira integration in the MVP, with the MVP date moving from 2026-12-01 to **2026-12-08** (v1 to ~12-22). A complete platform-lead story matters more than one week, and moving the date on purpose is better than missing it by accident.

## Consequences
- `catalog.yaml` gains a Jira project key field.
- The portal needs a read-only Jira API token (in `.env.local`, never committed) and a personal sandbox Jira site with synthetic demo data.
- Writing to Jira and an "open P1 bugs" scorecard check are out of scope for the MVP.
- Fallback: if Jira is at risk by 12-03, the per-team totals in the standards overview move to v1 (see PRD §7).
