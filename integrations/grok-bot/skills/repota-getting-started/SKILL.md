---
name: repota-getting-started
description: Use this as the first conversation of a newly imported Repota bot with its new owner, to set up repositories, coding CLIs and git push access.
---
# Getting started (Repota)

You find repositories that use the repota convention with open tasks in `.repota/`, and execute those tasks one at a time, committing straight to `main`. Say that in one line, then set up, asking ONE thing at a time and acting on each answer before the next.

1. **Source control.** Check whether GitHub (and/or Cursor Origin) is reachable with the built-in source-control tools. If not, show the connect card. Ask whether any orgs or repos should be excluded.
2. **Rules.** Confirm the defaults: work on `main` unless a repo says otherwise, no branches or PRs, one task at a time. Save their answer to memory.
3. **Coding runners.** Ask whether they have Claude and/or ChatGPT subscriptions to use for coding. If yes, install the CLIs on your computer (`npm install -g @anthropic-ai/claude-code @openai/codex`, add `~/.local/bin` to PATH), then:
   - Claude Code: ask them to run `claude setup-token` on their own machine and paste the token into a secret request named `CLAUDE_CODE_OAUTH_TOKEN`. Verify with `claude -p "Reply with just: ok"`.
   - Codex: run `codex login --device-auth` on your computer and give them the link and one-time code to approve on their own device. Verify with `codex exec --skip-git-repo-check "Reply with just: ok"`.
   If they have neither, use Cursor cloud agents only and skip step 4.
4. **Git push identity.** Recommend a dedicated GitHub bot account so pushes are distinguishable and access can be revoked. They create it themselves on their own machine (your computer's IP is often blocked from GitHub sign-up), ideally with a `+bot` alias of their own email so recovery stays with them. Then run `gh auth login --web` and have them approve the device code while signed in as the bot; run `gh auth setup-git` and set git user.name/email to the bot's noreply address. Have them invite the bot to the org and grant Write (per repo, or org base permission). Verify with `gh api repos/<owner>/<repo> --jq .permissions.push`.
5. **Schedule.** Offer a routine that scans for open repota tasks on a schedule they pick (e.g. every morning).

Save each setup fact to memory as you go (never secrets), then run @repota-run for the first scan and report what you found before executing anything.
