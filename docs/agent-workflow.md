# Agent workflow

How this product gets built: a human product owner running a team of AI coding agents.

## Roles

| Role | Who | Responsibilities |
|---|---|---|
| Product owner and tech lead | John (human) | Writes the PRD, prioritizes the backlog, writes acceptance criteria, reviews every PR, approves every merge, records decisions |
| Planner agent | Claude Code | Breaks PRD sections into user stories and drafts acceptance criteria for John to approve |
| Implementer agents | Claude Code, one per issue, each in its own git worktree | Builds one issue on a feature branch and opens a PR that meets the definition of done in `CLAUDE.md` |
| Reviewer agent | Claude Code | Reviews each PR against its acceptance criteria and `CLAUDE.md` before John sees it |

## Flow

```
PRD ─► Planner drafts stories ─► John approves → GitHub Issues
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

1. **Story gate:** an issue can't be dispatched until it has testable acceptance criteria (Given / When / Then) and John has approved it.
2. **CI gate:** tests, lint and type-check must pass.
3. **Review gate:** the reviewer agent's findings are addressed, then John approves.
4. **Rework tracking:** a PR that needs changes after John's review counts toward the rework rate.

## Metrics captured

Stories shipped · cycle time (issue dispatched → merged) · token cost per feature · rework rate (share of PRs merged without changes requested). These feed the agent delivery dashboard project.

*This document will change as the process does. Changes are recorded in `docs/decisions/`.*
