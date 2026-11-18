# PRD: Backstage-lite (internal developer portal)

| | |
|---|---|
| **Owner** | John Collins (Product Owner) |
| **Status** | Draft: discovery (3 of 7 questions resolved; Jira added to MVP) |
| **Backlog** | Jira (system of record, see [ADR 0005](decisions/0005-jira-as-backlog-system-of-record.md)) |
| **Last updated** | 2026-11-17 |

> Sections marked **TBD** get filled in during discovery. Each open question gets resolved here or in a decision record.

## 1. Problem

Engineering teams lose time on basic questions: *Who owns this service? Who's on call? Where's the runbook? Is it deployed? Does it meet our standards?* The answers are spread across wikis, spreadsheets, chat history and people's heads. Full portals like Backstage solve this, but they take a dedicated platform team to stand up and maintain.

**TBD:** sharpen the problem with a specific scenario, such as an incident where nobody could find the owner.

## 2. Users

| Persona | Need | Priority |
|---|---|---|
| **Engineering / platform lead** | See standards adoption across all services, spot ownership and quality risk, track improvement over time | **Primary (MVP)** |
| On-call / incident responder | Find a service's owner, on-call contact and runbook in under a minute | Secondary: served by the service detail page |
| Service developer | See how their service scores and what to fix | Secondary: served by the scorecard detail |

The MVP is built around the platform lead's question: *"Across all our services, where are we falling short of our standards, and who owns fixing it?"* (see [ADR 0002](decisions/0002-primary-persona-platform-lead.md))

## 3. Goals and success metrics

**TBD.** Candidate metrics:
- Catalog coverage: % of services registered with an owner
- Scorecard compliance: % of services passing each standard ("has tests", "has runbook")
- Time to find an owner or runbook (task-based test)
- Weekly active users of the portal

## 4. Scope

### MVP (in scope)
- **Catalog as code:** each service declares itself in a `catalog.yaml` at its repo root (name, description, owning team, on-call contact, links). The portal discovers and syncs these through the GitHub API. (see [ADR 0003](decisions/0003-catalog-as-code-yaml.md))
- **Service catalog list** with search and filter by team and score
- **Service detail page:** metadata, links and scorecard results
- **Scorecards**, run automatically against each repo:
  1. Has a README and a runbook (`README.md`, `docs/runbook.md`)
  2. Has tests, and the latest CI run on `main` passed
  3. Declares an owner and an on-call contact in `catalog.yaml`
- **Standards overview** for the platform lead: pass rate per check across all services, and the services failing each check with their owners
- **Jira integration (read-only):** a service's `catalog.yaml` names its Jira project key. The service detail page shows open bug and incident counts with links into Jira, and the standards overview shows open-bug totals per team. (see [ADR 0004](decisions/0004-jira-integration-in-mvp.md))
- Deploy status: TBD (see open questions)

### Out of scope (draft)
- Authentication / SSO beyond a basic login (TBD)
- Plugin system
- Real paging or on-call scheduling integrations; on-call is stored as data
- Writing to Jira (creating or updating tickets from the portal)
- An "open P1 bugs" scorecard check (v1 candidate)
- Any employer or real production data. The demo uses synthetic services only.

## 5. Open questions

1. ~~Who is the primary persona for the MVP?~~ **Resolved:** the platform lead (ADR 0002).
2. ~~How do services get into the catalog?~~ **Resolved:** a `catalog.yaml` in each repo (ADR 0003).
3. ~~Which scorecard checks ship in the MVP?~~ **Resolved:** README/runbook, tests + CI, owner + on-call. Branch protection deferred to v1.
4. Where does "deploy status" come from: GitHub Releases, Deployments, or Actions runs? Is it in the MVP at all?
5. Where do the synthetic demo services live (a dedicated GitHub org, or repos under John's account), and how many?
6. What targets go with the success metrics?
7. Which Jira projects and synthetic bugs/incidents seed the demo, and which Jira issue types count as "incident"?

## 6. Milestones

| Milestone | Target | Contents |
|---|---|---|
| MVP | **2026-12-08** (was 12-01, moved for Jira scope, ADR 0004) | catalog.yaml sync, catalog list + detail, 3 scorecard checks, standards overview, read-only Jira bug/incident counts, deployed demo |
| v1 | ~2026-12-22 | TBD: candidates are deploy status, branch-protection check, open-P1 scorecard check, score trend over time, on-call quick-find |

## 7. Risks

| Risk | Mitigation |
|---|---|
| Jira API rate limits or auth issues slow the build | Read-only API token stored in `.env.local`; cache results; demo runs against a personal sandbox site with synthetic data only |
| The bigger MVP slips past 12-08 | Jira is built after the catalog and scorecards. If it's at risk by 12-03, the standards-overview Jira totals move to v1 |
