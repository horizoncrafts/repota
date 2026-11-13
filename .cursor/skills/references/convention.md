---
description: Repository task convention for .repota/. Use when creating, editing, moving, or checking repota tasks.
alwaysApply: false
globs: ".repota/**/*.md"
---

# Repository task convention

## Storage and status

Tasks live in `.repota/`. Each task is one Markdown file. Files directly in `.repota/` form the inbox and have no status. Create new tasks there.

Assign a status by moving a task into a direct subdirectory of `.repota/`. Each project chooses its own status names and meanings; no statuses are required or fixed. For example:

```text
.repota/
├── add-dark-mode.md
├── open/
├── in-progress/
└── closed/
```

Here, `add-dark-mode.md` has no status; `open/`, `in-progress/`, and `closed/` are only example status directories.

The containing directory is the sole source of status. Change status by moving the Markdown file while preserving its filename. Move it back to `.repota/` to remove its status and return it to the inbox. Each task must exist in exactly one location: the inbox or a status directory. Do not nest directories inside status directories.

`.repota/_additional-info/` is a special reserved directory, not a status directory. Use it only for shared supporting documents when multiple tasks need the same context and no suitable location exists elsewhere in the repository. Files inside `.repota/_additional-info/` are not tasks.

Retain completed, cancelled, and superseded tasks in the repository. Explain cancellation or supersession in the task body.

## Identity

The filename identifies the task independently of its directory.

- Use descriptive, lowercase, hyphen-separated filenames, such as `add-dark-mode.md`.
- Filenames must be unique across the inbox and all status directories.
- Prefer to keep the filename unchanged throughout the task's lifecycle.
- Do not reuse a task's filename for different work.

## Contents

Contents of a task file are unrestricted. Mind it will be fed to a task executor, so

- follow typical conventions (idea, description, acc criteria, references, ...) that work the best
- try to keep it consistent within the project

Avoid using frontmatter or structured fields for ID, status, assignee, dependencies, creation date, type, priority, or external reference. Everything can actually be just a text. Even estimates can be simply another paragraph (method, math) rather than a structured field. Express relevant relationships and references naturally in the body. Git provides change history.

Checkboxes may describe progress within a task; they do not determine its status.

## References

Refer to other tasks by their full filename, such as `add-dark-mode.md`, independent of their current directory. Tools resolving task references must search the inbox and every status directory.

Do not use ordinary path-based Markdown links as durable task references: moving a task between the inbox and status directories changes its path.

Do not copy shared context into task files; reference existing files instead. Any file paths mentioned in a task body must point outside `.repota/`, except `.repota/_additional-info/`.