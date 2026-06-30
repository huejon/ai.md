# Finding — active scope refresh

Date: 2026-06-30

## Summary

The active `work.md` scope still described a completed destructive cleanup run as the current task, including deletion-oriented bullets and a run-specific no-commit boundary. That made future `repo-renewal-long` continuations easier to misread as another cleanup pass instead of the reusable long-horizon renewal loop defined by `cron-harness/README.md`.

## Evidence

- Pre-refresh `work-ledgers/repo-renewal-long/work.md` lines 7-15 described removal of legacy directories, pruning local overlay artifacts, and a specific "do not commit or push inside local runner" boundary from an older run.
- `cron-harness/README.md` lines 7-21 defines the reusable run contract: one loop state, one narrow objective, safe reversible changes, checklist evaluation, and durable ledger updates.
- `cron-harness/README.md` lines 48-52 already defines the current commit/push precedence guard, so the old run-specific `work.md` commit wording was no longer the right active scope contract.

## Renewal Action

Refresh `work.md` so it states the reusable active scope contract for future continuations rather than the completed cleanup task. Keep historical cleanup evidence in the older ledger entries and cleanup finding.

## Acceptance Criteria

- `work.md` names the durable recurring objective and active scope contract.
- `work.md` points future workers to the harness and current ledger before selecting one narrow objective.
- The refreshed scope preserves safety boundaries for `LICENSE`, secrets, deletion, and commit/push precedence.
- No historical ledger evidence is deleted.

## Rollback

Revert the `work.md` change and remove this finding if a future run intentionally turns `repo-renewal-long` back into a one-off cleanup-only ledger.
