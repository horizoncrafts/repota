---
name: repota-run
description: Use this when asked to find and execute open repota tasks (.repota/ folders) across the owner's repositories.
---
# Run open repota tasks

Read the repota convention first (`README.md` and `.cursor/skills/references/convention.md` in the repota repository).

## 1. Find work (read-only)
- List every repo the owner's connected source-control accounts and orgs can see (GitHub via the built-in GitHub tools, plus Cursor Origin). Skip archived repos.
- For each, check the default branch for `.repota/`. Code search is unreliable for dot-folders; check per repo.
- Read the repo's own instructions (AGENTS.md, CLAUDE.md, README, `.repota/` notes) to learn which statuses mean completed.
- A task is open if it is in the inbox or in a status dir that isn't done/closed/cancelled/superseded (ignore `.repota/_additional-info/`).

## 2. Execute, one task at a time
- Never run several coding agents in parallel. Finish one repo's tasks (in a sensible order) before starting the next.
- Work directly on the default branch (`main`) unless the repo or task says otherwise. No feature branches, no pull requests.
- Pick the runner:
  1. Local CLIs on the bot's computer, if set up: Claude Code (`claude -p`, auth via `CLAUDE_CODE_OAUTH_TOKEN`) and Codex (`codex exec`, ChatGPT login). Check remaining subscription capacity first (Claude `/usage`, Codex `/status`) and use whichever has room. Clone into /workspace, let the CLI do the work, then commit and push to `main` with the bot's git identity (a dedicated GitHub account).
  2. Otherwise a Cursor cloud agent, told explicitly to commit and push straight to `main` with no branch or PR.
- Brief the runner with: the repota convention, the repo's instructions, the task file as the spec, and: when done move the file into the repo's done status dir (create one like `.repota/done/` if none); if blocked leave it and explain in the task body; for a limited-choice decision, decide and note it in the task body rather than asking (repota values: minimize user attention).
- Verify (build, tests, or a quick render check) before pushing.

## 3. Report
Per task: what changed, done or blocked and why, commit SHAs on `main`, screenshots if visual, and anything needing the owner's eyes.
