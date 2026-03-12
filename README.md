# Install Guide

## Included skills
This repository includes the core routed review skills plus a small debugging bundle:

- `pua-debugging`: pushes for exhaustive investigation and stronger end-to-end ownership when work gets stuck.
- `verification-before-completion`: requires fresh verification evidence before claiming a task is fixed or complete.
- `systematic-debugging`: enforces root-cause investigation before proposing fixes, with additional supporting reference files.
- `python-uv-workflow`: standardizes `uv`-based Python project work around `uv`, `ruff`, and `ty`.

## 1. Global setup
Copy `AGENTS.md` into `~/.codex/AGENTS.md`.

Install the default skill set from `skills/` into `~/.codex/skills/`, but keep `pua-debugging` opt-in because it intentionally changes tone and trigger behavior.

```bash
rsync -a --exclude 'pua-debugging' skills/ ~/.codex/skills/
```

If you explicitly want `pua-debugging`, install it separately:

```bash
cp -R skills/pua-debugging ~/.codex/skills/
```

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
