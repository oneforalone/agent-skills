# State

- Date: 2026-03-12
- Status: repository initialized and extended with imported skills
- Notes:
  - Added a repository-level `.gitignore` for local OS/editor/cache artifacts.
  - Created the initial repository commit.
  - Added `skills/pua-debugging/SKILL.md` from the provided GitHub source.
  - Added `skills/verification-before-completion/` from `obra/superpowers`.
  - Added `skills/systematic-debugging/` from `obra/superpowers`.
  - Updated `README.md` to document the imported debugging skills.
  - Renamed review orchestration skills to use the `*-review` suffix consistently.
  - Fixed review findings by making `pua-debugging` opt-in, restoring root `.agent/` scaffolding, and sanitizing imported skill references.
  - Added `skills/python-uv-workflow/` for Python projects that standardize on `uv`, `ruff`, and `ty`.
  - Narrowed `python-uv-workflow` so it only applies to uv-based repos or explicit uv standardization requests.
