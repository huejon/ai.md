# Evaluation Checklist

Use before reporting completion for long-horizon repository renewal work.

## Repository Safety

- [ ] No push, commit, deploy, publish, external message, or production mutation occurred.
- [ ] No secrets were written to docs, prompts, logs, or reports.
- [ ] `LICENSE` was not edited or removed.
- [ ] Destructive cleanup was avoided unless explicitly authorized by the active task and recorded with evidence.

## Scope Control

- [ ] The run has one clear primary renewal objective.
- [ ] Changes are small, reversible, and high-signal.
- [ ] Uncertain cleanup is recorded in `cleanup-plan.md` or the active work ledger instead of deleted.
- [ ] The durable ledger has current state, run-log, decisions or findings, and handoff updates.

## Prompt/Skill/Harness Quality

- [ ] Scope and success criteria are explicit.
- [ ] Output or report format is explicit.
- [ ] Safety and injection guardrails are present where relevant.
- [ ] Uncertainty handling is documented.
- [ ] Tests, scenarios, or checklist validation exist for production artifacts.

## Evidence

- [ ] Startup protocol was completed.
- [ ] Relevant diffs were inspected.
- [ ] Verification commands include directory, exit code, relevant output, and meaning.
- [ ] Remaining risks are stated.
- [ ] Next action is recorded in the durable handoff.
