# everything

یک مخزن واحد که همه‌ی اسکیل‌ها را ادغام می‌کند و با **یک دستور** اجرا می‌شود: `everything <task>`.
A single repo merging all agent skills, driven by **one command**: `everything <task>`.

## How it works / نحوه کار — N3S
- فقط یک دستور: `everything <task>`. این دستور ارکستریتور **N3S** (Need، Navigate، Narrow، Solve) است: اول نیاز را دسته‌بندی می‌کند، فقط کمترین اسکیل لازم برای همان مرحله را بارگذاری می‌کند، کانتکست را باریک می‌کند و تا تأیید نتیجه ادامه می‌دهد. هیچ اسکیلی به‌صورت سراسری بارگذاری نمی‌شود.
- One command: `everything <task>`. It is an **N3S** orchestrator (Need, Navigate, Narrow, Solve): classify the need, load only the minimum skill for the current step (full SKILL.md just-in-time from a compact index), narrow context, solve and verify. No skill is loaded globally; karpathy/caveman are lightweight defaults only. Target ~70% less context (a target, not a guarantee).
- Full spec / مشخصات کامل: [docs/N3S.md](docs/N3S.md)
- Files: `skills/everything/SKILL.md`, `commands/everything.md`.
- Install: copy `skills/<source>/<skill>` into `~/.claude/skills/` (or `~/.codex/skills/`), and `commands/everything.md` into `~/.claude/commands/` (Codex: `~/.codex/prompts/`).
- Layout: `skills/<source>/<skill>/`; each source folder keeps upstream LICENSE/NOTICE.

## Overlaps (kept, not deleted) / هم‌پوشانی‌ها
| Topic | Primary (superpowers) | Also |
|---|---|---|
| TDD | test-driven-development | addyosmani/test-driven-development |
| Debugging | systematic-debugging | addyosmani/debugging-and-error-recovery, caveman/investigate-first |
| Planning | writing-plans, executing-plans | addyosmani/planning-and-task-breakdown, spec-driven-development |
| Ideation | brainstorming | addyosmani/idea-refine, interview-me |
| Code review | requesting/receiving-code-review | addyosmani/code-review-and-quality, caveman/caveman-review |
| Verification | verification-before-completion | caveman/verify-and-stop |
| Parallel agents | dispatching-parallel-agents, subagent-driven-development | caveman/cavecrew |
| Skill authoring | writing-skills | anthropics/skill-creator |
| Frontend | ui-ux-pro-max | anthropics/frontend-design, addyosmani/frontend-ui-engineering |
| Browser testing | anthropics/webapp-testing | addyosmani/browser-testing-with-devtools |
| Refactor | — | addyosmani/code-simplification, caveman/safe-refactor |
| Migration | — | addyosmani/deprecation-and-migration, caveman/migration |

