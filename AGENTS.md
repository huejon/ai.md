# AGENTS.md — Research Notes

Universal rules for agents operating in this repository.

## Purpose

This repository is an owned research and prompt-engineering operations workspace. It keeps renewal harnesses, checklists, and curated research context. It does not assume or contain any specific downstream runtime configuration repository. Outputs are cognitive configuration and operational documentation, not application code.

## Operating Model

- **coordinating process orchestrates.** coordinating process selects priorities, starts daily loops, and coordinates agents.
- **local runner engineers.** local runner performs local edits, file organization, harness work, verification, and evidence reporting.
- **Repository artifacts guide specialist work.** Use the renewal harness, cleanup notes, and knowledge base here; downstream runtime consumers should apply only distilled operational rules. Do not bulk-copy knowledge files into downstream configuration.
- **Artifacts are English.** Prompts, specs, skills, ledgers, reports, and docs are written in English.
- **Conversation is Portuguese.** User-facing clarification and status are in Portuguese unless asked otherwise.

## Mandatory Startup Protocol

Every task starts by:

1. Reading relevant files with `Glob`/`Read`/`Grep`.
2. Reading `AGENTS.md`, `README.md`, and `knowledge/INDEX.md` when repository policy or daily work may be affected.
3. Running `git log --oneline -10`.
4. Running `date`.
5. Inspecting the relevant tree before editing.

Do not skip this, even for simple tasks.

## Long-Horizon Renewal Harness

Recurring automated improvement work must start at `cron-harness/README.md` or the local runner command `/daily-cron`.

The `/daily-cron` command name is retained for compatibility, but its job is long-horizon repository renewal. It should normally continue the local `.opencode/works/repo-renewal-long/` ledger and use the `work` agent flow.

Recurring responsibility is split:

- The **research-notes knowledge-curation cron** maintains curated research, `knowledge/INDEX.md`, and harness guidance in this repository.
- **Downstream application automation** may run separately under operator control to read this repository's curated findings and update only distilled runtime guidance outside this repository.

Harness gates:

1. Establish scope and loop state.
2. Read current policy, knowledge index, `knowledge/research/good-ai-assisted-research-methodology.md`, and relevant artifacts.
3. Prefer safe, small, reversible edits.
4. Apply only changes allowed by the safe auto-apply policy.
5. Run the evaluation checklist before claiming completion.
6. Update the local work ledger, especially run log, decisions, findings, memory candidates, and handoff.
7. Put uncertain cleanup in `cron-harness/cleanup-plan.md` or the active ledger; delete only when explicitly authorized and evidence-backed.

## Autonomy and Boundaries

Act directly when work is clear, local, and reversible.

Stop or ask only when:
- action is destructive or irreversible,
- intent is genuinely ambiguous after inspection,
- a production, billing, deploy, publish, push, or external-message side effect is requested,
- credentials or secrets would be exposed.

local automation may commit and push routine validated repository maintenance directly to `main` as governed by repository policy; active task instructions may still forbid commit/push for a run. Never deploy, publish, mutate production, send external messages, perform billing changes, or delete `LICENSE` without explicit user approval.

## D.A.R.T.E. Workflow

Use D.A.R.T.E. for new or materially changed prompts and skills. Runtime artifacts intended for downstream systems should be authored in the operator-designated downstream workspace unless the task explicitly targets this repo's harness or research:

1. **Discovery** — Collect requirements and constraints.
2. **Architecture** — Define identity, reasoning, tools, context, safety, and success criteria.
3. **Redaction** — Write the prompt or `SKILL.md`.
4. **Test** — Cover happy path, edge, adversarial, and failure-mode scenarios.
5. **Enhance** — Score, simplify, and improve before approval.

## Delegation Policy

Non-trivial work should be delegated when the agent surface supports it.

| Task | Delegate To |
|---|---|
| New agent/skill from scratch | `prompt-architect-planner` first |
| Write system prompt or `SKILL.md` from spec | `prompt-architect-builder` |
| Full review/test/evaluation | `prompt-architect-reviewer` |
| Complex redesign | `prompt-architect-planner` |

The orchestrator may do quick edits, workspace maintenance, structure questions, and knowledge lookups directly.

## Quality Bar

Every production prompt, skill, command, or harness must include:
- clear scope and success criteria,
- explicit output/report format,
- uncertainty handling,
- safety and injection guardrails,
- evaluation or test coverage,
- rollback or cleanup notes when relevant.

## Knowledge Base Rules

Location:

```text
knowledge/
  INDEX.md
  research/*.md
```

Freshness:
- **Current**: < 3 months.
- **Aging**: 3-6 months; verify key claims.
- **Stale**: > 6 months; re-research before relying on findings.

Read `knowledge/INDEX.md` before research. If research is created or updated, update the index.

## Workspace Structure

```text
cron-harness/              # Long-horizon renewal loop contract and checklists
.opencode/works/           # Local-only local runner work ledgers and handoffs
knowledge/                 # Shared research base
```

Rules:
- Preserve valuable knowledge and harness artifacts. Downstream runtime agents, skills, prompts, templates, and references are external consumers, not contents of this repository.
- Keep local runner project configuration minimal, high-signal, and local-only. Work ledgers belong under `.opencode/works/<work-name>/`; do not create root `work-ledgers/`.
- Legacy local prompt-copy directories are intentionally absent; do not reintroduce root `agents/`, `skills/`, `templates/`, `prompts/`, or `guides/` here.
- Keep generated outputs small, high-signal, and reversible.

## Inviolable Rules

1. coordinating process orchestrates; local runner and repo agents perform engineering.
2. Follow D.A.R.T.E. for new or materially changed prompts and skills.
3. Use cron harness gates for recurring repository renewal work.
4. Never skip safety guardrails or evaluation evidence.
5. local automation may commit and push routine validated repository maintenance directly to `main` under repository policy; never delete without explicit approval and never delete `LICENSE`.
6. Never delete `LICENSE`.
7. Keep artifacts in English and user conversation in Portuguese.
8. Prefer documented cleanup plans over risky deletion.
9. Do not reintroduce legacy local deployable prompt-copy directories unless a future task explicitly re-establishes them with evidence.
10. Do not store secrets in prompts, logs, reports, or memory.
