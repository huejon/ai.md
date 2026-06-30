# OpenCode Policy for This Repository

This repository is an AI-operated Hermes/OpenCode prompt-operations workspace.

## Operating Rules

- OpenCode may edit, validate, commit, and push directly to `main` after local validation.
- There is no human review gate for routine repository maintenance in this workspace.
- Hermes remains the orchestrator; OpenCode performs local engineering, validation, and evidence reporting.
- Preserve `LICENSE` and never store secrets in prompts, ledgers, logs, or reports.
- Do not deploy, publish packages, mutate production systems, perform billing changes, or send external messages unless explicitly requested.

## Validation Before Commit/Push

Before committing or pushing, run the task-relevant checks and record concise evidence: command, directory, exit code, and relevant output.

## Handoff

For non-trivial work, maintain `.opencode/works/<work-name>/handoff.md` instead of relying on conversation compaction.
