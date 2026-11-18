# 0005: Jira is the backlog system of record; PRs carry the acceptance criteria

- **Status:** Accepted
- **Date:** 2026-11-17
- **Decider:** John Collins
- **Supersedes:** using GitHub Issues as the backlog (the original plan)

## Context
Most product and platform organizations run their backlogs in Jira. Showing a real Jira backlog (epics, stories, acceptance criteria, sprints) is stronger portfolio evidence than GitHub Issues. But a free Jira site can't be made publicly visible, while the GitHub repo is public.

## Options considered
1. **GitHub Issues only:** public, but it doesn't show Jira skills.
2. **Mirror Jira and GitHub Issues:** visible everywhere, but two sources of truth that drift.
3. **Jira as the system of record, with each PR carrying its story's acceptance criteria:** one source of truth, and the public trail still stands on its own.

## Decision
We chose **option 3**. Stories, epics and acceptance criteria live in the team-managed Scrum project **Backstage-lite (`BSL`)** on John's personal Jira Cloud site. Each branch and PR is named with its Jira key, and each PR description copies the story's acceptance criteria and maps each one to evidence. Jira's GitHub integration links PRs back to tickets.

## Consequences
- `CLAUDE.md` and `docs/agent-workflow.md` reference Jira keys instead of GitHub issue numbers.
- The GitHub issue template is replaced by a PR template with an acceptance-criteria section.
- Issue #1 (already open) stays as the last GitHub-tracked story.
- For interviews, the case study includes screenshots of the Jira board, and a reviewer can be invited to the Jira site if needed.
