# CLAUDE.md: Agent operating rules

These rules apply to every AI agent working in this repo. John Collins is the product owner and approves every merge. When this file and an issue disagree, stop and ask.

## How work arrives

- Every change starts from a **Jira story** (project `BSL`) that has acceptance criteria and that John has pulled into the active sprint. No story, no work. (ADR 0005)
- Move the story to **In Progress** when you start and to **In Review** when the PR is open. Only John moves stories to **Done**.
- Work on one story per branch: `feat/BSL-<n>-short-slug`, `fix/BSL-<n>-short-slug` or `docs/BSL-<n>-short-slug`.
- PR titles start with the key: `BSL-<n>: summary`.
- Each PR description **copies the story's acceptance criteria** and maps each one to the test or evidence that proves it. The Jira board is private, so the PR has to stand on its own for public readers.
- Stay inside the story's scope. If you find other work, propose a new Jira story rather than expanding the PR.

## Definition of done

A PR is ready for review only when all of these are true:

1. Every acceptance criterion in the story is met and shown in the PR description.
2. Automated tests cover the new behavior, and the full suite passes locally and in CI.
3. Lint, type-check and format pass with no new warnings.
4. Any user-visible change comes with a screenshot or short clip in the PR.
5. Docs are updated where behavior or setup changed (README, `docs/`).
6. If the change makes a meaningful choice (a library, a data model, a trade-off), it adds a decision record in `docs/decisions/`.
7. No secrets, tokens, real personal data, or employer or internal system names anywhere in the diff.

## Guardrails

- **Never** merge your own PR, push to `main`, force-push a shared branch or rewrite history.
- **Never** commit secrets. Config goes in `.env.local` (git-ignored), and every new variable gets a documented placeholder in `.env.example`.
- Use only sandbox or test credentials and synthetic seed data.
- Don't add a dependency without saying why in the PR description. Prefer well-maintained, widely used packages.
- Don't disable, skip or weaken tests to make CI pass. If a test is wrong, say so in the PR.
- When requirements are ambiguous, ask in the Jira story or PR before guessing.
- Jira access is limited to the `BSL` project on John's personal sandbox site. Never create, edit or close stories John hasn't asked for.

## Engineering standards

*Fill these in once the stack decision record lands.*

- Language and framework: TBD (planned: TypeScript, Next.js)
- Database: TBD (planned: Postgres)
- Testing: TBD (unit, integration, end-to-end)
- Commands: `install`, `dev`, `test`, `lint` — TBD

## Commit messages

Use the Conventional Commits style, `type(scope): summary`, with the Jira key (`BSL-<n>`) in the body. Jira's GitHub integration links on the key.
