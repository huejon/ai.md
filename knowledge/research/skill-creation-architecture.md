# Skill Creation Architecture

> Last updated: 2026-07-01
> Status: Current

## Summary

Agent Skills are compact, on-demand capability packages: a directory named for the skill, a required `SKILL.md` with YAML frontmatter plus Markdown, and optional `scripts/`, `references/`, and `assets/` resources. Use skills for repeatable task procedures or domain knowledge that should not live permanently in an agent prompt. Use commands for user-invoked workflow templates, agents for distinct reasoning roles or tool/autonomy boundaries, and references for passive knowledge that does not need invocation behavior.

The February 2026 implementation plan in the previous version of this note is retired for this repository. Its proposed `prompts/`, `.claude/`, local-runtime skill mirrors, and root runtime-copy conventions are obsolete here. Current repository policy keeps this workspace as compact research and renewal guidance, not active runtime configuration.

## Sources

| Source | Source class | Checked | Confidence | Notes |
|---|---|---:|---|---|
| Agent Skills specification, <https://agentskills.io/specification> | Open standard / primary spec | 2026-07-01 | High | Defines directory layout, `SKILL.md` frontmatter, naming constraints, and progressive disclosure. |
| Anthropic Agent Skills overview, <https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview> | Official vendor docs | 2026-07-01 | High | Confirms metadata/instructions/resources loading levels and recommends keeping the main skill body compact. |
| Claude Code skills docs, <https://code.claude.com/docs/en/skills> | Official product docs | 2026-07-01 | High | Confirms Claude Code follows Agent Skills and extends skills with direct slash invocation, subagent execution, and dynamic context injection. |
| OpenCode skills docs, <https://opencode.ai/docs/skills/> | Official product docs | 2026-07-01 | High | Confirms native on-demand `skill` tool, search paths, recognized fields, regex constraints, and permission controls. |
| OpenCode commands docs, <https://opencode.ai/docs/commands/> | Official product docs | 2026-07-01 | High | Confirms commands remain a separate markdown/config template mechanism. |
| Local installed OpenCode evidence | Local command output | 2026-07-01 | High | `opencode --version` reported 1.17.12 and `opencode debug config` parsed the local configuration. |
| Repository policy: `AGENTS.md`, `README.md`, `cron-harness/README.md` | Local canonical policy | 2026-07-01 | High | Forbids reintroducing root runtime config copies and keeps this repo focused on research notes and harness artifacts. |

## Key Findings

### 1) Agent Skills standard anatomy

- A skill is a directory whose name matches the skill name.
- `SKILL.md` is required and contains YAML frontmatter followed by Markdown instructions.
- Required fields: `name` and `description`.
- Standard optional fields: `license`, `compatibility`, and `metadata`; the spec also documents experimental `allowed-tools`.
- Name constraints: 1-64 characters, lowercase alphanumeric plus single hyphen separators, no leading/trailing/consecutive hyphens, and must match the parent directory.
- Description constraints: 1-1024 characters and should say both what the skill does and when to use it.
- Progressive disclosure is the core design pattern: metadata is always visible, the `SKILL.md` body loads on trigger, and bundled resources load only as needed.

### 2) Keep the main skill small

Anthropic recommends keeping the `SKILL.md` body under roughly 5k tokens and moving detail into supporting files. For this repository's guidance, treat the main skill as the decision/procedure layer, not a dump of docs. Put long examples, reference tables, templates, or scripts in supporting files only when the runtime actually needs them.

### 3) Platform behavior differs after the shared standard

Agent Skills provide the base package format, but product behavior varies. Claude Code can expose skills as slash commands and adds invocation/context features. OpenCode loads skills through the native `skill` tool, recognizes only standard metadata fields, and keeps commands as a separate feature.

### 4) This repository should not host runtime skill copies

Current repository policy says `research-notes` is an evidence and methodology workspace. It should maintain compact architecture guidance and evaluation checklists, not `.claude/skills/`, `.opencode/skills/`, `prompts/`, root `skills/`, or mirrored runtime artifacts. If downstream systems need a skill, create it in the operator-designated runtime workspace and cite this note as guidance.

## Platform Comparison

| Dimension | Agent Skills standard | Claude Code | OpenCode |
|---|---|---|---|
| Core package | Directory with `SKILL.md` plus optional `scripts/`, `references/`, `assets/` | Follows the Agent Skills standard | Follows the Agent Skills standard |
| Required frontmatter | `name`, `description` | Standard fields; docs also describe Claude Code-specific controls | Recognized fields: `name`, `description`, `license`, `compatibility`, `metadata`; unknown fields ignored |
| Loading model | Metadata first, body on trigger, resources on demand | Metadata/frontmatter supports auto-load and direct `/skill-name` invocation | Skills are loaded on demand through the native `skill` tool |
| Invocation | Spec defines package, not one UI | Direct slash invocation; `.claude/commands` still work but custom commands have merged into skills | Agent calls `skill({ name })`; permissions can allow, ask, deny, or disable the tool |
| Search / location | Implementation-specific | `.claude/skills/<name>/SKILL.md` and product-supported skill surfaces | `.opencode/skills/`, global OpenCode skills, `.claude/skills/`, global Claude skills, `.agents/skills/`, global Agents skills; project-local paths walk up to the git worktree |
| Commands relationship | Out of scope | Custom commands still work for compatibility; skills are the current capability surface | Commands remain separate templates under `commands/` with `description`, `agent`, `model`, `subtask`, arguments, shell output, and file references |
| Best use | Portable skill package | Claude Code workflows needing slash invocation, subagent execution, or dynamic context | OpenCode on-demand procedural knowledge with explicit skill-tool permission control |

