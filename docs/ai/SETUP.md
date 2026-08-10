# One-time setup

## Labels
Create:
`ai-build`, `ai-review`, `ai-fix`, `human-check`, `ha-dashboard`,
`ha-automation`, `ha-integration`, `safe-to-merge`.

## Claude
Claude Code supports project instructions in `CLAUDE.md`.
For GitHub-native operation, Anthropic documents installing its GitHub integration
from Claude Code with `/install-github-app`. Keep API credentials in GitHub Secrets.

Suggested flow:
1. Open an issue from the AI build template.
2. Ask Claude to implement it.
3. Claude creates/updates a PR.
4. Claude finishes with `STATUS: REVIEW_REQUESTED`.

## Codex
Connect this repository as a Codex environment.
Codex supports `AGENTS.md` repository instructions and GitHub PR review.
Enable automatic Codex PR review for this repo if desired, or use `@codex review`.

Do not enable automatic merge.

## Interaction loop

Issue
→ Claude implementation
→ PR + hand-off
→ Codex review
→ Claude fix pass
→ Codex re-review
→ `human-check`
→ Human test/merge

GitHub is the conversation; the agents do not need a private chat channel.

## Autonomy boundary

Agents may create branches, edit files, run validation, open PRs, comment,
review, and iterate.

Human approval remains required for merge to `main`, auth/network changes,
secrets, security devices, physical-device automation changes, and ambiguous
entity mappings.
