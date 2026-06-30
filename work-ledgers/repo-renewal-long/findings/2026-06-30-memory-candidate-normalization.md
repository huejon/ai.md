# Finding — memory candidate normalization

Date: 2026-06-30

## Objective

Primary loop state: `learn`; supporting actions: `apply` and `evaluate`.

Normalize the active `memory-candidates.md` policy candidate so future workers do not inherit obsolete placeholder wording from the earlier local-overlay cleanup history.

## Evidence

- The prior handoff suggested the next objective: review `memory-candidates.md` for obsolete local-overlay wording and either normalize it or move it into historical decisions only.
- `memory-candidates.md` line 6 referred to `prior local-overlay policy file`, a historical placeholder that no longer names a tracked canonical artifact.
- Current root policy and harness files (`AGENTS.md`, `README.md`, `cron-harness/README.md`) already define the durable tracked policy surface and active-instruction commit/push precedence.

## Change

- Replaced the obsolete placeholder-specific memory candidate with neutral repository policy wording that points future workers to tracked root/harness policy plus the local-only runner overlay if present.

## Acceptance Criteria

- `memory-candidates.md` no longer contains `prior local-overlay policy file`.
- The candidate still preserves the important operational lesson: direct commit/push is allowed only when the active instruction allows it after validation and durable ledger evidence.
- No historical decisions or run-log evidence are deleted.

## Rollback

Restore the previous `memory-candidates.md` bullet from git history and remove this finding if a future task intentionally reintroduces that placeholder as an active policy reference.