## Design Rules: Skill vs Command vs Agent vs Reference

### Create a skill when

- The capability is repeatable and task-specific.
- It needs on-demand instructions or resources that would bloat an always-loaded prompt.
- Trigger conditions can be described clearly in 1-1024 characters.
- The workflow benefits from progressive disclosure.
- The same capability should be reusable across compatible agents or projects.

### Prefer a command when

- The user intentionally starts a workflow by name.
- The artifact is mostly a template or macro with argument substitution, shell output, or file references.
- The flow should choose an agent/model/subtask up front rather than adding mid-session capability.
- Platform-specific command behavior is acceptable.

### Prefer an agent when

- The work needs a distinct role, reasoning style, risk posture, autonomy level, or tool permission boundary.
- The behavior must govern the full session rather than one invoked procedure.
- Context isolation or specialist review/judgment is the primary value.

### Prefer a reference when

- The content is passive background knowledge.
- There is no clear invocation trigger or procedure.
- A short rule in `AGENTS.md`, a research note, or a downstream reference file is enough.

### Do not create a skill when

- A one-line policy or checklist item would work.
- The skill would mainly duplicate existing command/agent behavior.
- The content is stale, unsourced, or too broad to test.
- The target runtime workspace is unknown; design first, implement in the designated downstream runtime only.

## D.A.R.T.E. Skill Workflow

1. **Discovery** — Confirm target runtime, trigger, users/agents, inputs, outputs, tool needs, safety boundaries, source material, and whether a skill is better than a command, agent, or reference.
2. **Architecture** — Specify name, description, platform targets, frontmatter fields, progressive-disclosure split, resources, permission assumptions, evaluation criteria, rollback path, and uncertainty.
3. **Redaction** — Write `SKILL.md` and only the necessary supporting files in the designated runtime workspace. Keep the main body compact and task-focused; do not add identity/persona material.
4. **Test** — Validate frontmatter/schema, invocation behavior, happy path, edge cases, adversarial misuse, permission/tool assumptions, and cross-platform degradation if portability is claimed.
5. **Enhance** — Remove duplication, shorten the body, improve trigger wording, move heavy detail to resources, and rerun the evaluation checklist before approval.

## Evaluation Checklist

- **Fit**: Is a skill the right primitive instead of a command, agent, or reference?
- **Name**: Does `name` match the directory and the standard regex?
- **Description**: Does it clearly say what the skill does and when to use it, within 1-1024 characters?
- **Frontmatter**: Are fields limited to the target platform's supported schema, with unknown/experimental fields used intentionally?
- **Progressive disclosure**: Is `SKILL.md` concise, with long examples or references moved out?
- **Resources**: Are bundled scripts/references/assets necessary, minimal, and safe?
- **Invocation**: Are user-driven and agent-driven trigger paths tested on the target platform?
- **Arguments/context**: Are arguments, dynamic context, and missing-input behavior documented and tested?
- **Permissions/safety**: Are tool permissions, external side effects, secrets, and destructive actions constrained?
- **Portability**: If cross-platform support is claimed, are Claude Code and OpenCode differences handled explicitly?
- **Repository boundary**: For this repo, does the change avoid adding runtime config copies or root legacy prompt directories?
- **Rollback**: Can the skill or downstream runtime change be removed cleanly?

## Retired February 2026 File Plan

The earlier plan proposed adding or mirroring skill artifacts under paths such as:

- `prompts/templates/meta-task-create-skill.md`
- `prompts/skills/<name>/...`
- `.claude/skills/<name>/SKILL.md`
- local-runtime skill mirrors
- root runtime-oriented skill/prompt directories

That plan is obsolete for `research-notes`. It reflected an older workspace model that treated this repository as a runtime prompt/config store. Current policy explicitly says not to reintroduce root `agents/`, `skills/`, `templates/`, `prompts/`, or `guides/`, and not to bulk-copy runtime skills here. Keep only durable architecture guidance in `knowledge/` and implement runtime skills externally when explicitly requested in the correct workspace.

## Uncertainty and Re-check Path

- Re-check Agent Skills and product docs after OpenCode or Claude Code upgrades, because frontmatter support, command behavior, and invocation controls may change.
- Re-run `opencode --version` and `opencode debug config` before changing local OpenCode behavior.
- Treat Claude Code-specific fields as product-specific until verified in current docs; do not assume OpenCode honors them.
- If a future task asks to create a skill, first identify the target runtime workspace and confirm repository policy allows writing there.
- If source docs contradict this note, update this research file and `knowledge/INDEX.md` before using the new rule operationally.
