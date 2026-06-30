# repo-renewal-long

## Objective

Continue the durable agent-runtime repository renewal loop and keep this operations repository minimal, high-signal, and aligned with current local runner operating policy.

## Current Task Scope

- Remove `.agents/`, `.claude/`, and `.factory/` entirely as explicitly requested.
- Clean `work-ledgers/` so it retains only high-signal project files needed for future long-horizon work: `AGENTS.md`, `README.md`, `local-runner.jsonc`, `command/daily-cron.md`, and the current useful `works/repo-renewal-long/` ledger/handoff.
- Remove `prior local-overlay agent-copy directory/`, `prior local-overlay dependency directory/`, package files, obsolete `prior local-overlay ignore file`, and stale/noisy prior ledger artifacts.
- Update root docs, local runner overlay docs, harness cleanup notes, and this ledger so active references no longer point to deleted local prompt-copy directories.
- Preserve `LICENSE` and avoid secrets.
- Validate with `git diff --check`, `git diff -- LICENSE`, and `git status`.
- Do not commit or push inside local runner; coordinating process will perform final commit/push after validation.

## Out of Scope

- Deploying, publishing packages, mutating production, billing changes, or external messaging.
- Editing `LICENSE`.
- Committing or pushing during this run.
