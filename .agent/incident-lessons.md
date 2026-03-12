# Incident Lessons

Append one section per incident.

## 2026-03-12 Repository bootstrap drift
- Failure pattern: Repository-level instructions referenced `.agent/` files that only existed in the template copy, not in the repository root.
- Why it happened: The repo template was imported without keeping the root `.agent/` scaffold aligned.
- Which review skill should catch it: `linus-review`, `blast-radius-analysis`
- New checks to apply: When adding or renaming workflow files, verify root docs, repo templates, and shipped scaffold files stay in sync.
