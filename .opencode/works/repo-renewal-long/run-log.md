# Run Log

## 2026-06-30 — OpenCode policy cleanup

### Startup

- Loaded `/var/home/core/.config/opencode/references/work-command.md` with the requested Python command.
- Ran `git log --oneline -10` and `date` in `/var/home/core/workspace/jonloureiro/ai.md`.
- Read `AGENTS.md`, `README.md`, `knowledge/INDEX.md`, and `cron-harness/README.md`.
- Inspected `CLAUDE.md`, `.opencode/`, and existing worktree state.

### Changes

- Removed root `CLAUDE.md` entirely.
- Added `.opencode/AGENTS.md` with concise OpenCode-specific policy.
- Reconciled root `AGENTS.md` and `README.md` policy lines with the requested no-human-review-gate/direct-push-after-validation policy.
- Created `.opencode/works/repo-renewal-long/` durable ledger files.

### Notes

- Pre-existing worktree changes were present before this run. This run intentionally touched `AGENTS.md` and `README.md` only to reconcile the requested OpenCode push/review-gate policy.
- `LICENSE` was not edited.

### Validation

- `git diff --check` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves no diff whitespace errors/conflict markers.
- `git diff -- LICENSE` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves `LICENSE` has no diff.
- `git status` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; showed expected dirty worktree including `D CLAUDE.md`, new `.opencode/AGENTS.md`, `.opencode/works/`, pre-existing `D j-qa.md`/`D j-rev.md`, and other pre-existing changes. Proves no commit/push occurred and shows final worktree state.

### Reviews and Judges

- Initial review panel found a root policy contradiction and missing handoff validation evidence.
- Fixed both issues by reconciling root policy wording and recording validation evidence.
- Post-fix `review-qwen`, `review-glm`, and `review-kimi` returned PASS.
- `judge-qwen` returned ACCEPT; `judge-glm` returned ACCEPT WITH NOTES.
- Previous review summary was removed during the later legacy-directory cleanup because it described deleted local deployment-copy directories as active.

## 2026-06-30 — Legacy directory removal and OpenCode overlay pruning

### Startup and inspection

- Loaded `/var/home/core/.config/opencode/references/work-command.md` with the requested Python command.
- Ran `git log --oneline -10` and `date` in `/var/home/core/workspace/jonloureiro/ai.md`.
- Read `README.md`, `knowledge/INDEX.md`, `cron-harness/README.md`, `.opencode/README.md`, `.opencode/opencode.jsonc`, `.opencode/command/daily-cron.md`, and the active ledger files.
- Inspected relevant trees and references with `Glob`, `Grep`, and `git ls-files` before deletion.

### Changes

- Removed `.agents/`, `.claude/`, `.factory/`, and `.opencode/agents/` entirely.
- Removed `.opencode/node_modules/`, `.opencode/package.json`, `.opencode/package-lock.json`, and `.opencode/.gitignore`.
- Removed stale prior ledger findings/review files that described deleted local deployment-copy directories as active.
- Updated root `AGENTS.md`, root `README.md`, `.opencode/README.md`, and `cron-harness/cleanup-plan.md` to match the new repository layout.
- Updated this ledger with current scope, decisions, and handoff.

### Notes

- `LICENSE` was not edited.
- OpenCode did not commit or push; Hermes will do final commit/push.

### Initial verification

- `git diff --check` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves no diff whitespace errors/conflict markers at this point.
- `git diff -- LICENSE` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves `LICENSE` has no diff at this point.
- `git status --short` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; showed expected deletions under legacy local directories and `.opencode/agents/`, modifications to docs/ledger, and no commit/push.

### Review panel

- `review-qwen`: PASS; noted no blocking issues and suggested follow-up cleanup of stale scenario/delegation references.
- `review-glm`: PASS; noted no blocking issues and confirmed retained canonical root directories and minimal `.opencode/` file set.
- `review-kimi`: initially FAIL only because empty local `.opencode/prompts`, `.opencode/skills`, `reviews`, and `proposals` directories remained on disk; fixed by removing those empty directories.

### Final verification and judges

- `.opencode` directory inventory via Python in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; directories are only `.opencode/command`, `.opencode/works`, `.opencode/works/repo-renewal-long`, `.opencode/works/repo-renewal-long/findings`, and `.opencode/works/repo-renewal-long/reviews`.
- Final `git diff --check` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves no whitespace errors or conflict markers.
- Final `git diff -- LICENSE` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves `LICENSE` has no diff.
- Final `git status --short` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; showed expected uncommitted deletions of legacy local directories and `.opencode/agents`, expected doc/ledger modifications, and two new ledger artifacts. Proves OpenCode did not commit/push.
- `judge-qwen`: ACCEPT.
- `judge-glm`: ACCEPT.
