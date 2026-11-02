# AGENTS.md template

> Template adapted from `https://github.com/affaan-m/ECC` `AGENTS.md` at `b38be6a7f6350964d59328b52f0624e1d1d552d1`. MIT License, Copyright (c) 2026 Affaan Mustafa.
>
> This is a template for a project that chooses to adopt it. It is not the operating instruction file for the repository that vendors this subset. Do not copy it to the repository root unless the maintainers want these rules. It does not authorize shell commands, network calls, hooks, installers, telemetry, or memory capture.

## Core principles

1. **Agent-first** — Delegate to a specialized role only when a person asks for that role.
2. **Test-driven** — Write tests before implementation. Hold an 80%+ coverage bar.
3. **Security-first** — Validate inputs. Do not weaken auth to make a task easier.
4. **Immutability** — Create new objects instead of mutating shared ones.
5. **Plan before execute** — Plan a complex feature before writing code.

## Roles in this subset

| Role | Use when |
|------|----------|
| planner | A person asks for an implementation plan |
| tdd-guide | A person asks for a test-first pass |
| code-reviewer | A person asks for a quality and security review |
| security-reviewer | A person asks for a vulnerability review |
| typescript-reviewer | A person asks for a TypeScript or JavaScript review |

Upstream lists many more agents. They were not copied. Do not invent calls to agents that are not in this subset.

## Security

Before a commit is proposed:

- No hardcoded secrets (API keys, passwords, tokens)
- User input validated at the boundary
- Queries parameterized
- HTML from users sanitized
- CSRF protection considered for state-changing browser actions
- Authentication and authorization checked
- Rate limiting considered on public endpoints
- Error messages do not leak secrets

Never hardcode secrets. Use the project's existing secret mechanism. If a secret was exposed, stop and tell a person so they can rotate it.

## Coding style

- Prefer many small files over a few large ones. 200–400 lines is typical. 800 is a soft ceiling.
- Handle errors explicitly. Do not swallow them.
- Functions stay under about 50 lines. Nesting stays under about 4 levels.
- Names should say what the value is.

## Testing

Hold 80% coverage across unit, integration, and end-to-end tests for critical flows.

1. Write the test first and confirm it fails for the intended reason.
2. Write the smallest implementation that makes that test pass.
3. Refactor only while the tests stay passing.

Fix the implementation when a test is right. Change a test only when the test itself is wrong.

## Workflow

1. Plan dependencies, risks, and phases.
2. Apply the test-first loop.
3. Review critical and high findings before calling the work done.
4. Put project knowledge in the project's existing docs. Do not create a parallel memory store.
5. Use conventional commit messages: `feat`, `fix`, `refactor`, `docs`, `test`, `chore`, `perf`, `ci`.

## Patterns

- API responses share one envelope: success flag, data, error, pagination metadata.
- Hide storage behind a repository interface (`findAll`, `findById`, `create`, `update`, `delete`).

## Success

- Tests pass and coverage meets the bar
- No known critical vulnerability in the diff
- The change stays readable
- The request is actually met
