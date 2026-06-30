# Run Log

## 2026-06-30 — local runner policy cleanup

### Startup

- Loaded `/var/home/core/.config/local-runner/references/work-command.md` with the requested Python command.
- Ran `git log --oneline -10` and `date` in `/var/home/core/workspace/jonloureiro/ai.md`.
- Read `AGENTS.md`, `README.md`, `knowledge/INDEX.md`, and `cron-harness/README.md`.
- Inspected `CLAUDE.md`, `work-ledgers/`, and existing worktree state.

### Changes

- Removed root `CLAUDE.md` entirely.
- Added `prior local-overlay policy file` with concise local runner-specific policy.
- Reconciled root `AGENTS.md` and `README.md` policy lines with the requested no-human-review-gate/direct-push-after-validation policy.
- Created the first durable renewal ledger files in the prior local overlay location.

### Notes

- Pre-existing worktree changes were present before this run. This run intentionally touched `AGENTS.md` and `README.md` only to reconcile the requested local runner push/review-gate policy.
- `LICENSE` was not edited.

### Validation

- `git diff --check` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves no diff whitespace errors/conflict markers.
- `git diff -- LICENSE` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves `LICENSE` has no diff.
- `git status` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; showed the expected dirty worktree, including removed legacy files, new local-overlay policy/ledger files, pre-existing `D j-qa.md`/`D j-rev.md`, and other pre-existing changes. Proves no commit/push occurred and shows final worktree state.

### Reviews and Judges

- Initial review panel found a root policy contradiction and missing handoff validation evidence.
- Fixed both issues by reconciling root policy wording and recording validation evidence.
- Post-fix `review-qwen`, `review-glm`, and `review-kimi` returned PASS.
- `judge-qwen` returned ACCEPT; `judge-glm` returned ACCEPT WITH NOTES.
- Previous review summary was removed during the later legacy-directory cleanup because it described deleted local deployment-copy directories as active.

## 2026-06-30 — Legacy directory removal and local runner overlay pruning

### Startup and inspection

- Loaded `/var/home/core/.config/local-runner/references/work-command.md` with the requested Python command.
- Ran `git log --oneline -10` and `date` in `/var/home/core/workspace/jonloureiro/ai.md`.
- Read `README.md`, `knowledge/INDEX.md`, `cron-harness/README.md`, `prior local-overlay README`, `prior local-overlay config`, `prior local-overlay command source`, and the active ledger files.
- Inspected relevant trees and references with `Glob`, `Grep`, and `git ls-files` before deletion.

### Changes

- Removed `.agents/`, `.claude/`, `.factory/`, and `prior local-overlay agent-copy directory/` entirely.
- Removed `prior local-overlay dependency directory/`, `prior local-overlay package manifest`, `prior local-overlay package lockfile`, and `prior local-overlay ignore file`.
- Removed stale prior ledger findings/review files that described deleted local deployment-copy directories as active.
- Updated root `AGENTS.md`, root `README.md`, `prior local-overlay README`, and `cron-harness/cleanup-plan.md` to match the new repository layout.
- Updated this ledger with current scope, decisions, and handoff.

### Notes

- `LICENSE` was not edited.
- local runner did not commit or push; coordinating process will do final commit/push.

### Initial verification

- `git diff --check` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves no diff whitespace errors/conflict markers at this point.
- `git diff -- LICENSE` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves `LICENSE` has no diff at this point.
- `git status --short` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; showed expected deletions under legacy local directories and `prior local-overlay agent-copy directory/`, modifications to docs/ledger, and no commit/push.

### Review panel

- `review-qwen`: PASS; noted no blocking issues and suggested follow-up cleanup of stale scenario/delegation references.
- `review-glm`: PASS; noted no blocking issues and confirmed retained canonical root directories and minimal `work-ledgers/` file set.
- `review-kimi`: initially FAIL only because empty local `work-ledgers/prompts`, `work-ledgers/skills`, `reviews`, and `proposals` directories remained on disk; fixed by removing those empty directories.

### Final verification and judges

- Prior local-overlay directory inventory via Python in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; only the command directory and active renewal ledger subdirectories remained at that point.
- Final `git diff --check` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves no whitespace errors or conflict markers.
- Final `git diff -- LICENSE` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; no output. Proves `LICENSE` has no diff.
- Final `git status --short` in `/var/home/core/workspace/jonloureiro/ai.md`: exit 0; showed expected uncommitted deletions of legacy local directories and `prior local-overlay agent-copy directory`, expected doc/ledger modifications, and two new ledger artifacts. Proves local runner did not commit/push.
- `judge-qwen`: ACCEPT.
- `judge-glm`: ACCEPT.

## 2026-06-30 — Vendor/tool-name neutralization

### Startup and inspection

- Loaded the work command reference with the Python command requested by the user.
- Ran `git log --oneline -10` and `date` in the repository root.
- Read `AGENTS.md`, `README.md`, `knowledge/INDEX.md`, `cron-harness/README.md`, and prior active ledger files.
- Inspected tracked files and found explicit references in root docs, harness docs, knowledge research, skills, and the tracked local runtime overlay.

### Changes

- Added root ignore coverage for the local-only runtime overlay without spelling the forbidden term in tracked text.
- Moved useful durable ledger history to `work-ledgers/repo-renewal-long/`.
- Removed the prior local runtime overlay from git tracking.
- Updated tracked documentation and research/skill artifacts to neutral terminology.

### Initial validation

- `git ls-files local runtime overlay` in the repository root: exit 0; no output after index removal, proving the local runtime overlay is no longer in the tracked index.
- `git check-ignore local runtime overlay/example` in the repository root: exit 0; output `local runtime overlay/example`, proving the root ignore pattern covers the local-only overlay.
- Case-insensitive tracked-file scan for the requested tool/vendor terms in the repository root: exit 0; output `No tracked-file matches for coordinating-process|local-runner`.
- `git diff --check` in the repository root via Python subprocess: exit 0; no output besides `EXIT_CODE=0`.
- `git diff -- LICENSE` in the repository root via Python subprocess: exit 0; no diff output besides `EXIT_CODE=0`.
- `git status --short` in the repository root via Python subprocess: exit 0; shows staged local-runtime-overlay deletions, modified neutral docs, and untracked `.gitignore`/`work-ledgers/` before final staging.

### Review panel

- `review-qwen`: PASS; noted no blocking issues and confirmed scan, ignore, license, and no-commit evidence.
- `review-glm`: PASS; noted no blocking issues and confirmed the local-only overlay and neutral ledger location.
- `review-kimi`: FAIL; found that `.gitignore` and `work-ledgers/` were untracked and that useful prior ledger history had not been fully preserved. Fixed by restoring prior ledger content into `work-ledgers/repo-renewal-long/` and preparing the new tracked files for the final index.
