# Context

Repository role: Hermes/OpenCode prompt-operations workspace for recurring agent setup, prompt, skill, command, harness, knowledge, and loop-engineering work.

Startup evidence gathered:
- Read `AGENTS.md`, `README.md`, and `knowledge/INDEX.md`.
- Read current daily command at `.opencode/command/daily-cron.md`.
- Read `CLAUDE.md`, `.opencode/README.md`, and `.opencode/opencode.jsonc` for the continuation objective.
- Read current cron harness files under `cron-harness/`.
- Ran `git log --oneline -10` and `date`.
- Inspected root and relevant `.opencode/` and `cron-harness/` trees.

Relevant observed facts:
- `.opencode/command/daily-cron.md` now declares `agent: work` in the local renewal diff.
- `cron-harness/README.md` now describes a long-horizon renewal loop and safe cleanup boundaries.
- User explicitly authorized removal of old/noisy artifacts for this long renewal task.
- `.opencode/works/cron-harness-reorg/` and `.opencode/works/daily-cron/` are historical work artifacts, not canonical operating docs.
- `CLAUDE.md` was still focused on the older prompt-engineering quick-start and did not mention long-horizon renewal.
- `.opencode/README.md` and `.opencode/opencode.jsonc` are untracked but describe reusable repository overlay behavior and contain no secrets.
