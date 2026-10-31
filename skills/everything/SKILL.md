---
name: everything
description: "ONE all-in-one command. Use `everything <task>` for any coding, design, or agent task: runs the whole workflow end to end (understand -> brainstorm -> plan -> build with TDD -> UI -> debug -> review -> verify -> ship) and automatically invokes each bundled skill whenever its trigger fires during the task. The user never needs to call another skill."
---

# everything — continuous all-in-one orchestrator

The user types only `everything <task>`. You own the whole task end to end. This is not a one-time picker: keep re-checking the triggers below at every step and load the matching skill the moment its trigger fires (load by name; if missing, use the listed fallback and say so).

## Always-on rules (whole session)
- **karpathy-guidelines**: think before coding, simplest solution, surgical changes, verifiable goals.
- **graphify**: whenever you need to understand code structure or `graphify-out/` exists, query the graph before reading files broadly.
- **caveman**: terse output by default; drop it if user asks for detail. Use `caveman-commit` for commit messages.
- **verification-before-completion**: never claim done without running the check.
- **context-engineering**: keep context lean; summarize large reads.

## Stage pipeline
Run stages in order; skip a stage only when it clearly doesn't apply, and state the skip in one line. Jump back to an earlier stage when its trigger fires again.

| # | Stage | Trigger | Skills (primary -> fallback) |
|---|---|---|---|
| 1 | Understand | always first | graphify, investigate-first, caveman-explore, source-driven-development |
| 2 | Brainstorm | goal vague, new feature, design choice | brainstorming -> idea-refine, interview-me |
| 3 | Plan | >1 step or >1 file | writing-plans -> spec-driven-development, planning-and-task-breakdown, constraint-driven-development |
| 4 | Isolate | code changes in a repo | using-git-worktrees, git-workflow-and-versioning |
| 5 | Build | implementing | test-driven-development (addy-test-driven-development), incremental-implementation, surgical-patch; parallelizable tasks -> subagent-driven-development / dispatching-parallel-agents / cavecrew; existing plan -> executing-plans |
| 6 | UI | any UI/frontend/design work | ui-ux-pro-max -> frontend-design -> frontend-ui-engineering; artifacts -> web-artifacts-builder |
| 7 | Specialized | as matched | MCP server -> mcp-builder; Claude API -> claude-api; API design -> api-and-interface-design; new skill -> skill-creator / writing-skills; refactor -> code-simplification, safe-refactor; migration -> deprecation-and-migration, migration; perf -> performance-optimization; security -> security-and-hardening; logging/metrics -> observability-and-instrumentation |
| 8 | Debug | any failure, error, unexpected result | systematic-debugging -> debugging-and-error-recovery; then back to stage 5 |
| 9 | Test in browser | web app behavior | webapp-testing, browser-testing-with-devtools |
| 10 | Review | after each meaningful chunk | requesting-code-review, code-review-and-quality, caveman-review, doubt-driven-development; on feedback -> receiving-code-review |
| 11 | Verify | before any "done" | verification-before-completion, verify-and-stop |
| 12 | Ship | work complete | finishing-a-development-branch, documentation-and-adrs, ci-cd-and-automation, shipping-and-launch |

## Loop
1. Announce the planned stages in one line.
2. Execute; at each step re-evaluate triggers (errors -> stage 8, UI appears -> stage 6, scope grows -> stage 3).
3. Finish with a short report: what changed, checks run, skills used.

Overlaps: superpowers versions are primary; addyosmani/caveman equivalents are fallbacks (see repo README).

"n3s method": pending definition from the owner; pipeline is generic until defined.
