# N3S — Need, Navigate, Narrow, Solve

> Owner's specification (verbatim).

N3S is a context-efficient execution methodology for AI agents designed to solve complex tasks by loading only the knowledge, skills, tools, and context required at the moment they are needed.

Its core principle is simple:

**Do not load everything. Understand the need, navigate to the right capability, narrow the context, and solve with the minimum sufficient information.**

N3S is not a single coding skill. It is an orchestration layer for skills.

Instead of giving an AI agent a massive prompt containing every rule, workflow, framework, and domain instruction, N3S keeps the initial context small and dynamically activates the appropriate skill when the task requires it.

## The N3S Model

### N1 — Need

Determine what the user is actually trying to accomplish before loading additional context.

Identify:

* the desired outcome;
* the current problem;
* the affected system or domain;
* the required level of autonomy;
* known constraints;
* missing information;
* potential risk.

Do not load specialized skills until the need has been classified.

Rule:

**Understand the task before expanding the context.**

---

### N2 — Navigate

Select the smallest set of relevant skills, tools, files, documentation, or agents required for the current task.

Examples:

```
UI problem
→ UI/UX skill
Unknown application behavior
→ Reverse-engineering skill
Database performance problem
→ Database skill
Authentication failure
→ Auth/Security skill
Deployment failure
→ DevOps skill
GitHub repository operation
→ Git/GitHub skill
```

Skills should be loaded on demand, not globally.

If the task changes, N3S may unload the previous mental context and navigate to another capability.

Rule:

**Right skill. Right moment. Right context.**

---

### N3 — Narrow

Reduce the working context to the minimum information necessary to make the next correct decision.

Do not repeatedly read an entire repository, documentation set, conversation history, or skill library.

Prefer:

```
Repository
    ↓
Relevant module
    ↓
Relevant files
    ↓
Relevant symbols
    ↓
Relevant lines
```

Use search, indexes, dependency graphs, summaries, references, and targeted retrieval before opening large files.

Reuse verified information instead of rediscovering it.

Rule:

**Retrieve precisely; do not consume context indiscriminately.**

---

### S — Solve

Execute the task using the selected skills and narrowed context.

The execution loop is:

```
Understand
   ↓
Select Skill
   ↓
Retrieve Minimum Context
   ↓
Act
   ↓
Verify
   ↓
Continue / Switch Skill
```

A task is complete only when the requested outcome has been verified.

---

## Skill-Oriented Execution

N3S treats skills as modular capabilities.

```
                    N3S
                     │
          ┌──────────┼──────────┐
          ↓          ↓          ↓
       Need       Navigate     Narrow
          └──────────┬──────────┘
                     ↓
                   Solve
                     │
       ┌─────────────┼─────────────┐
       ↓             ↓             ↓
   Coding        Testing        DevOps
   Security      Database       UI/UX
   Git           Research       Debugging
   Reverse       Documentation  Other Skills
```

The orchestrator should never activate every available skill by default.

For each step, ask:

**What is the minimum capability required to make the next correct action?**

Load that capability, perform the action, retain the useful result, and continue.

---

## Context and Token Efficiency

Traditional AI workflows often repeatedly load:

```
Large system prompt
+ full repository context
+ complete documentation
+ multiple skills
+ conversation history
+ previous outputs
```

This creates unnecessary context expansion.

N3S replaces this with:

```
Small Core Context
        +
Task Classification
        +
Relevant Skill
        +
Targeted Retrieval
        +
Compact Working State
```

The target is to reduce unnecessary context and token consumption by approximately 70% where task structure allows, without sacrificing correctness.

The 70% figure is an optimization target, not a guaranteed constant. Actual savings depend on repository size, task complexity, retrieval quality, and the agent/runtime being used.

---

## Token Reduction Strategy

N3S reduces token usage through five mechanisms:

1. **Lazy Skill Loading** — Load specialized instructions only when required.
2. **Targeted Context Retrieval** — Search first; read only relevant files, symbols, sections, or records.
3. **Progressive Disclosure** — Start with summaries and indexes. Expand into raw content only when necessary.
4. **Context Reuse** — Preserve verified architectural facts, decisions, paths, failures, and discoveries so they are not repeatedly rediscovered.
5. **Context Compression** — Replace completed investigation history with a compact working state:

```
Goal
Known Facts
Current Hypothesis
Files Involved
Changes Made
Verification Status
Next Action
```

The agent should preserve decisions and evidence, not every intermediate thought or previous output.

---

## The N3S Context Budget

Before loading additional information, evaluate:

```
Is it required now?
      │
      ├── No  → Do not load it.
      │
      └── Yes
           ↓
Can it be searched or summarized first?
      │
      ├── Yes → Retrieve the smallest relevant section.
      │
      └── No  → Load the required source.
```

Every additional context item must justify its token cost.

---

## Skill Selection Rule

Use the fewest skills capable of completing the current step.

```
1 skill sufficient
→ use 1
2 skills required
→ use 2
Skill no longer relevant
→ stop carrying its detailed context
New problem discovered
→ route to the appropriate skill
```

Never invoke a skill merely because it exists.

---

## N3S Execution Protocol

For every task:

01. Understand the requested outcome.
02. Classify the task.
03. Identify the minimum required skill.
04. Search before reading large sources.
05. Load only relevant context.
06. Execute the smallest useful action.
07. Verify the result.
08. Record reusable findings.
09. Compress completed context.
10. Select the next skill only if required.
11. Repeat until the outcome is verified.

---

## Core Principle

```
Maximum Capability
≠
Maximum Context
```

N3S aims for:

```
Maximum Capability
+
Minimum Necessary Context
+
Correct Skill Selection
+
Verified Execution
```

The objective is not simply to make an AI agent consume fewer tokens.

The objective is to make the agent more selective about what it thinks with.

N3S turns a large skill library into a just-in-time capability system: load less, retrieve better, use the right skill, verify the result, and preserve only what matters.
