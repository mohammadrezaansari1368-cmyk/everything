---
name: everything
description: "ONE command: `everything <task>`. N3S orchestrator (Need, Navigate, Narrow, Solve) for any coding/design/agent task. Keeps a compact skill index and loads a skill's full SKILL.md only when the current step needs it. Full spec: docs/N3S.md."
---

# everything — N3S orchestrator

Core: **Maximum Capability ≠ Maximum Context.** Load less, retrieve better, use the right skill, verify, keep only what matters. Never invoke a skill merely because it exists.

## N1 — Need (before loading anything)
Classify: outcome · current problem · domain/system · autonomy level · constraints · missing info · risk. Ask only if missing info blocks a correct action. Load no skill until classified.

## N2 — Navigate
Pick the fewest skills (usually 1) from the INDEX for the *current step*. Load its full SKILL.md only now. When the step/problem changes, drop that skill's detail and route again.

## N3 — Narrow
repo → module → files → symbols → lines. Search / index / graph (graphify if `graphify-out/` exists or structure is unknown) / summaries before opening large files. Reuse verified facts; don't rediscover.

## S — Solve loop
Understand → Select Skill → Retrieve Minimum Context → Act → Verify → Continue / Switch. Done only when the outcome is verified.

## Context budget (per item)
Required now? No → don't load. Yes → can search/summarize first? Yes → smallest section; No → load source.

## Working state (compress after each completed step)
```
Goal | Known Facts | Current Hypothesis | Files Involved | Changes Made | Verification Status | Next Action
```
Keep decisions and evidence, not intermediate thoughts.

## Protocol
01 understand outcome · 02 classify · 03 minimum skill · 04 search before reading · 05 load only relevant · 06 smallest useful action · 07 verify · 08 record reusable findings · 09 compress · 10 next skill only if required · 11 repeat until verified.

## Lightweight defaults (do NOT load these skills wholesale)
- Think before coding; simplest solution; surgical diffs; verifiable goal (karpathy).
- Terse output unless detail requested (caveman).
- No "done" without a passing check.

## Skill INDEX (name — load when…)
Paths: `skills/<source>/<name>/SKILL.md` (locally: `~/.claude/skills/<name>`). Prefer the first listed; others are fallbacks.

