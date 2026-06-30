# CLAUDE and OpenCode Overlay Alignment

## Finding 1: `CLAUDE.md` lagged behind the renewed operating model

Evidence:
- `AGENTS.md`, `README.md`, and `cron-harness/README.md` now describe long-horizon repository renewal.
- `.opencode/command/daily-cron.md` routes the compatibility command to the `work` agent and the durable ledger.
- `CLAUDE.md` only described the older prompt-engineering quick start and did not mention the renewal ledger.

Decision:
- Add concise operating-model and long-horizon renewal guidance to `CLAUDE.md` while keeping `AGENTS.md` as the complete instruction source.

Rollback:
- Revert the `CLAUDE.md` additions if Claude-facing guidance should remain only a pointer to `AGENTS.md`.

## Finding 2: `.opencode/README.md` and `.opencode/opencode.jsonc` are canonical overlay candidates

Evidence:
- `.opencode/agents/` files are already tracked canonical OpenCode deployment prompts.
- `.opencode/command/daily-cron.md` is now the repository command entrypoint for renewal.
- `.opencode/opencode.jsonc` contains only the schema URL and `"share": "disabled"`, a safe project default with no secrets.
- `.opencode/README.md` documents repository overlay usage and can prevent future confusion between canonical overlay files and local/task-scoped artifacts.

Decision:
- Treat `.opencode/README.md` and `.opencode/opencode.jsonc` as canonical overlay files worth tracking in the eventual change set.

Rollback:
- Keep them untracked or remove them from a future staged set if the repository owner decides OpenCode overlay policy should remain local-only.
