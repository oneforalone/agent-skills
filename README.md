# Install Guide

## Included skills
This repository includes the core routed review skills plus a small debugging bundle:

- `pua-debugging`: pushes for exhaustive investigation and stronger end-to-end ownership when work gets stuck.
- `oversized-file-refactor`: enforces a 1200-line ceiling for source files by requiring `linus-review` and `pua-debugging` before refactoring oversized files.
- `verification-before-completion`: requires fresh verification evidence before claiming a task is fixed or complete.
- `systematic-debugging`: enforces root-cause investigation before proposing fixes, with additional supporting reference files.
- `python-uv-workflow`: standardizes `uv`-based Python project work around `uv`, `ruff`, and `ty`.

## 1. Global setup
Copy the repository-root `AGENTS.md` into `~/.codex/AGENTS.md`.

Install the default skill set from `skills/` into `~/.codex/skills/`, but keep `pua-debugging` and `oversized-file-refactor` opt-in because the refactor skill explicitly depends on `pua-debugging` and inherits its stronger tone and workflow.

```bash
rsync -a --exclude 'pua-debugging' --exclude 'oversized-file-refactor' skills/ ~/.codex/skills/
```

If you explicitly want `pua-debugging`, install it separately:

```bash
cp -R skills/pua-debugging ~/.codex/skills/
```

If you also want the 1200-line oversized-file rule, install the companion skill after `pua-debugging`:

```bash
cp -R skills/oversized-file-refactor ~/.codex/skills/
```

## 2. Repository setup
Copy `repo-template/AGENTS.md` into your repository root as `AGENTS.md`.
Copy `repo-template/.agent/` into your repository root.

The split is intentional:
- repository-root `AGENTS.md` is the global Codex policy
- `repo-template/AGENTS.md` is the repository-local template for downstream projects

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
