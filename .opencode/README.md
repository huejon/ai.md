# Project OpenCode Overlay

OpenCode auto-discovers this `.opencode/` directory.

This directory is the repository OpenCode overlay. Track project-level OpenCode files when they describe reusable repository behavior; keep machine-local experiments, secrets, and transient logs out.

Canonical overlay files in this repository:

- `AGENTS.md` — OpenCode-specific repository policy.
- `command/` — OpenCode command entrypoints, including `/daily-cron` for long-horizon renewal.
- `opencode.jsonc` — safe project defaults such as disabled sharing.
- `README.md` — this overlay contract.

Local or task-scoped artifacts:

- `works/<work-name>/` — durable local work ledgers; track only when the ledger is part of the intended repository evidence for a change.
- `memory/` — optional evidence-backed stable facts; omit empty placeholders.

Current retained ledger:

- `works/repo-renewal-long/` — current long-horizon renewal ledger and handoff.

Do not store vendored dependencies, package manager files, legacy prompt-copy directories, secrets, or transient logs here.

Do not store secrets here.
