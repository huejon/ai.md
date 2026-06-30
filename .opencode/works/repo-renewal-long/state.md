# State

## 2026-06-30

Loop state: `apply` -> `evaluate`.

The current run implements an explicit cleanup request. Legacy local prompt-copy/deployment directories and noisy OpenCode dependency/package artifacts have been removed locally. Root docs, OpenCode overlay docs, harness cleanup notes, and this ledger are being updated to reflect the retained canonical layout.

Existing worktree changes were present before this run, including prior renewal edits and deleted root `j-qa.md`/`j-rev.md`. This run intentionally changes the requested cleanup paths plus documentation/ledger references needed to keep the repository coherent.

Boundary: OpenCode will not commit or push in this run; Hermes will perform final commit/push after validation.
