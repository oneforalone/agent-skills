---
name: oversized-file-refactor
description: Use when a non-generated source file may exceed 1200 lines or the user asks to split a large file. Check `wc -l`; if the file is over 1200 lines, invoke `linus-review` and `pua-debugging`, do the smallest safe refactor, preserve behavior unless asked otherwise, and run relevant verification.
---

# Oversized File Refactor

Only for non-generated source files; skip vendored code, lockfiles, snapshots, minified bundles, and append-only migrations unless explicitly asked otherwise.

1. Run `wc -l <path>`.
2. If the file is `<= 1200` lines, stop.
3. If the file is `> 1200` lines, invoke `$linus-review` and `$pua-debugging`, then do the smallest safe refactor without mechanical splitting or API drift.
4. Run the narrowest relevant verification and report leftovers.
