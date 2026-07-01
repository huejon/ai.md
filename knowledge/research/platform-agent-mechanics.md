# Platform Agent Mechanics — Claude Code & OpenCode

> Last updated: 2026-07-01
> Status: Current

## Summary

Claude Code and OpenCode both support reusable Markdown-defined agents, but their mechanics are not interchangeable. Treat the Markdown body as the portable instruction layer and the frontmatter/config as platform-specific. Source confidence is high for current official documentation fetched 2026-07-01, and medium-high for local OpenCode behavior because this machine runs OpenCode `1.17.12` while the web docs were last updated 2026-06-30 and may describe newer behavior.

## Sources

| Source | Date checked | Source date/version | Confidence | Notes |
|---|---:|---|---|---|
| Claude Code custom subagents docs: <https://docs.anthropic.com/en/docs/claude-code/sub-agents> | 2026-07-01 | Current official docs; page includes version annotations through 2.1.x | High | Primary source for Claude Code subagent scope, context, fields, invocation, permissions, background mode, and Agent/Task naming. |
| Claude Code settings docs: <https://docs.anthropic.com/en/docs/claude-code/settings> | 2026-07-01 | Current official docs; page includes version annotations through 2.1.x | High | Primary source for settings scopes, precedence, and `agent` setting. |
| OpenCode agents docs: <https://opencode.ai/docs/agents/> | 2026-07-01 | Last updated 2026-06-30 | High for docs | Primary source for primary agents, subagents, config fields, markdown locations, task permission, and built-ins. |
| OpenCode config docs: <https://opencode.ai/docs/config/> | 2026-07-01 | Last updated 2026-06-30 | High for docs | Primary source for config precedence, `.opencode` directories, `agent`, `default_agent`, commands, permissions, and variables. |
| OpenCode commands docs: <https://opencode.ai/docs/commands/> | 2026-07-01 | Last updated 2026-06-30 | High for docs | Primary source for command files, arguments, command agent selection, and `subtask`. |
| OpenCode tools docs: <https://opencode.ai/docs/tools/> | 2026-07-01 | Last updated 2026-06-30 | High for docs | Primary source for built-in tools and permission mapping. |
| Local installed evidence: `opencode --version`, `opencode debug config`, `opencode debug agent work`, `opencode debug paths` | 2026-07-01 | OpenCode 1.17.12 | Medium-high | Confirms this machine's resolved config shape, `default_agent`, `agent` map, `command` map, permissions, `task` tool exposure, and config paths. |

## Key Findings

### 1. Context and delegation model

- **Claude Code:** each subagent runs in its own context window with its own system prompt, tool access, and permissions, then returns results to the main conversation. Subagents are useful when exploration/log output should not pollute the main context. The current docs say subagents receive the subagent prompt plus basic environment details, not the full Claude Code system prompt.
- **OpenCode:** docs distinguish **primary agents** (main assistant, switchable with Tab/keybind) from **subagents** (invoked automatically by primary agents or manually by `@` mention). Subagent work appears as child sessions; docs describe navigation from parent to child and back.
- **Operational rule:** pass only the task-specific context a subagent needs. Do not assume a spawned agent can see the parent's full transcript unless current platform docs explicitly say so.

### 2. Claude Code mechanics

- Agent files are Markdown with YAML frontmatter and a Markdown body. Project subagents live under `.claude/agents/`; user subagents live under `~/.claude/agents/`; managed, CLI-defined, and plugin subagents also exist with documented precedence.
- Only `name` and `description` are required in file frontmatter. Current supported fields include `tools`, `disallowedTools`, `model`, `permissionMode`, `maxTurns`, `skills`, `mcpServers`, `hooks`, `memory`, `background`, `effort`, `isolation`, `color`, and `initialPrompt`.
- Built-ins include Explore, Plan, general-purpose, statusline-setup, and claude-code-guide.
- The docs now describe the tool as **Agent**; existing `Task(...)` references in settings and agent definitions remain aliases after the documented Task-to-Agent rename.
- Subagents can be invoked by natural language, `@` mention, or by running the main session as an agent with `claude --agent <name>` / the `agent` setting.
- Claude Code settings scopes are managed, CLI, local, project, and user; subagents use managed, CLI, project, user, and plugin scopes. Settings files live under `~/.claude/` and `.claude/` depending on scope.

### 3. OpenCode mechanics

