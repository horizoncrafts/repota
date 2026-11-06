# Repota bot for Grok Bot

A Grok Bot template for an assistant that finds repositories using the repota convention (see [docs/repota.md](../../docs/repota.md)) and executes their open tasks one at a time, committing straight to `main`.

It runs tasks with whichever coding runner has capacity: Claude Code or Codex on the bot's own computer (using your existing subscriptions), with Cursor cloud agents as the fallback.

## Contents

- `skills/repota-run/SKILL.md`: the job. Find repos with open tasks, execute them one at a time, report.
- `skills/repota-getting-started/SKILL.md`: the first conversation with a new owner. It covers connecting source control, installing and signing in Claude Code and Codex, and giving the bot a git identity that can push.

## Defaults

- Work on `main` unless the repository or task says otherwise. No feature branches, no pull requests.
- One task at a time, never several coding agents in parallel.
- Finished tasks move into the repository's done status directory. Blocked tasks stay put with an explanation in the task body.
- Limited-choice decisions are made by the bot and noted in the task body, not asked.

## Setup summary

1. Connect GitHub (or Cursor Origin) to the bot.
2. Optional coding CLIs on the bot's computer:
   - Claude Code: `npm install -g @anthropic-ai/claude-code`, then run `claude setup-token` on your own machine and give the bot the token as the secret `CLAUDE_CODE_OAUTH_TOKEN`.
   - Codex: `npm install -g @openai/codex`, then `codex login --device-auth` on the bot's computer, approved from your own device.
3. Git push identity: create a dedicated GitHub account for the bot from your own machine, ideally with a `+bot` alias of your own email. Sign the bot's computer in with `gh auth login --web` (approve as the bot), then `gh auth setup-git`. Invite the account to your org and grant it Write.
4. Optionally add a routine that scans for open tasks on a schedule.
