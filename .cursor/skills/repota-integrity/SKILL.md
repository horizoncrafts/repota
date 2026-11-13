---
name: repota-integrity
description: Verify, report and optionally fix consistency issues in the `.repota/` folder.
paths:
  - ".repota/**/*.md"
disable-model-invocation: false
icon: shield
color: blue
---

# Integrity

Read the shared [Repota convention](../references/convention.md) before proceeding. Resolve this path relative to this skill's directory. Apply the convention to the user's target repository.

Run on every addition, rename, or edit of a `.md` file in `.repota/`, or when asked to check `.repota/`:

- Verify `.repota/` against every rule in the convention (storage and the special `.repota/_additional-info/` directory, filename identity and uniqueness, body contents, and task/file references).
- Report any violations and optionally fix them.
