# repo-renewal-long

## Objective

Continue the durable agent-runtime repository renewal loop and keep this operations repository minimal, high-signal, and aligned with current local runner operating policy.

## Active Scope Contract

- Start each continuation from `cron-harness/README.md`, the current `handoff.md`, `state.md`, and `run-log.md`.
- Choose exactly one narrow renewal objective per run unless the active user instruction explicitly requests more.
- Prefer `discover`, `learn`, `plan`, `apply`, `evaluate`, or `report` loop states; use `blocked` only with evidence of a real blocker or required decision.
- Keep edits small, reversible, and within the safe auto-apply policy: docs, checklists, prompts, command files, skills, agent specs, templates, knowledge index updates, and ledger records.
- Record evidence in `run-log.md`; record durable rationale in `decisions.md` or `findings/`; record resume instructions in `handoff.md`.
- Preserve `LICENSE`, avoid secrets, and do not delete files unless the active task explicitly authorizes cleanup and the ledger records evidence, risk, and rollback first.
- Commit or push only when the active user/command instruction for the current run explicitly allows it after validation.

## Out of Scope

- Deploying, publishing packages, mutating production, billing changes, or external messaging.
- Editing `LICENSE`.
- Broad rewrites, speculative cleanup, or reintroducing legacy local prompt-copy/deployment directories without explicit evidence-backed authorization.
