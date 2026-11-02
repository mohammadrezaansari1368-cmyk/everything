# ECC curated subset

Markdown-only excerpt of [affaan-m/ECC](https://github.com/affaan-m/ECC) (everything-claude-code).

| | |
|---|---|
| Source | https://github.com/affaan-m/ECC |
| Upstream commit | `b38be6a7f6350964d59328b52f0624e1d1d552d1` |
| Commit date | 2026-10-30 |
| License | MIT. Copyright (c) 2026 Affaan Mustafa. Full notice: [LICENSE.md](LICENSE.md) |
| What this is | Rules, skills, and agent definitions for TDD, code review, security review, and Node.js/TypeScript, plus an `AGENTS.md` template and npm supply-chain guidance |

Each copied file was read before it was added. Shell, network, installer, hook, telemetry, and prompt-override instructions were removed. These files do not override this repository's agent instructions. `templates/AGENTS.md` is a template, not a live `AGENTS.md` at the repo root.

## How this fits the repo

This repository already routes TDD, code review, and security through superpowers, addyosmani, and caveman skills. Those stay the primary skills. The ECC copies are kept under `ecc/` so the MIT text and attribution stay intact. They are not a second entry in the N3S router for the same job.

Node.js and TypeScript patterns were not already in the index, so `skills/everything` may load `ecc/skills/typescript-patterns` or `ecc/skills/backend-patterns` when that is the step. npm supply-chain guidance had no existing doc here.

## Files taken

| File | Why |
|---|---|
| `rules/common/testing.md` | TDD rule: red-green-refactor and an 80% coverage bar |
| `rules/common/code-review.md` | Code review rule: when to review, severity, checklist |
| `rules/common/security.md` | Security review rule: secrets, injection, XSS, CSRF |
| `rules/typescript/coding-style.md` | TypeScript/JavaScript style |
| `rules/typescript/patterns.md` | TypeScript/JavaScript API, hook, and repository shapes |
| `rules/typescript/security.md` | TypeScript/JavaScript secret handling |
| `rules/typescript/testing.md` | TypeScript/JavaScript testing note (Playwright for E2E) |
| `skills/tdd-workflow/SKILL.md` | TDD skill, including untrusted-plan handling and an evidence report |
| `skills/security-review/SKILL.md` | Security review skill: checklist and safe-code patterns |
| `skills/typescript-patterns/SKILL.md` | TypeScript skill: strict types, narrowing, errors |
| `skills/backend-patterns/SKILL.md` | Node.js skill: Express and Next.js API, data, and auth patterns |
| `agents/planner.md` | Planner agent definition |
| `agents/code-reviewer.md` | Reviewer agent definition |
| `agents/security-reviewer.md` | Security reviewer definition |
| `agents/typescript-reviewer.md` | Node.js/TypeScript reviewer definition |
| `agents/tdd-guide.md` | TDD agent the testing rule points at |
| `templates/AGENTS.md` | Short template adapted from upstream `AGENTS.md` |
| `docs/npm-supply-chain-scanning.md` | npm scan policy, written as docs from the upstream workflow comments |
| `docs/supply-chain-incident-response.md` | npm incident playbook, with scanner and install commands removed |
| `LICENSE.md` | MIT notice required for the copy |

## Stripped while copying

- Bash, shell, and CI workflow fences that told an agent to run a package manager, a detector script, `gh`, or a coverage uploader
- `tools: Bash` (and write/edit grants) on agent definitions, so the definitions are read-only
- "Use proactively / must be used / automatically activated" wording that would override this repo
- Hook install steps, `.claude` settings, and the ECC package-manager detector script
- The instruction to upload lockfiles to a third-party scanner

## Skipped

| Upstream path | Why |
|---|---|
| `scripts/`, `hooks/`, `package.json`, MCP configs, memory, dashboard, video (`skills/remotion-video-creation`) | Out of scope. Not read into this tree and not executed |
| `.github/workflows/npmscan.yml`, `.github/workflows/supply-chain-watch.yml`, `scripts/ci/scan-supply-chain-iocs.js`, `scripts/ci/supply-chain-advisory-sources.js` | Scripts and workflows. The npm scan policy was rewritten as `docs/npm-supply-chain-scanning.md` |
| `rules/typescript/hooks.md`, `rules/common/hooks.md`, `.claude/rules/node.md` | Hook configuration and hook-authoring notes |
| `rules/README.md` | Installer (`install.sh`) instructions |
| `skills/security-scan/SKILL.md`, `commands/security-scan.md` | Instructions to install and run AgentShield with `npx` |
| `commands/code-review.md`, `commands/plan.md` | Slash-command shims that run `gh` and package scripts. The rule and the agent definitions cover the same jobs |
| Root `AGENTS.md` agent catalog (71 agents) | Reduced to `templates/AGENTS.md`. The other roles were not requested |
| `SECURITY.md` command sections (`grep`, `netstat`, `lsof`, `npx ecc-agentshield`) | Operational commands. The supply-chain policy bullets are in the npm doc |
| `skills/nodejs-keccak256` | Narrow crypto helper, not Node.js guidance |
| Other languages, translated docs, and the rest of `agents/` and `skills/` | Outside the requested subset |
| `rules/common/coding-style.md`, `patterns.md`, `git-workflow.md`, `performance.md`, `agents.md`, `development-workflow.md` | Not part of the requested TDD, review, security, or TypeScript set |

## Overlap with skills already here

| Topic | Already routed | ECC copy |
|---|---|---|
| TDD | `skills/superpowers/test-driven-development`, `skills/addyosmani/test-driven-development` | `ecc/skills/tdd-workflow` (evidence report and 80% bar). Not merged, so the MIT text stays attributed |
| Code review | `skills/superpowers/requesting-code-review`, `skills/addyosmani/code-review-and-quality` | `ecc/rules/common/code-review.md` and `ecc/agents/code-reviewer.md` |
| Security review | `skills/addyosmani/security-and-hardening` | `ecc/skills/security-review` and `ecc/agents/security-reviewer.md` |
| Planning | `skills/superpowers/writing-plans` | `ecc/agents/planner.md` only. No second planning skill |
