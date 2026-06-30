# Initial Renewal Findings — 2026-06-30

## Finding 1: `/daily-cron` used the wrong agent for the renewed operating model

Evidence:
- `.opencode/command/daily-cron.md` declared `agent: prompt-architect`.
- The active task explicitly requires using the `work` agent and repo command flows.
- The loaded OpenCode customization guidance confirms command frontmatter supports an `agent` field and command bodies are the prompt template.

Decision:
- Change `/daily-cron` to `agent: work` and direct it to continue `.opencode/works/repo-renewal-long/`.

## Finding 2: The old daily harness optimized for one-off small cron runs

Evidence:
- `cron-harness/README.md` described a "small, safe" daily loop and required uncertain cleanup to remain in `cleanup-plan.md`.
- The active task requires long-duration renewal, evidence-backed learning, durable handoff, and authorized cleanup of old/noisy artifacts.

Decision:
- Replace the daily-only framing with a long-horizon repository renewal harness while preserving safety boundaries.

## Finding 3: Root `j-qa.md` and `j-rev.md` are obsolete noisy duplicates

Evidence:
- Root `j-qa.md` and `j-rev.md` contain older short agent drafts.
- Tracked deployable agent files exist at `.claude/agents/j-qa.md`, `.claude/agents/j-rev.md`, `.opencode/agents/j-qa.md`, and `.opencode/agents/j-rev.md`.
- Richer source artifacts exist under `agents/j-qa/` and `agents/j-rev/` with architecture specs, system prompts, test scenarios, and evaluations.
- `cron-harness/cleanup-plan.md` had already flagged these root files as duplicate candidates.

Decision:
- Remove the root duplicates. Reversal path: restore with `git checkout -- j-qa.md j-rev.md` before commit, or from repository history later.

## Finding 4: Old work ledgers are superseded by the durable renewal ledger

Evidence:
- `.opencode/works/cron-harness-reorg/` is a previous reorganization ledger, not the current continuation point.
- `.opencode/works/daily-cron/2026-06-30.md` is a one-off daily report, while the active task explicitly requires `.opencode/works/repo-renewal-long/` durable continuity.
- The active user instruction says not to preserve historical work just because it exists.

Decision:
- Remove the superseded historical work files and keep the current evidence in `.opencode/works/repo-renewal-long/`.
- Reversal path: restore removed historical files from this working tree before commit or from git history if they were later committed.

## Finding 5: Empty memory stubs add noise without durable facts

Evidence:
- `.opencode/memory/project.md`, `.opencode/memory/gotchas.md`, and `.opencode/memory/verification.md` only contained placeholder headings and generic instructions.
- The active task asks for a minimal, high-signal operations repo and forbids storing secrets in memory or logs.

Decision:
- Remove empty memory stubs now. Recreate memory files only when there are verified stable facts worth preserving.