- OpenCode config is JSON/JSONC with schema `https://opencode.ai/config.json`. Config sources are merged in documented precedence: remote, global `~/.config/opencode/opencode.json`, `OPENCODE_CONFIG`, project `opencode.json`, `.opencode` directories, `OPENCODE_CONFIG_CONTENT`, managed config files, then macOS managed preferences.
- OpenCode uses plural config directories such as `agents/`, `commands/`, `skills/`, `tools/`, and `themes/` under `~/.config/opencode/` or `.opencode/`; singular names remain backward-compatible.
- Agents can be configured in the `agent` object or as Markdown files under `~/.config/opencode/agents/` or `.opencode/agents/`. For Markdown agents, the file name becomes the agent name.
- Current documented agent fields include `description`, `temperature`, `steps` (with legacy `maxSteps` deprecated), `disable`, `prompt`, `model`, deprecated `tools`, `permission`, `mode`, `hidden`, `color`, `top_p`, and provider-specific additional options. `mode` is `primary`, `subagent`, or `all`; default is `all`.
- Built-ins documented on 2026-06-30: primary `build` and `plan`; subagents `general`, `explore`, and `scout`; hidden system agents `compaction`, `title`, and `summary`.
- OpenCode commands can be configured in the `command` object or Markdown files under `commands/`. A command may select an `agent`; if the selected agent is a subagent, invocation defaults to a subtask, and `subtask: true` forces subagent-style execution even for primary-mode agents.
- OpenCode tools are controlled by `permission`, not new `tools` config. Built-ins include `bash`, `edit`, `write`, `read`, `grep`, `glob`, experimental `lsp`, `apply_patch`, `skill`, `todowrite`, `webfetch`, `websearch`, and `question`.

### 4. Installed OpenCode 1.17.12 evidence on this machine

- `opencode --version` returned `1.17.12`.
- `opencode debug paths` returned config path `/var/home/core/.config/opencode`, data path `/var/home/core/.local/share/opencode`, and tmp path `/tmp/opencode`.
- `opencode debug config` showed this machine uses `default_agent: "work"`, `model: "openai/gpt-5.5"`, `small_model: "opencode-go/minimax-m3"`, `share: "disabled"`, project/user instructions, an `agent` map, a `command` map, and permission keys including `bash`, `read`, `question`, `external_directory`, and `doom_loop`.
- `opencode debug agent work` showed `work` as a primary agent with `task`, `webfetch`, `todowrite`, `skill`, and `apply_patch` available. Reviewer/judge agents inspected locally were `mode: "subagent"` with model IDs under `opencode-go/*`.
- Installed evidence confirms the local config shape used by this workspace, but it does not prove every current web-doc feature is available in 1.17.12.

## Cross-Platform Design Rules

| Concern | Claude Code | OpenCode | Portable rule |
|---|---|---|---|
| Agent file body | Markdown system prompt | Markdown body or `prompt` | Keep behavior instructions platform-neutral. |
| Agent identity | `name` frontmatter | Markdown file name or `agent` key | Do not rely on identical naming rules. |
| Project location | `.claude/agents/` | `.opencode/agents/` or `opencode.json` | Keep platform config in platform-specific paths. |
| User location | `~/.claude/agents/` | `~/.config/opencode/agents/` | Do not copy whole runtime trees between tools. |
| Primary-agent mode | `claude --agent` / `agent` setting | `mode: primary` / `default_agent` | Configure separately per platform. |
| Subagent invocation | Agent tool / `@` mention / natural language | Task tool / `@` mention / command `subtask` | Treat subagent calls as isolated work packets. |
| Tool control | `tools`, `disallowedTools`, permissions | `permission`; `tools` deprecated | Prefer least privilege and current permission syntax. |
| Commands | Slash commands in Claude Code docs | `command` config or `.opencode/commands/*.md` | Keep command templates small and explicit. |

## Implications for This Workspace

- This repository should keep research notes and distilled operating rules, not active Claude Code or OpenCode runtime copies.
- When designing reusable agents, author the durable behavior as a compact Markdown body, then create separate platform frontmatter/config wrappers only in the appropriate runtime workspace.
- For OpenCode on this machine, use installed `opencode debug config`, `opencode debug agent <name>`, and `opencode debug paths` as the first local truth before relying on web docs for a config change.
- Avoid obsolete placeholder wording such as unspecified vendor/local-runner mechanics. Name the actual platform being researched: Claude Code or OpenCode.

## Uncertainty and Re-check Path

- Claude Code docs fetched here are current official docs but did not expose a page-level last-updated date in the fetched text; version annotations imply behavior may vary by Claude Code version.
- OpenCode docs are newer than the installed CLI evidence on this machine. Before applying a newly documented field, re-check with `opencode --version`, `opencode debug config`, `opencode debug agent <name>`, and the current `https://opencode.ai/config.json` schema.
- Re-check this note when OpenCode is upgraded from 1.17.12, when Claude Code changes Agent/Task semantics, or when this workspace changes its local agent/reviewer panel policy.
