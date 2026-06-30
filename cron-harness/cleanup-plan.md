# Cleanup Plan

Purpose: record uncertain cleanup candidates for later review. During `repo-renewal-long`, deletion is allowed only when the active task explicitly authorizes cleanup and evidence is recorded in the durable ledger first.

## Current First-Pass Notes

- 2026-06-30: User explicitly authorized removing legacy local deployment/copy directories and local runner dependency noise. The active ledger records deletion of the old local prompt-copy directories and pruning of local runner package/dependency artifacts.
- 2026-06-30: User explicitly authorized cleanup of root `agents/`, `skills/`, `templates/`, `prompts/`, and `guides/` after useful review/QA/traceability patterns were distilled into `~/.config/opencode/references/delivery-gates.md`. Preserve `knowledge/` unless separately reviewed.

## Candidate Format

| Candidate | Evidence | Risk | Recommended Action | Decision |
|---|---|---|---|---|
|  |  |  |  |  |
