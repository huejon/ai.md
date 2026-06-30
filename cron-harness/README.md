# Long-Horizon Repository Renewal Harness

Purpose: continue a durable, evidence-backed renewal loop that keeps this Hermes/OpenCode operations repository minimal, high-signal, and useful for recurring long tasks.

This harness replaces one-off daily cron churn. Each run must learn from current repository evidence, improve one meaningful part of the operating system, and leave a durable handoff for the next run.

## Run Contract

Each run must:

1. Read `AGENTS.md`, `README.md`, `knowledge/INDEX.md`, and this file.
2. Run `git log --oneline -10` and `date`.
3. Inspect relevant tree areas before editing.
4. Load or create the active durable work ledger, normally `.opencode/works/repo-renewal-long/`.
5. Select exactly one primary loop state from the list below.
6. Select one narrow renewal objective with explicit evidence and acceptance criteria.
7. Make meaningful, reversible local changes covered by the safe auto-apply policy and the active user instruction.
8. Run the evaluation checklist.
9. Update the durable ledger, especially `run-log.md`, `decisions.md`, `memory-candidates.md`, and `handoff.md`.
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
- add reports or work ledgers under `.opencode/works/`;
- update `knowledge/INDEX.md` when research files are changed;
- remove old/noisy artifacts only when the active user task explicitly authorizes cleanup and the ledger records evidence, risk, and reversal path first.

Not allowed without explicit approval or an active task that explicitly grants cleanup authority:
- deleting files or directories;
- pushing, committing, publishing, deploying, or opening PRs;
- changing secrets, credentials, billing, production systems, or external services;
- broad rewrites that make rollback hard;
- editing `LICENSE` or removing license notices.

When unsure, do not delete or rewrite. Add the candidate to `cleanup-plan.md` or `.opencode/works/repo-renewal-long/proposals/` with evidence and a recommended owner decision.

## Artifact Locations

- Durable renewal ledger: `.opencode/works/repo-renewal-long/`.
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

## Completion Criteria

A run is complete only when it reports:
- files changed, files created, and files removed;
- verification commands, working directory, exit codes, and relevant output;
- what the evidence proves;
- remaining risks or unverified items;
- the next action recorded in the durable handoff.
