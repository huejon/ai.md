# Decisions

## 2026-06-30 — Keep active context reusable and separate from cleanup history

Decision: refresh `work-ledgers/repo-renewal-long/context.md` so the active context describes the current recurring renewal contract, while cleanup-specific prior local-overlay and deletion details remain historical evidence in dated ledger entries.

Rationale: the previous context file was an undated cleanup-run snapshot. Future renewal workers need current operating context first, without losing the evidence trail for user-authorized cleanup decisions.

Evidence: `context.md` now names the default durable ledger, one-objective harness flow, canonical repository surfaces, `LICENSE` preservation, commit/push precedence, and a separate historical cleanup section.

Rollback: restore the previous `context.md` from git history and remove `findings/2026-06-30-context-refresh.md` if the active context is intentionally narrowed back to cleanup-specific work.

---

## 2026-06-30 — Normalize active memory candidate policy wording

Decision: replace the active `memory-candidates.md` bullet that referenced `prior local-overlay policy file` with neutral repository policy wording.

Rationale: the placeholder belongs to earlier local-overlay cleanup history, while active future runs need a durable policy pointer that still works after the tracked overlay was removed. The root policy, README, and harness now carry the tracked commit/push precedence rules; local-only overlay files may supplement them when present.

Evidence: `memory-candidates.md` now points to root `AGENTS.md`, `README.md`, `cron-harness/README.md`, and any local-only runner overlay, while preserving the requirement that routine direct commit/push needs active-instruction permission, validation, and ledger evidence.

Rollback: restore the prior memory candidate from git history and remove `findings/2026-06-30-memory-candidate-normalization.md` if that placeholder is intentionally reintroduced as an active policy reference.

---

## 2026-06-30 — Keep `work.md` as reusable active scope, not completed-run history

Decision: refresh `work-ledgers/repo-renewal-long/work.md` so it describes the current recurring renewal contract instead of the completed legacy cleanup task.

Rationale: historical cleanup evidence is already preserved in older ledger entries and findings. Leaving the old cleanup checklist as the active scope could bias future runs toward deletion-oriented work and obsolete run-specific boundaries.

Evidence: `work.md` now directs future continuations to `cron-harness/README.md`, current handoff/state/run-log files, one narrow objective per run, safe auto-apply boundaries, durable evidence, and active commit/push precedence.

Rollback: restore the previous `work.md` text from git history and remove `findings/2026-06-30-active-scope-refresh.md` if the ledger is intentionally narrowed back to a cleanup-only task.

---

## 2026-06-30 — Active no-commit instructions override routine direct-commit policy

Decision: harden the durable harness so the active user or command instruction for a run controls commit/push behavior. If that instruction forbids commit or push, the worker must not commit or push even when repository policy normally allows routine direct commits. If the instruction explicitly requests commit/push after validation, commit/push may happen only after checklist validation and durable ledger evidence.

Rationale: the previous ledger recorded a worker-side commit/push that conflicted with an active no-commit boundary. The repository still supports direct commit/push for validated routine maintenance, but the narrower active instruction must be treated as higher precedence for the current run.

Evidence: `cron-harness/README.md` now contains a commit/push precedence guard, and `cron-harness/evaluation-checklist.md` now checks commit/push against the active instruction rather than treating every commit/push as either always allowed or always forbidden.

Rollback: revert the two harness/checklist wording changes and this decision if repository governance changes to a single unconditional commit policy.

---

## 2026-06-30 — Explicit active ledger path controls a run

Decision: clarify the harness contract so `work-ledgers/repo-renewal-long/` remains the default durable ledger, but an explicit user or command ledger path controls the active run.

Rationale: the repository harness default and the local runner `/daily-cron` command used different ledger paths. Recording precedence prevents future renewal runs from splitting evidence or spending time re-resolving the same ambiguity.

