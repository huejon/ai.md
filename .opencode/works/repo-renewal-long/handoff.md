# Handoff — repo-renewal-long

## Current State

Requested cleanup has been applied locally:

- Root `CLAUDE.md` removed.
- `.opencode/AGENTS.md` added with OpenCode-specific policy: no human review gate, OpenCode/Hermes may commit and push directly to `main` after validation.
- Root `AGENTS.md` and `README.md` policy lines reconciled so they do not contradict the OpenCode-specific policy.
- Durable ledger created/updated under `.opencode/works/repo-renewal-long/`.
- `LICENSE` preserved.
- No secrets added.

## Validation Evidence

Executed in `/var/home/core/workspace/jonloureiro/ai.md`:

- `git diff --check` — exit 0; no output. Proves no whitespace errors or conflict markers in the diff.
- `git diff -- LICENSE` — exit 0; no output. Proves `LICENSE` was preserved without modifications.
- `git status` — exit 0; showed `D CLAUDE.md`, `?? .opencode/AGENTS.md`, `?? .opencode/works/`, plus pre-existing unrelated changes. Proves the worktree remains uncommitted/unpushed for Hermes final handling.

## Existing Worktree Context

Before this run, `git status --short` already showed modified `AGENTS.md`, `README.md`, deleted `j-qa.md`/`j-rev.md`, and untracked `.opencode/**` plus `cron-harness/**`. This run intentionally changed the requested cleanup/policy files, this ledger, and minimal root policy wording needed to resolve the direct-push/no-human-review-gate conflict.

## Next Action

Hermes should perform final commit/push outside OpenCode as requested, staging only intended files after reviewing the dirty worktree. Review/judge consensus is recorded in `reviews/2026-06-30-review-summary.md`.
