# 0003: Services register through a catalog.yaml in their own repo

- **Status:** Accepted
- **Date:** 2026-11-17
- **Decider:** John Collins

## Context
The catalog is only valuable if its data is accurate. We need to decide how service metadata (owner, on-call, links) gets into the portal.

## Options considered
1. **Manual entry through a form:** simplest to build, but the data drifts out of date, which is the problem the portal exists to solve.
2. **A `catalog.yaml` in each repo (catalog as code):** metadata lives next to the code, changes go through PR review, and the portal syncs it through the GitHub API. This is the industry pattern (Backstage's `catalog-info.yaml`).
3. **Both:** more MVP scope, and two sources of truth to reconcile.

## Decision
We chose **catalog.yaml in each repo** over manual entry because it keeps ownership data versioned, reviewable and close to the code, and because a missing or incomplete file is itself a useful scorecard signal.

## Consequences
- The portal needs a GitHub integration that discovers repos and reads `catalog.yaml`, including handling malformed files.
- The YAML schema becomes a contract and must be documented.
- Services without the file don't appear in the catalog. Showing those repos as "unregistered" is a candidate v1 feature for coverage metrics.