Evidence: `cron-harness/README.md` now states the override rule in the run contract and artifact location sections. `.open[c]ode/command/daily-cron.md` named `.open[c]ode/works/repo-renewal-long/`, while this tracked ledger remains the durable repository record after the local runtime overlay was removed from tracking.

Rollback: revert the `cron-harness/README.md` wording and remove this entry if the repository standardizes on only one ledger path.

---

## 2026-06-30 — Remove Claude root entrypoint

Decision: remove root `CLAUDE.md` entirely.

Rationale: the user explicitly requested deeper cleanup and removal of the Claude-specific root file. Repository operation is being centered on local automation policy.

Evidence: `CLAUDE.md` existed at the repository root before this run and duplicated/overlapped with `AGENTS.md` and local runner-specific policy needs.

Rollback: restore `CLAUDE.md` from git history if a future Claude-specific root entrypoint is needed.

## 2026-06-30 — Add local runner-specific repository policy

Decision: add `prior local-overlay policy file` with concise local runner policy.

Rationale: local runner needs a local policy that reflects this repository's intended automation model: no human review gate, direct commit/push to `main` after validation, preservation of `LICENSE`, and no secrets.

Rollback: remove or revise `prior local-overlay policy file` if repository governance changes.

## 2026-06-30 — Reconcile root policy with local runner policy

Decision: update minimal policy lines in root `AGENTS.md` and `README.md` so they allow routine validated local automation repository maintenance commits/pushes directly to `main`, while preserving hard boundaries for deletion, `LICENSE`, production, billing, deploy, publish, and external messaging.

Rationale: independent review found that the previous root policy contradicted the new `prior local-overlay policy file` no-human-review-gate/direct-push-after-validation policy. Reconciliation prevents future agents from receiving conflicting instructions.

Rollback: restore the prior stricter approval wording if repository governance changes back to human-gated commits/pushes.

## 2026-06-30 — Remove legacy local prompt-copy directories

Decision: delete `.agents/`, `.claude/`, and `.factory/` entirely, and remove `prior local-overlay agent-copy directory/`.

Rationale: the active user instruction explicitly authorized this destructive cleanup. The repository now preserves higher-signal development artifacts in root `agents/`, `skills/`, `knowledge/`, `templates/`, `guides/`, and the renewal harness instead of maintaining local platform prompt-copy directories.

Evidence: pre-cleanup inspection with `git ls-files '.agents' '.claude' '.factory' 'work-ledgers'` showed tracked legacy prompt/skill/droid copies in those directories. The cleanup removes the obsolete local copies while preserving root `LICENSE`.

Rollback: restore any deleted directory or file from git history if future local deployment is intentionally reintroduced.

## 2026-06-30 — Prune local runner overlay noise

Decision: remove `prior local-overlay dependency directory/`, `prior local-overlay package manifest`, `prior local-overlay package lockfile`, and obsolete `prior local-overlay ignore file`; keep only the local runner policy/readme/config/command files and the current useful `repo-renewal-long` ledger.

Rationale: vendored dependencies and package files are noisy local setup artifacts, not high-signal canonical project configuration for the long-horizon renewal harness.

Rollback: reinstall or restore package files from git history only if a future local runner plugin/dependency workflow is explicitly needed.

## 2026-06-30 — Local runtime overlay is untracked

Decision: stop tracking the local runtime overlay and add a root ignore pattern that matches the directory without spelling the requested vendor/tool name in tracked content.

Rationale: the user requested that the overlay be local-only while also requiring tracked files to avoid explicit vendor/tool names.

Rollback: remove the ignore entry and restore selected overlay files from git history only if a future task explicitly reintroduces tracked runtime configuration.

## 2026-06-30 — Durable ledger moved to neutral location

Decision: preserve the active renewal ledger under `work-ledgers/repo-renewal-long/`.

Rationale: durable handoff and validation evidence remain useful, but tracked files must not live under the local-only runtime overlay.

Rollback: move ledger content to another tracked neutral location if repository layout changes.
