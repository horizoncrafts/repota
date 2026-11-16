---
name: repota-change-status
description: When changing status of a task
paths:
  - ".repota/**/*.md"
disable-model-invocation: false
icon: lightning
color: yellow
---

Read the shared [Repota convention](../references/convention.md) before proceeding. Resolve this path relative to this skill's directory. Apply the convention to the user's target repository.

If a new status is required and justified (judge on your own), create a new status subfolder under `.repota/`.

Commit the change immediately. Push only if the repository's rules allow pushing directly (for example, no branch protection or PR-only workflow); otherwise leave it committed and say so.
