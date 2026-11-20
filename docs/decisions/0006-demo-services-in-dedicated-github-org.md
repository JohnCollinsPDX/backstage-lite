# 0006: Demo services live in a dedicated GitHub organization

- **Status:** Accepted
- **Date:** 2026-11-19
- **Decider:** John Collins

## Context
The portal needs services to catalog and score. The platform-lead persona (ADR 0002) needs enough services, with a realistic spread of passing and failing checks, for the standards overview to mean something. The demo must use synthetic data only.

## Options considered
1. **About 5 repos under John's personal account:** less setup, but fake service repos clutter the profile recruiters see next to the portfolio projects, and a personal account doesn't look like a company.
2. **A dedicated free GitHub organization with 8 repos across 3 fictional teams:** looks and behaves like a real engineering org (teams, ownership), keeps the personal profile clean, and the portal reads it through the same GitHub API it would use for any company.

## Decision
We chose **a dedicated GitHub org with 8 synthetic repos** over personal-account repos, because it keeps the portfolio profile clean and makes the demo realistic.

## Consequences
- John creates the org (free plan). The org name is TBD.
- Seeding the 8 repos becomes its own story, and that work can be scripted.
- The portal's GitHub integration targets an org, which matches real-world use.
- 8 repos is enough for meaningful pass rates, and small enough to keep up.