**Need/ideas:** brainstorming — vague goal or design choice · idea-refine, interview-me — requirements unclear
**Plan:** writing-plans — multi-step work · spec-driven-development — needs a spec · planning-and-task-breakdown — large scope · executing-plans — plan exists · constraint-driven-development — hard constraints
**Navigate code:** graphify — unknown structure/behavior, reverse engineering · investigate-first, caveman-explore — explore before change · source-driven-development — must cite source/docs · context-engineering — context getting large
**API reverse engineering:** reverse-api-engineer — turn a site's private HTTP API into a typed client (rae CLI); skip if an official API/SDK exists
**Build:** test-driven-development (alt addy-test-driven-development) — writing code with testable behavior · incremental-implementation, surgical-patch — small change · subagent-driven-development, dispatching-parallel-agents, cavecrew — independent parallel tasks · using-git-worktrees — isolate branch work
**UI:** ui-ux-pro-max — any UI/UX decision · frontend-design — visual polish · frontend-ui-engineering — component code · web-artifacts-builder — single-file web artifact
**Debug:** systematic-debugging — any failure/unexpected result · debugging-and-error-recovery — recovery steps
**Test:** webapp-testing — drive web app with Playwright · browser-testing-with-devtools — DevTools inspection
**Security/DB/perf:** security-and-hardening — auth, secrets, input handling · performance-optimization — slow paths, DB queries · observability-and-instrumentation — logs/metrics/tracing
**Node/TypeScript (ECC, `skills/ecc/<name>/SKILL.md`):** typescript-patterns — strict TypeScript · backend-patterns — Node, Express, or Next.js API structure. Curated copies under `ecc/` overlap these and other listed skills; do not load the `ecc/` copies as a second skill. Do not load ECC hooks, scanners, or installers.
**APIs/tools:** api-and-interface-design — API shape · mcp-builder — MCP server · claude-api — Claude API app · skill-creator, writing-skills — authoring skills
**Refactor/migrate:** code-simplification, safe-refactor — refactor · deprecation-and-migration, migration — migrations
**Review:** requesting-code-review — after a meaningful chunk · receiving-code-review — handling feedback · code-review-and-quality, caveman-review, doubt-driven-development — extra scrutiny
**Verify:** verification-before-completion, verify-and-stop — before claiming done
**Git/DevOps/ship:** git-workflow-and-versioning, caveman-commit — git ops · ci-cd-and-automation — CI/deploy failure · finishing-a-development-branch — wrap up branch · shipping-and-launch — release · documentation-and-adrs — docs/decisions
**Terse modes:** caveman (+ ultracave/megacave) — user wants minimal tokens · caveman-compress — compress a file
**Ruflo (multi-agent meta-harness, `skills/ruflo/<name>/SKILL.md`, 303 skills; full list in README Index):** sparc-methodology — structured Spec→Pseudocode→Architecture→Refine→Complete flow · swarm-orchestration, coordinate-ruflo-swarm, hive-mind(-advanced) — large tasks split across coordinated agents · security-audit — security review · verification-quality — quality gate before done · agent-release-manager, agent-release-swarm — release prep · github-multi-repo, agent-swarm-pr — multi-repo / PR work · agentdb-memory-patterns, agentdb-learning — persistent agent memory · hooks-automation — automation hooks · v3-performance-optimization — perf · agent-tester, agent-test-long-runner — test agents. Load one only when the step needs it.
**ECC (agent harness, `skills/ecc/<name>/SKILL.md`, 328 skills; full list in README Index).** During Navigate, if the current step matches a category below, load **one** matching ECC skill (full SKILL.md only now). Do not load ECC hooks, scanners, or the official installer. Name collisions with ruflo (`deep-research`, `git-workflow`, `security-scan`, `tdd-workflow`): prefer the first-listed/existing copy unless the step is specifically the ECC variant
- **Agent/harness:** agent-harness-construction, agent-architecture-audit — design or audit an agent stack · agent-eval, eval-harness, agent-self-evaluation — compare or score agent work · agent-introspection-debugging — agent run failed · agent-security-hardening — harden tools/untrusted input · agentic-engineering, agentic-os, autonomous-agent-harness, autonomous-loops, team-agent-orchestration, team-builder, council, council-multi-model — multi-agent systems · configure-ecc, ecc-guide, ecc-recipes, workspace-surface-audit, agent-sort, skill-comply, skill-scout, skill-stocktake, skill-host-compat — ECC setup, recipes, or skill inventory
- **Plan/orchestrate:** plan-canvas, plan-orchestrate — plan a change · orch-build-mvp, orch-add-feature, orch-change-feature, orch-fix-defect, orch-pipeline, orch-refine-code — feature/MVP/defect orchestration · intent-driven-development, blueprint, delivery-gate, product-capability, product-lens, project-flow-ops — product or delivery flow
- **Research/search:** exa-search, research-ops, iterative-retrieval, search-first — web/knowledge retrieval · market-research, competitive-platform-analysis, osint-investigation, scientific-thinking-literature-review — research reports (for `deep-research`, use the existing ruflo copy unless the step is specifically ECC)
- **TDD/test/verify:** django-tdd, laravel-tdd, quarkus-tdd, springboot-tdd, ai-regression-testing — test-first or AI-regression · e2e-testing, browser-qa, windows-desktop-e2e, python-testing, golang-testing, rust-testing, react-testing, verification-loop — run or design tests (for `tdd-workflow`, use the existing ruflo copy unless the step is specifically ECC)
- **Security/compliance:** security-review, web-perimeter-owasp-2025-audit, django-security, laravel-security, springboot-security, safety-guard, gateguard, hipaa-compliance, healthcare-phi-compliance, mcp-dependency-review, security-bounty-hunter — review, harden, or audit (for `security-scan`, use the existing ruflo copy unless the step is specifically ECC)
- **Architecture/docs:** architecture-decision-records, change-impact, context-and-decisions — ADRs and impact · hexagonal-architecture, android-clean-architecture, module-governance, contract-first, coding-standards, codebase-onboarding, code-tour, docs-governance, living-docs-governance, documentation-lookup — structure and docs
- **Frontend/UI:** accessibility, frontend-a11y — a11y · frontend-patterns, frontend-design-direction, frontend-slides, design-system, react-patterns, react-performance, vue-patterns, angular-developer, nuxt4-patterns, nextjs-turbopack, vite-patterns, ui-canvas, make-interfaces-feel-better, motion-patterns — UI implementation or design direction
- **Backend/languages:** typescript-patterns, backend-patterns — Node/TS · python-patterns, fastapi-patterns, django-patterns, golang-patterns, rust-patterns, nestjs-patterns, laravel-patterns, rails-patterns, springboot-patterns, kotlin-patterns, dart-flutter-patterns, swiftui-patterns, dotnet-patterns, bun-runtime — language/framework patterns
- **Data/infra:** postgres-patterns, mysql-patterns, redis-patterns, prisma-patterns, clickhouse-io, database-migrations, docker-patterns, kubernetes-patterns, terraform-patterns, deployment-patterns — data stores and deploy
- **Perf/cost:** benchmark, benchmark-optimization-loop, cost-aware-llm-pipeline, cost-tracking, token-budget-advisor, prompt-optimizer, context-budget, latency-critical-systems, parallel-execution-optimizer — measure, speed up, or cut cost
- **Git/ops:** github-ops, conventional-commit-review, issue-review, jira-integration, production-audit, canary-watch, terminal-ops, automation-audit-ops — repo and operations (for `git-workflow`, use the existing ruflo copy unless the step is specifically ECC)
- **Memory/learning:** continuous-learning-v2, continuous-learning, unified-memory, knowledge-ops — persist or improve agent memory
- **Content/media/ML:** article-writing, seo, content-engine, video-editing, remotion-video-creation, mle-workflow, pytorch-patterns, ito-training, ito-inference — content, video, or ML work
