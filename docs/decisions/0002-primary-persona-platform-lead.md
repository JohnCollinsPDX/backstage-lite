# 0002: The platform lead is the primary MVP persona

- **Status:** Accepted
- **Date:** 2026-11-17
- **Decider:** John Collins

## Context
Three personas would use the portal: platform leads, on-call responders and service developers. A two-week MVP can only be built around one primary job to be done.

## Options considered
1. **On-call responder** ("find the owner in under a minute"): a sharp, easy-to-demo job, but it treats the portal as a lookup tool.
2. **Platform lead** ("where are we falling short of our standards, and who owns fixing it?"): drives adoption and governance, which are what a platform product is judged on.
3. **Service developer** (self-service scorecard fixes): useful, but it depends on a platform lead having set the standards first.

## Decision
We chose the **platform lead** because the portal's value as a platform product comes from standards adoption across the organization. The on-call and developer needs are still served by the service detail page and scorecard detail; they just don't drive MVP priorities.

## Consequences
- The MVP needs a cross-service **standards overview**, not just per-service pages.
- The demo needs enough synthetic services (with a realistic mix of passing and failing checks) for the overview to tell a story.
- The success metrics focus on coverage and compliance rates.
