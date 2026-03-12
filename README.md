# Install Guide

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
$review-pipeline
```

## 5. Incident learning
When you finish a postmortem, invoke:

```text
$incident-learning
```

and append the lesson into `.agent/incident-lessons.md`.
