# Context

Repository role: Hermes/OpenCode prompt-operations workspace for recurring agent setup, prompt, skill, command, harness, knowledge, and loop-engineering work.

Startup evidence gathered in this cleanup continuation:
- Loaded `/var/home/core/.config/opencode/references/work-command.md` with the requested Python command.
- Read `AGENTS.md`, `README.md`, `knowledge/INDEX.md`, `cron-harness/README.md`, `.opencode/README.md`, `.opencode/opencode.jsonc`, `.opencode/command/daily-cron.md`, and active `repo-renewal-long` ledger files.
- Ran `git log --oneline -10`, `date`, `git status --short`, and `git ls-files` inspections.
- Inspected references to legacy local directories before deleting them.

Relevant observed facts:
- The active user instruction explicitly authorized destructive cleanup of `.agents/`, `.claude/`, `.factory/`, and noisy `.opencode/` artifacts.
- The retained OpenCode project overlay is minimal: policy, README, config, command, and this durable ledger.
- Root `LICENSE` is preserved and must remain untouched.
- OpenCode must not commit or push in this run; Hermes will do final commit/push after validation.
