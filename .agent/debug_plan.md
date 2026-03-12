# Debug Plan

Required instrumentation:
- Verify repository instructions against files that actually exist.
- Verify imported skill docs for stale paths after edits.

Validation steps:
- Confirm root `.agent/` contains the files referenced by `AGENT.md`.
- Search the repository for stale `systematic-debugging` path references.
- Read the install section in `README.md` to confirm `pua-debugging` is opt-in only.

Sensitive logging constraints:
- Do not log secrets, tokens, raw credentials, or private customer data.
