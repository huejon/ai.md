# repo-renewal-long

## Objective

Continue the durable Hermes/OpenCode repository renewal loop and keep this operations repository minimal, high-signal, and aligned with current OpenCode operating policy.

## Current Task Scope

- Remove `.agents/`, `.claude/`, and `.factory/` entirely as explicitly requested.
- Clean `.opencode/` so it retains only high-signal project files needed for future long-horizon work: `AGENTS.md`, `README.md`, `opencode.jsonc`, `command/daily-cron.md`, and the current useful `works/repo-renewal-long/` ledger/handoff.
- Remove `.opencode/agents/`, `.opencode/node_modules/`, package files, obsolete `.opencode/.gitignore`, and stale/noisy prior ledger artifacts.
- Update root docs, OpenCode overlay docs, harness cleanup notes, and this ledger so active references no longer point to deleted local prompt-copy directories.
- Preserve `LICENSE` and avoid secrets.
- Validate with `git diff --check`, `git diff -- LICENSE`, and `git status`.
- Do not commit or push inside OpenCode; Hermes will perform final commit/push after validation.

## Out of Scope

- Deploying, publishing packages, mutating production, billing changes, or external messaging.
- Editing `LICENSE`.
- Committing or pushing during this run.
