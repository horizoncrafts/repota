# Repota

A minimal convention for tracking development tasks inside a repository, without an external tracker and close to the code.

See [.cursor/skills/references/convention.md](.cursor/skills/references/convention.md) for the rules and examples.

## Install in Codex

Register the repository marketplace and install Repota in Codex CLI.

```sh
codex plugin marketplace add horizoncrafts/repota
codex plugin add repota@repota
```

To install from a local checkout during development, replace `horizoncrafts/repota` with the absolute path to this repository. Start a new chat after installation. In Codex desktop, select the Repota marketplace in Plugins and install Repota.

In the repository whose tasks you want to manage, ask Codex to create a Repota task, change a task's status, or check `.repota/` for consistency. You can also select `repota:repota-new-task`, `repota:repota-change-status`, or `repota:repota-integrity` through `/skills` in Codex CLI.

The skills load the bundled convention and operate on the current project's `.repota/` directory.

## Install in Cursor

Customize → Plugins → + Add → From GitHub Repository, then paste `https://github.com/horizoncrafts/repota`. Install Repota for your user or for one project.

## Values

- human-first - everything can be easily managed by a human. Additional tools, AI skills are welcome but mustn't be critical.
- minimalistic convention - simple files, no frontmatter headers.
- no redundancy - always checking for duplicated or unnecessary items or knowledge.
- minimize user attention - users mustn't be bothered. Don't expect users to come with a solution or respond to questions. Users respond when they intentionally check task progression. When a limited-choice decision is needed, decide and note it in the task body rather than asking.
