# 0001: Use AI coding agents as the delivery team

- **Status:** Accepted
- **Date:** 2026-11-17
- **Decider:** John Collins

## Context
This project is meant to show product ownership: setting direction, writing requirements, keeping quality high and making trade-offs. I have one person's time and a 3–4 week target per release.

## Options considered
1. **Write all the code myself:** slower, and it puts the focus on coding instead of product ownership.
2. **AI agents write the code, and I own product and quality:** this matches where software delivery is heading, and it leaves a record of every requirement, review and decision.

## Decision
AI coding agents (Claude Code) implement the work. I own the PRD, the backlog, acceptance criteria, PR review and merge approval. The rules are in `CLAUDE.md` and the process is in `docs/agent-workflow.md`.

## Consequences
- Every change has a reviewable trail: issue → PR → review comments → merge.
- Quality depends on clear acceptance criteria and strong gates, which is where my QA and automation background counts.
- Agent cost and rework need tracking. That's the job of the agent delivery dashboard project.
