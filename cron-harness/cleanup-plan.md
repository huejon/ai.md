# Cleanup Plan

Purpose: record uncertain cleanup candidates for later review. During `repo-renewal-long`, deletion is allowed only when the active task explicitly authorizes cleanup and evidence is recorded in the durable ledger first.

## Current First-Pass Notes

- 2026-06-30: User explicitly authorized removing legacy local deployment/copy directories and OpenCode dependency noise. The active ledger records deletion of the old local prompt-copy directories and pruning of OpenCode package/dependency artifacts.
- Root `j-qa.md` and `j-rev.md` were already marked for removal in earlier renewal work; keep richer canonical artifacts under `agents/j-qa/` and `agents/j-rev/`.
- `skills/` contains potentially valuable operational context; preserve unless a future task explicitly authorizes more cleanup with evidence.
- `guides/`, `templates/`, and `knowledge/` contain potentially valuable operational context; preserve.

## Candidate Format

| Candidate | Evidence | Risk | Recommended Action | Decision |
|---|---|---|---|---|
|  |  |  |  |  |
