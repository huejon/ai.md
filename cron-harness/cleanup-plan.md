# Cleanup Plan

Purpose: record uncertain cleanup candidates for later review. During `repo-renewal-long`, deletion is allowed only when the active task explicitly authorizes cleanup and evidence is recorded in the durable ledger first.

## Current First-Pass Notes

- `.opencode/node_modules/`, `.opencode/package.json`, and `.opencode/package-lock.json` appear to be local OpenCode plugin dependencies and are ignored by `.opencode/.gitignore`; leave untouched unless dependency management is explicitly in scope.
- `j-qa.md` and `j-rev.md` duplicate deployed-looking agent material at the repository root. Initial renewal evidence found richer canonical/deployed versions under `.claude/agents/`, `.opencode/agents/`, and `agents/j-*`; removal is appropriate when recorded in `.opencode/works/repo-renewal-long/decisions.md`.
- `skills/` and `.agents/skills/` both contain skill material. Preserve until canonical/deployment responsibilities are confirmed.
- `guides/`, `templates/`, and `knowledge/` contain potentially valuable operational context; preserve.

## Candidate Format

| Candidate | Evidence | Risk | Recommended Action | Decision |
|---|---|---|---|---|
|  |  |  |  |  |
