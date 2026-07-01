# Knowledge Base — Index

> Research findings, validated techniques, and domain knowledge used by all agents in this workspace.
> Before researching a topic, check this index first. If recent research exists, use it instead of re-researching.

## Research Files

| File | Topic | Last Updated | Freshness | Value / Maintenance Notes |
|---|---|---:|---|---|
| [good-ai-assisted-research-methodology.md](research/good-ai-assisted-research-methodology.md) | Evidence-backed method for AI-assisted literature/scientific research and knowledge maintenance | 2026-07-01 | Current | Default methodology for new research runs; current repo path is `research-notes`, not old workspace names. |
| [context-engineering.md](research/context-engineering.md) | Context Engineering paradigm, attention budget, token economics | 2026-02-14 | Aging | Valuable; verify current vendor/blog claims before applying. |
| [claude-4-best-practices.md](research/claude-4-best-practices.md) | Claude 4.x prompting best practices, breaking changes from Claude 3.x | 2026-02-14 | Aging | Valuable but model/vendor-specific; re-check current docs before prompt policy changes. |
| [multi-agent-patterns.md](research/multi-agent-patterns.md) | Multi-agent architectures, orchestration patterns, context isolation | 2026-02-14 | Aging | Valuable principles; re-check framework docs and empirical claims before relying on numbers. |
| [attention-and-context-limits.md](research/attention-and-context-limits.md) | Context window performance degradation, lost-in-the-middle, practical limits | 2026-02-14 | Aging | Valuable; keep peer-reviewed lost-in-the-middle claims, re-check vendor context claims. |
| [skill-creation-architecture.md](research/skill-creation-architecture.md) | Agent Skills standard and skill creation architecture | 2026-07-01 | Current | Refreshed from current Agent Skills, Claude Code, OpenCode docs, and local OpenCode 1.17.12 evidence; old February runtime-copy path conventions are retired for this repository. |
| [platform-agent-mechanics.md](research/platform-agent-mechanics.md) | Claude Code and OpenCode agent/subagent mechanics, context windows, config scopes, and cross-platform compatibility | 2026-07-01 | Current | Refreshed from official Claude Code/OpenCode docs plus installed OpenCode 1.17.12 debug evidence; re-check after OpenCode upgrades or Claude Code Agent/Task changes. |
| [prd-template-driven-authoring.md](research/prd-template-driven-authoring.md) | Clarification-first, template-locked PRD authoring patterns from retired sample workflow | 2026-02-16 | Aging | Valuable pattern; source `samples/` paths are retired and should not be treated as live files. |
| [techspec-template-driven-authoring.md](research/techspec-template-driven-authoring.md) | Evidence-first, template-locked technical specification authoring patterns | 2026-02-16 | Aging | Valuable pattern; source `samples/` paths are retired and should not be treated as live files. |
| [task-execution-autonomy-guardrails.md](research/task-execution-autonomy-guardrails.md) | Task planning/execution modes, autonomy boundaries, and completion guardrails | 2026-02-16 | Aging | Valuable guardrails; source `samples/` paths are retired and should not be treated as live files. |
| [j-researcher-skill-research.md](research/j-researcher-skill-research.md) | Deep-research skill contract for `j-*` agents | 2026-02-17 | Aging | Historically useful; references legacy/other-repo `j-*` artifacts, so verify before applying. |
| [j-rev-and-j-qa-architecture.md](research/j-rev-and-j-qa-architecture.md) | j-rev/j-qa architecture, QA evidence model, accessibility and review gates | 2026-02-17 | Aging | Valuable for architecture ideas; references legacy local paths and needs source refresh. |

## Freshness Rules

- **Current**: Researched within the last 3 months. Use directly.
- **Aging**: Researched 3-6 months ago. Use but verify key claims against current docs.
- **Stale**: Researched 6+ months ago. Re-research before relying on findings.

## How to Use

1. **Before researching**: Check this index. If a relevant file exists and is Current or Aging, read it first; if only Stale files exist, use them only as leads and re-verify key claims.
2. **During research**: Follow [good-ai-assisted-research-methodology.md](research/good-ai-assisted-research-methodology.md): date gate, protocol-lite search plan, credible source hierarchy, evidence table, AI audit, and skeptical challenge.
3. **After researching**: Create a new file or update an existing one. Update this index with freshness and value/maintenance notes.
4. **File format**: Include Topic/Summary, Sources, Key Findings, Implications or Maintenance Rules, unknowns when relevant, and Last updated/Status metadata.
