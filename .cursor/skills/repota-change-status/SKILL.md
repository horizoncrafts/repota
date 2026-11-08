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

THe status change means moving the .md file to appropriate folder under `.repota/` or removing status ("Inbox") by moving to `.repota/`.
If a new status is required and justified (judge on your own) create a subfolder under `.repota/`.

Commit and push the change immediately.
