# PRD: Backstage-lite (internal developer portal)

| | |
|---|---|
| **Owner** | John Collins (Product Owner) |
| **Status** | Draft: discovery |
| **Last updated** | 2026-11-17 |

> Sections marked **TBD** get filled in during discovery. Each open question gets resolved here or in a decision record.

## 1. Problem

Engineering teams lose time on basic questions: *Who owns this service? Who's on call? Where's the runbook? Is it deployed? Does it meet our standards?* The answers are spread across wikis, spreadsheets, chat history and people's heads. Full portals like Backstage solve this, but they take a dedicated platform team to stand up and maintain.

**TBD:** sharpen the problem with a specific scenario, such as an incident where nobody could find the owner.

## 2. Users

| Persona | Need | Primary? |
|---|---|---|
| Service developer | Register a service, see how it scores against standards, find what to fix | TBD |
| On-call / incident responder | Find a service's owner, on-call contact and runbook in under a minute | TBD |
| Engineering / platform lead | See standards adoption across all services, spot risk | TBD |

## 3. Goals and success metrics

**TBD.** Candidate metrics:
- Catalog coverage: % of services registered with an owner
- Scorecard compliance: % of services passing each standard ("has tests", "has runbook")
- Time to find an owner or runbook (task-based test)
- Weekly active users of the portal

## 4. Scope

### MVP (in scope, draft)
- Service catalog: name, description, owning team, on-call contact, links to repo, docs and runbook
- Service detail page
- Scorecards: automated checks on each service's repo through the GitHub API
- Deploy status: latest deploy or release per service
- Search and filter

### Out of scope (draft)
- Authentication / SSO beyond a basic login (TBD)
- Plugin system
- Real paging or on-call scheduling integrations; on-call is stored as data
- Any employer or real production data. The demo uses synthetic services only.

## 5. Open questions

1. Who is the primary persona for the MVP?
2. How do services get into the catalog: manual entry, a `catalog.yaml` in each repo, or both?
3. Which scorecard checks ship in the MVP?
4. Where does "deploy status" come from: GitHub Releases, Deployments, or Actions runs?
5. What are the MVP → v1 milestones and dates?

## 6. Milestones

| Milestone | Target | Contents |
|---|---|---|
| MVP | TBD | TBD |
| v1 | TBD | TBD |
