# State

## 2026-06-30

Loop state: `apply` -> `evaluate`.

The current run implements an explicit cleanup request. Legacy local prompt-copy/deployment directories and noisy local runner dependency/package artifacts have been removed locally. Root docs, local runner overlay docs, harness cleanup notes, and this ledger are being updated to reflect the retained canonical layout.

Existing worktree changes were present before this run, including prior renewal edits and deleted root `j-qa.md`/`j-rev.md`. This run intentionally changes the requested cleanup paths plus documentation/ledger references needed to keep the repository coherent.

Boundary: local runner will not commit or push in this run; the coordinating process will perform final commit/push after validation.

The active durable ledger now lives under `work-ledgers/repo-renewal-long/`. The local runtime overlay remains on disk for local use but has been removed from the tracked index and is covered by the root ignore pattern.
