# Install Guide

## Included skills
This repository includes the core routed review skills plus a small debugging bundle:

- `pua-debugging`: pushes for exhaustive investigation and stronger end-to-end ownership when work gets stuck.
- `verification-before-completion`: requires fresh verification evidence before claiming a task is fixed or complete.
- `systematic-debugging`: enforces root-cause investigation before proposing fixes, with additional supporting reference files.

## 1. Global setup
Copy `AGENTS.md` into `~/.codex/AGENTS.md`.

Copy every folder under `skills/` into `~/.codex/skills/`.

## 2. Repository setup
Copy `repo-template/AGENT.md` into your repository root as `AGENT.md`.
Copy `repo-template/.agent/` into your repository root.

## 3. Verify
Run:

```bash
codex --ask-for-approval never "Summarize the current instructions."
codex --ask-for-approval never "List the skills that are available."
```

## 4. Review entrypoint
For non-trivial review, invoke:

```text
$pipeline-review
```

## 5. Incident learning
When you finish a postmortem, invoke:

```text
$incident-learning
```

and append the lesson into `.agent/incident-lessons.md`.
