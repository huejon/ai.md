# Long-Horizon Repository Renewal Harness

Purpose: continue a durable, evidence-backed renewal loop that keeps this agent-runtime operations repository minimal, high-signal, and useful for recurring long tasks, especially curated knowledge maintenance.

This harness replaces one-off daily cron churn. Each run must learn from current repository evidence, improve one meaningful part of the operating system, and leave a durable handoff for the next run.

## Run Contract

Each run must:

1. Read `AGENTS.md`, `README.md`, `knowledge/INDEX.md`, `knowledge/research/good-ai-assisted-research-methodology.md`, and this file.
2. Run `git log --oneline -10` and `date`.
3. Inspect relevant tree areas before editing.
4. Load or create the active local work ledger, normally `.opencode/works/repo-renewal-long/`, unless the invoking command or user explicitly names a different active ledger path.
5. Select exactly one primary loop state from the list below.
6. Select one narrow renewal objective with explicit evidence and acceptance criteria.
7. Make meaningful, reversible local changes covered by the safe auto-apply policy and the active user instruction.
8. Run the evaluation checklist.
9. Update the local ledger, especially `run-log.md`, `decisions.md`, `memory-candidates.md`, and `handoff.md`.
10. Report changed, created, and removed files with verification evidence.

## Loop States

- `discover`: identify noisy, stale, duplicated, missing, or weak operational artifacts.
- `learn`: extract evidence-backed lessons from prior runs, diffs, failures, or reviews.
- `plan`: define a narrow renewal improvement and acceptance criteria.
- `apply`: make safe local edits, including authorized cleanup when evidence supports it.
- `evaluate`: run checklist-based review and command evidence.
- `report`: summarize changed, created, and removed files, evidence, risks, and next actions.
- `blocked`: stop because a decision, credential, live external dependency, or external side-effect approval is required.

## Safe Auto-Apply Policy

Allowed without extra approval:
- add or refine docs, checklists, prompts, command files, skills, agent specs, and templates;
- correct broken links, stale wording, and duplicate low-value wording;
- add reports or work ledgers under local `.opencode/works/`;
- update `knowledge/INDEX.md` when research files are changed;
- remove old/noisy artifacts only when the active user task explicitly authorizes cleanup and the ledger records evidence, risk, and reversal path first.

Not allowed without explicit approval or an active task that explicitly grants cleanup authority:
- deleting files or directories;
- pushing, committing, publishing, deploying, or opening PRs;
- changing secrets, credentials, billing, production systems, or external services;
- broad rewrites that make rollback hard;
- editing `LICENSE` or removing license notices.

Commit/push precedence guard:
- The active user or command instruction for the current run overrides the repository's routine direct-commit policy.
- If the active instruction forbids commit or push, do not commit or push even when repository policy would normally allow it.
- If the active instruction explicitly requests commit/push after validation, perform it only after the evaluation checklist passes and the local ledger records the validation evidence.
- Opening PRs remains disallowed unless the active instruction explicitly requests it.

When unsure, do not delete or rewrite. Add the candidate to `cleanup-plan.md` or the active work ledger's `proposals/` directory with evidence and a recommended owner decision.

## Artifact Locations

- Renewal ledger: local `.opencode/works/repo-renewal-long/` by default. Do not create or revive root `work-ledgers/` unless the user explicitly asks for a tracked neutral ledger.
- Daily or task reports: `.opencode/works/<work-name>/handoff.md` plus dated findings when useful.
- Run logs: `.opencode/works/<work-name>/run-log.md`.
- Findings: `.opencode/works/<work-name>/findings/`.
- Reviews: `.opencode/works/<work-name>/reviews/`.
- Proposals: `.opencode/works/<work-name>/proposals/`.
- Cleanup candidates: `cron-harness/cleanup-plan.md`.
- Prompt and loop checklists: this directory.

## Learning Contract

Each non-blocked run should record at least one of:

- a finding backed by file or command evidence;
- a decision with rationale and rollback path;
- a memory candidate for future repository operation;
- a cleanup proposal for uncertain work;
- a concrete improvement to commands, skills, harnesses, or docs.

Do not preserve historical work solely because it exists. Preserve artifacts because they are canonical, referenced, current, or useful for future operation.

## Cron Responsibility Split

This section defines recurring responsibilities and boundaries. It does not by itself install a scheduler, daemon, or external automation.

- **ai.md knowledge-curation cron**: operates in this repository. It refreshes research notes, classifies freshness/value, maintains `knowledge/INDEX.md`, updates harness/checklists, and records evidence in `.opencode/works/`. It may propose distilled OpenCode guidance but should not bulk-copy active config artifacts into this repo.
- **config-opencode application cron**: operates in `~/.config/opencode`. It reads curated `ai.md` knowledge, applies only minimal operational changes to active OpenCode agents/commands/skills/references/prompts, validates the config repo, and records its own local ledger.

When a run touches research methodology, use the current methodology note as the default quality gate and record source hierarchy, search protocol, AI-audit checks, and review/judge evidence.

## Completion Criteria

A run is complete only when it reports:
- files changed, files created, and files removed;
- verification commands, working directory, exit codes, and relevant output;
- what the evidence proves;
- remaining risks or unverified items;
- the next action recorded in the durable handoff.
