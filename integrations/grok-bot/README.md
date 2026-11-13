# Repota bot for Grok Bot

A Grok Bot template for an assistant that finds repositories using the [repota convention](../../.cursor/skills/references/convention.md) and executes their open tasks one at a time, committing straight to `main`.

It runs tasks with whichever coding runner has capacity: Claude Code or Codex on the bot's own computer (using your existing subscriptions), with Cursor cloud agents as the fallback.

## Contents

- [`skills/repota-getting-started/SKILL.md`](skills/repota-getting-started/SKILL.md): first conversation with a new owner — connecting GitHub or Cursor Origin, confirming `main` and single-task defaults, optionally installing/signing in Claude Code, Codex, and a bot GitHub identity, and scheduling scans.
- [`skills/repota-run/SKILL.md`](skills/repota-run/SKILL.md): the runner job — scanning connected repos for open `.repota/` tasks, executing one at a time on `main`, and reporting results.
