# Decisions

## 2026-06-30 — Remove Claude root entrypoint

Decision: remove root `CLAUDE.md` entirely.

Rationale: the user explicitly requested deeper cleanup and removal of the Claude-specific root file. Repository operation is being centered on OpenCode/Hermes policy.

Evidence: `CLAUDE.md` existed at the repository root before this run and duplicated/overlapped with `AGENTS.md` and OpenCode-specific policy needs.

Rollback: restore `CLAUDE.md` from git history if a future Claude-specific root entrypoint is needed.

## 2026-06-30 — Add OpenCode-specific repository policy

Decision: add `.opencode/AGENTS.md` with concise OpenCode policy.

Rationale: OpenCode needs a local policy that reflects this repository's intended automation model: no human review gate, direct commit/push to `main` after validation, preservation of `LICENSE`, and no secrets.

Rollback: remove or revise `.opencode/AGENTS.md` if repository governance changes.

## 2026-06-30 — Reconcile root policy with OpenCode policy

Decision: update minimal policy lines in root `AGENTS.md` and `README.md` so they allow routine validated OpenCode/Hermes repository maintenance commits/pushes directly to `main`, while preserving hard boundaries for deletion, `LICENSE`, production, billing, deploy, publish, and external messaging.

Rationale: independent review found that the previous root policy contradicted the new `.opencode/AGENTS.md` no-human-review-gate/direct-push-after-validation policy. Reconciliation prevents future agents from receiving conflicting instructions.

Rollback: restore the prior stricter approval wording if repository governance changes back to human-gated commits/pushes.

## 2026-06-30 — Remove legacy local prompt-copy directories

Decision: delete `.agents/`, `.claude/`, and `.factory/` entirely, and remove `.opencode/agents/`.

Rationale: the active user instruction explicitly authorized this destructive cleanup. The repository now preserves higher-signal development artifacts in root `agents/`, `skills/`, `knowledge/`, `templates/`, `guides/`, and the renewal harness instead of maintaining local platform prompt-copy directories.

Evidence: pre-cleanup inspection with `git ls-files '.agents' '.claude' '.factory' '.opencode'` showed tracked legacy prompt/skill/droid copies in those directories. The cleanup removes the obsolete local copies while preserving root `LICENSE`.

Rollback: restore any deleted directory or file from git history if future local deployment is intentionally reintroduced.

## 2026-06-30 — Prune OpenCode overlay noise

Decision: remove `.opencode/node_modules/`, `.opencode/package.json`, `.opencode/package-lock.json`, and obsolete `.opencode/.gitignore`; keep only the OpenCode policy/readme/config/command files and the current useful `repo-renewal-long` ledger.

Rationale: vendored dependencies and package files are noisy local setup artifacts, not high-signal canonical project configuration for the long-horizon renewal harness.

Rollback: reinstall or restore package files from git history only if a future OpenCode plugin/dependency workflow is explicitly needed.
