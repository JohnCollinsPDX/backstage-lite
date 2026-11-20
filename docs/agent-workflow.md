# Agent workflow

How this product gets built: a human product owner running a team of AI coding agents.

## Roles

| Role | Who | Responsibilities |
|---|---|---|
| Product owner and tech lead | John (human) | Writes the PRD, prioritizes the Jira backlog, writes and approves acceptance criteria, reviews every PR, approves every merge, records decisions |
| Planner agent | Claude Code (with Jira access) | Breaks PRD sections into Jira epics and stories and drafts acceptance criteria for John to approve |
| Implementer agents | Claude Code, one per story, each in its own git worktree | Builds one Jira story on a `BSL-<n>` branch and opens a PR that meets the definition of done in `CLAUDE.md` |
| Reviewer agent | Claude Code | Reviews each PR against its acceptance criteria and `CLAUDE.md` before John sees it |

## Flow

```
PRD ─► Planner drafts stories ─► John approves → Jira (BSL)
          │
          ▼
  Implementer agents (parallel worktrees) ─► PR
          │
          ▼
  CI (tests, lint, types) ─► Reviewer agent ─► John reviews
          │                                     │
          │◄──── changes requested ─────────────┘
          ▼
       John merges ─► deploy preview / production
```

## Quality gates

1. **Story gate:** a Jira story can't be dispatched until it has testable acceptance criteria (Given / When / Then) and John has pulled it into the **active sprint**. Sprint planning is the approval.

Jira board flow: **To Do → In Progress** (agent picks it up) **→ In Review** (PR open) **→ Done** (John merges).
2. **CI gate:** tests, lint and type-check must pass.
3. **Review gate:** the reviewer agent's findings are addressed, then John approves.
4. **Rework tracking:** a PR that needs changes after John's review counts toward the rework rate.

## Metrics captured

Stories shipped · cycle time (story moved to In Progress → PR merged) · token cost per feature · rework rate (share of PRs merged without changes requested). These feed the agent delivery dashboard project.

*This document will change as the process does. Changes are recorded in `docs/decisions/`.*
