# State

## 2026-06-30

Loop state: `apply` -> `evaluate`.

The current run implements an explicit deeper cleanup request. Root `CLAUDE.md` was removed, `.opencode/AGENTS.md` was added for OpenCode-specific repository policy, root `AGENTS.md` and `README.md` were reconciled with that policy, and the durable ledger was created for future renewal continuity.

Existing worktree changes were present before this run (`AGENTS.md`, `README.md`, deleted `j-qa.md`/`j-rev.md`, untracked `.opencode/**`, and `cron-harness/**`). This run intentionally changed `CLAUDE.md`, `.opencode/AGENTS.md`, `.opencode/works/repo-renewal-long/**`, and minimal policy lines in `AGENTS.md`/`README.md` to avoid contradictory push/review-gate instructions.
