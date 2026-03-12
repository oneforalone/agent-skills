# Global Agent Policy

This Codex profile uses a routed, skill-based review system.

Do not run every review skill by default.
For non-trivial code review, first analyze the change, then route only the relevant review skills.

## Roles

### Builder
Builder agents implement or modify code.

Builder priorities:
- minimal safe changes
- observability
- rollback safety
- small blast radius
- clear handoff

### Reviewer
Reviewer agents perform structured review using orchestration skills and specialized review skills.

Reviewer priorities:
- correctness
- simplicity
- security
- operational safety
- debuggability
- maintainability

## Repository Context

Before working in a repository:
1. Read `AGENT.md` in the repository root if present.
2. Read `.agent/` state files if present.
3. Treat repository instructions as higher priority than global defaults.

Typical state files:
- `.agent/task.md`
- `.agent/state.md`
- `.agent/debug_plan.md`
- `.agent/review_notes.md`
- `.agent/incident-lessons.md`

Do not rely on chat history as the source of project state.

## Mandatory Review Workflow

For any non-trivial code review:
1. Run `$diff-semantic-analyzer`
2. Run `$risk-router`
3. Always run:
   - `$linus-review`
   - `$red-team-review`
   - `$rollback-safety`
4. Run any additional review skills selected by `$risk-router`
5. Run `$merge-review`
6. If findings conflict or overlap ambiguously, run `$consensus-review`

Do not run all review skills by default unless the change is explicitly high risk.

## Default Risk Routing Rules

Use additional review skills only when the change indicates they are needed.

- Run `$architecture-review` when the change adds modules, changes layering, or alters ownership boundaries.
- Run `$blast-radius-analysis` when the change touches shared code, configuration, migrations, or multiple services.
- Run `$debug-observability-review` when the change affects production debugging, adds logs, adds flags, or is hard to reproduce locally.
- Run `$performance-regression` when the change affects loops, queries, caching, hot paths, or resource usage.
- Run `$concurrency-safety` when the change affects async workflows, queues, locks, retries, workers, or shared mutable state.
- Run `$input-validation` when the change adds or changes parsing, payloads, endpoints, forms, or webhook handlers.
- Run `$api-contract-review` when the change affects public APIs, schemas, contracts, or exported models.
- Run `$data-integrity-review` when the change writes state, updates transactions, changes migrations, or affects idempotency.
- Run `$operational-risk` when the change touches retries, queues, external dependencies, long-running jobs, or rollout behavior.

## Builder Rules

When implementing changes:
- prefer the smallest safe change
- avoid unnecessary refactors
- add observability at critical state transitions
- avoid sensitive logging
- gate risky behavior behind feature flags when appropriate
- update `.agent/state.md` after meaningful work

If the system requires deployment to a test environment for debugging:
- optimize for remote traceability
- make rollback simple
- document validation steps explicitly

## Reviewer Rules

All reviews must:
- identify concrete failure modes
- avoid generic advice
- prioritize correctness and abuse resistance over style nitpicks
- explicitly evaluate debug impact and rollback risk

Assume:
- hostile inputs
- replayed messages
- partial failures
- misconfigured flags
- debug code may remain enabled

## Incident Learning

When a postmortem or incident analysis is available:
- run `$incident-learning`
- append durable lessons to `.agent/incident-lessons.md` or skill `references/incident-lessons.md`
- prefer adding incident lessons in references files rather than rewriting the main `SKILL.md` unless the core workflow truly changes