## Index / فهرست (72 skills)
| Skill | Source | URL | License | Purpose |
|---|---|---|---|---|
| `api-and-interface-design` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Guides stable API and interface design. Use when designing APIs, module boundaries, or any public interface. Use when creating REST or Graph |
| `browser-testing-with-devtools` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Tests in real browsers via Chrome DevTools MCP. Use when building or debugging anything that runs in a browser. Use when you need to inspect |
| `ci-cd-and-automation` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Automates CI/CD pipeline setup. Use when setting up or modifying build and deployment pipelines. Use when you need to automate quality gates |
| `code-review-and-quality` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Conducts multi-axis code review. Use before merging any change. Use when reviewing code written by yourself, another agent, or a human. Use  |
| `code-simplification` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Simplifies code for clarity. Use when refactoring code for clarity without changing behavior. Use when code works but is harder to read, mai |
| `constraint-driven-development` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Establishes a project's quality bar as a written contract and stops agents quietly lowering it. Interviews the user on which dimensions matt |
| `context-engineering` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Optimizes agent context setup. Use when starting a new session, when agent output quality degrades, when switching between tasks, or when yo |
| `debugging-and-error-recovery` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Guides systematic root-cause debugging. Use when tests fail, builds break, something that worked yesterday broke, behavior doesn't match exp |
| `deprecation-and-migration` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Manages deprecation and migration. Use when removing old systems, APIs, or features. Use when migrating users from one implementation to ano |
| `documentation-and-adrs` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Records decisions and documentation. Use when you need to document an architecture decision (ADR) or the reasoning behind a design choice, w |
| `doubt-driven-development` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Subjects every non-trivial decision to a fresh-context adversarial review before it stands. Use when you want every assumption cross-examine |
| `frontend-ui-engineering` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Builds production-quality, accessible, responsive user-facing UIs. Use when building or modifying interfaces and pages, creating components, |
| `git-workflow-and-versioning` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Structures git workflow practices. Use when making any code change. Use when committing, branching, resolving conflicts, splitting uncommitt |
| `idea-refine` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Refines raw ideas into sharp, actionable concepts through structured divergent and convergent thinking. Use when an idea is still vague, whe |
| `incremental-implementation` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Delivers changes incrementally in thin, verifiable slices. Use when implementing any feature or change that touches more than one file, or w |
| `interview-me` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Extracts what the user actually wants instead of what they think they should want. Achieves this through one-question-at-a-time interview un |
| `observability-and-instrumentation` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Instruments code so production behavior is visible and diagnosable. Use when adding logging, metrics, tracing, or alerting. Use when shippin |
| `performance-optimization` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Optimizes application performance across frontend, backend, queries, and databases. Use when performance requirements exist, when you suspec |
| `planning-and-task-breakdown` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Breaks work into ordered tasks. Use when you have a spec or clear requirements and need to break work into implementable tasks. Use when a t |
| `security-and-hardening` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Hardens code against vulnerabilities. Use when auditing an input handler for vulnerabilities, when handling user input, authentication, data |
| `shipping-and-launch` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Prepares production launches. Use when preparing to deploy to production, or when asking what needs to be in place before shipping. Use when |
| `source-driven-development` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Grounds every implementation decision in official documentation. Use when you want to verify an approach against the official docs before im |
| `spec-driven-development` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Creates specs before coding. Use when starting a new project, feature, or significant change and no specification exists yet. Use when draft |
| `test-driven-development` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Drives development with tests using the red-green-refactor loop. Use when implementing any logic, fixing any bug, or changing any behavior.  |
| `using-agent-skills` | addyosmani | [https://github.com/addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) | MIT | Discovers and invokes agent skills. Use when starting a session, or when you need to decide which skill or workflow applies to the piece of  |
| `claude-api` | anthropics | [https://github.com/anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 (per-skill LICENSE.txt) | /- |
| `frontend-design` | anthropics | [https://github.com/anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 (per-skill LICENSE.txt) | Guidance for distinctive, intentional visual design when building new UI or reshaping an existing one. Helps with aesthetic direction, typog |
| `mcp-builder` | anthropics | [https://github.com/anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 (per-skill LICENSE.txt) | Guide for creating high-quality MCP (Model Context Protocol) servers that enable LLMs to interact with external services through well-design |
| `skill-creator` | anthropics | [https://github.com/anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 (per-skill LICENSE.txt) | Create new skills, modify and improve existing skills, and measure skill performance. Use when users want to create a skill from scratch, ed |
| `web-artifacts-builder` | anthropics | [https://github.com/anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 (per-skill LICENSE.txt) | Suite of tools for creating elaborate, multi-component claude.ai HTML artifacts using modern frontend web technologies (React, Tailwind CSS, |
| `webapp-testing` | anthropics | [https://github.com/anthropics/skills](https://github.com/anthropics/skills) | Apache-2.0 (per-skill LICENSE.txt) | Toolkit for interacting with and testing local web applications using Playwright. Supports verifying frontend functionality, debugging UI be |
| `cavecrew` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-commit` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-compress` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-discover` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-evidence-review` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-explore` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Read-only repository explorer for cold-start orientation, broad cross-file localization, or when a direct search failed. Skip it when the ex |
| `caveman-help` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-learn` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Act on a Caveman learn report - review the ranked token sinks, apply cost-lowering fixes with per-edit consent, and report what those fixes  |
| `caveman-manage` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-optimize` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-review` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-setup` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman-stats` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `caveman` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `investigate-first` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Diagnose ambiguous failures before editing. Use for unknown causes, intermittent behavior, performance regressions, or investigations needin |
| `lean-build` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Build feature work with high overbuilding risk. Use for new behavior, product slices, or integrations where repository reuse, strict scope,  |
| `megacave` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `migration` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Implement reversible compatibility-safe transitions. Use for schema, data, API, protocol, configuration, or dependency migrations requiring  |
| `safe-refactor` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Restructure code while preserving behavior. Use for extraction, consolidation, ownership moves, or cleanup where verification must bracket s |
| `surgical-patch` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Fix bugs and small behavior changes at the narrowest responsible layer. Use when regression proof, preserved surrounding behavior, and task- |
| `ultracave` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | > |
| `verify-and-stop` | caveman | [https://github.com/JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | Apache-2.0 | Prove existing work meets acceptance conditions without expanding scope. Use for validation-only tasks, completion checks, focused gate runs |
| `everything` | everything | this repo | — | ONE all-in-one command. Use `everything <task>` for any coding, design, or agent task: runs the whole workflow end to end (understand -> bra |
| `graphify` | graphify | [https://github.com/Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) | Apache-2.0 | Use for any question about a codebase, its architecture, file relationships, or project content — especially when graphify-out/ exists, wher |
| `karpathy-guidelines` | karpathy | [https://github.com/multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) | MIT (README) | Behavioral guidelines to reduce common LLM coding mistakes. Use when writing, reviewing, or refactoring code to avoid overcomplication, make |
| `brainstorming` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | You MUST use this before any creative work - creating features, building components, adding functionality, modifying behavior, or planning a |
| `diagnosing-superpowers` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when a superpowers session went wrong and your human partner wants to know why — repeated work, ignored plans, stumbles, poor results, a |
| `dispatching-parallel-agents` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when facing 2+ independent tasks that can be worked on without shared state or sequential dependencies |
| `executing-plans` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when executing an implementation plan in the current session as the implementer yourself — your human partner chose inline execution, or |
| `finishing-a-development-branch` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when implementation is complete, all tests pass, and you need to decide how to integrate the work |
| `receiving-code-review` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when receiving code review feedback, before implementing suggestions, especially if feedback seems unclear or technically questionable - |
| `requesting-code-review` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when completing tasks, implementing major features, or before merging to verify work meets requirements |
| `subagent-driven-development` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when executing implementation plans with independent tasks in the current session |
| `systematic-debugging` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when encountering any bug, test failure, or unexpected behavior, before proposing fixes |
| `test-driven-development` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when implementing any feature or bugfix, before writing implementation code |
| `using-git-worktrees` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when starting feature work that needs isolation from current workspace or before executing implementation plans - ensures an isolated wo |
| `using-superpowers` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when starting any conversation - establishes how to find and use skills, requiring skill invocation before ANY response including clarif |
| `verification-before-completion` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when about to claim work is complete, fixed, or passing, before committing or creating PRs - requires running verification commands and  |
| `writing-plans` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when you have a spec or requirements for a multi-step task, before touching code |
| `writing-skills` | superpowers | [https://github.com/obra/superpowers](https://github.com/obra/superpowers) | MIT | Use when creating new skills, editing existing skills, or verifying skills work before deployment |
| `ui-ux-pro-max` | ui-ux-pro-max | [https://github.com/nextlevelbuilder/ui-ux-pro-max-skill](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | MIT | UI/UX design intelligence for web, mobile, and desktop. This skill should be used when designing, building, reviewing, or fixing interfaces, |

## Not included / حذف‌شده
- anthropics: docx, pdf, pptx, xlsx (source-available, not redistributable) and non-coding skills.
- caveman: proxy, engine, CLI, plugins, packages — skills only.

All rights remain with original authors; see each folder's LICENSE.
