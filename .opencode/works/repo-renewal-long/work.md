# repo-renewal-long

## Objective

Maintain a durable, evidence-backed renewal loop that keeps this Hermes/OpenCode operations repository minimal, high-signal, and aligned with current OpenCode operating policy.

## Current Task Scope

- Remove root `CLAUDE.md` entirely as explicitly requested.
- Add `.opencode/AGENTS.md` with concise OpenCode-specific policy: no human review gate; OpenCode/Hermes may commit and push directly to `main` after validation.
- Preserve `LICENSE`.
- Avoid secrets.
- Validate with `git diff --check`, `git diff -- LICENSE`, and `git status`.
- Do not commit or push inside OpenCode; Hermes will perform final commit/push after verification.

## Out of Scope

- Deploying, publishing packages, mutating production, billing changes, or external messaging.
- Editing `LICENSE`.
- Committing or pushing during this run.
