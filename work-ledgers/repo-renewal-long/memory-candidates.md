# Memory Candidates

- For renewal runs, the active user/command instruction has commit/push precedence over the repository's routine direct-commit policy: if it forbids commit/push, do not commit/push; if it explicitly requests commit/push after validation, do so only after checklist validation and ledger evidence.
- For `repo-renewal-long`, `work-ledgers/repo-renewal-long/` is the default durable repository ledger. An explicit user/command path controls a specific run, but if that path is ignored/local-only, mirror durable evidence back into `work-ledgers/repo-renewal-long/` before reporting.
- Keep `work-ledgers/repo-renewal-long/work.md` as the reusable active scope contract for future continuations; completed cleanup details belong in historical ledger entries and findings, not the active task scope.
- Repository-local automation policy is governed by root `AGENTS.md`, `README.md`, `cron-harness/README.md`, and the local-only runner overlay if present; routine maintenance may commit and push directly to `main` only when the active instruction allows it after validation and durable ledger evidence.
- Root `CLAUDE.md` was intentionally removed on 2026-06-30 as part of deeper cleanup; do not recreate it unless explicitly requested.
- `work-ledgers/` should stay limited to project policy/readme/config/command files and durable active work ledgers unless a future task explicitly authorizes more. Legacy local prompt-copy directories and vendored dependency artifacts should not be reintroduced without evidence.
