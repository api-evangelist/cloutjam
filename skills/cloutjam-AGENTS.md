# Contributing to cloutdesk/agents

> Project-level instructions for AI coding agents (Claude Code, OpenAI Codex,
> Cursor, and similar) working on this repository. Human contributors should
> read this too — the conventions apply equally.

This repository ships open agent templates and atomic skills for the
influencer marketing workflow. The content is consumed by Claude Code,
OpenAI Codex, and Microsoft Agent Framework runtimes via standard
drop-in file formats. See [README.md](README.md) for the user-facing entry
point.

## Repo structure

```
.
├── README.md           # public-facing entry point
├── LICENSE             # MIT
├── AGENTS.md           # this file
├── .gitignore
├── agents/             # composed templates (one directory per template)
│   └── <slug>/
│       ├── agent.md         # Claude Code + OpenAI Codex subagent format
│       └── microsoft.yaml   # Microsoft Agent Framework declarative manifest
└── skills/             # atomic skills (one directory per skill)
    └── <slug>/
        └── SKILL.md         # Anthropic Agent Skills standard
```

Two top-level content directories: `agents/` and `skills/`. Each subdirectory
is a single template or skill respectively. No nesting beyond one level.

## Adding a new skill

Skills are atomic capabilities — a single, well-bounded behavior that one
or more templates can compose. To add a skill:

1. Create `skills/<slug>/SKILL.md` where `<slug>` follows the naming
   convention below.
2. Use the SKILL.md frontmatter contract:
   ```yaml
   ---
   name: <slug>
   description: |
     <2-3 sentence description of when an agent should use this skill>
   license: MIT
   ---
   ```
3. The body should contain: a `## What this skill does` section, a
   `## Composed into` section listing the templates that reference the skill,
   a `## Cloutdesk MCP tools typically called` table, a `## Required scopes`
   list, and a `## Standalone usage` section showing how to drop the skill
   into Claude Code, OpenAI Codex, and Microsoft Agent Framework consumers.

## Adding a new template

Templates compose skills into a persona-driven agent. To add a template:

1. Create `agents/<slug>/agent.md` (Anthropic + OpenAI Codex subagent format)
   and `agents/<slug>/microsoft.yaml` (Microsoft Agent Framework manifest).
2. Use the agent.md frontmatter contract:
   ```yaml
   ---
   name: <slug>
   description: |
     <2-3 sentence description of when to invoke this agent>
   skills:
     - <skill-slug>
     - <skill-slug>
   tools:
     - cloutdesk__<tool>
   model: sonnet   # runtime-specific; see note below
   ---
   ```
   The `model` value is consumed differently by each runtime. Claude Code
   and Claude Desktop accept Anthropic identifiers (`sonnet`, `opus`,
   `haiku`); OpenAI Codex expects OpenAI identifiers (`gpt-4o`, `gpt-4.1`,
   etc.); Microsoft Agent Framework configures the model on the client
   used at agent construction time and ignores this field. Templates in
   this repo default to `sonnet` because the Anthropic identifier is the
   most common consumer; downstream consumers should override as needed.
3. The body should contain: a `## What this template does` section, a
   `## Skills composed` table, a `## Cloutdesk MCP tools used` table, and
   an `## Invocation examples` section.
4. The matching `microsoft.yaml` mirrors the frontmatter as Microsoft Agent
   Framework declarative-agent fields (`kind: Prompt`, `name`, `description`,
   `instructions`, `tools.mcp.server` / `tools.mcp.name`).

## Naming conventions

**Skills are capability-named** — gerund (`-ing`) or activity noun-phrase.
Never persona-suffixed (no `-assistant`, `-coordinator`, `-analyst`).
Examples that pass: `talent-discovery`, `proposal-drafting`,
`compliance-check`, `media-kit-creation`. Examples that fail:
`talent-finder-assistant`, `compliance-coordinator`.

**Templates are persona-named** — typically `<role>-<role-modifier>` form.
Examples that pass: `rep-assistant`, `agreement-reviewer`,
`finance-coordinator`, `talent-dev`. The persona name is the agent's job
identity; the skill names are the capabilities it composes.

**Slug format for both:** lowercase, hyphens, ≤64 characters, no reserved
words (`anthropic`, `claude`).

## Cross-references

The frontmatter `skills:` array in each template's `agent.md` references
skill slugs by directory name. The validator script (see "Validation"
below) enforces that every referenced skill exists at
`skills/<slug>/SKILL.md`.

When a skill body references another skill (e.g. `content-performance-analysis`
naturally hands off to `client-reporting`), use a relative markdown link:
`[client-reporting](../client-reporting/SKILL.md)`.

## Tool naming

Cloutdesk MCP tools follow MCP namespacing: `cloutdesk__<tool>`. The
prefix `cloutdesk` is the MCP server's config key in
`claude_desktop_config.json` (or equivalent). The six tools currently
exposed are documented in this repo's README.

## Validation

A validator script ships with the upstream source. Contributors running
this repository's CI should ensure the validator passes for every commit
that adds or modifies a skill or template. Local contributors can run an
equivalent check:

```
# Every agents/<slug>/ has agent.md + microsoft.yaml
# Every skills/<slug>/ has SKILL.md
# Every <slug> matches ^[a-z0-9-]+$
# Every skill referenced in any agent.md frontmatter exists as a SKILL.md
# Every cloutdesk__<tool> matches one of the six published tools
```

## Quality bar

- **Cross-vendor.** Every template ships both `agent.md` (Anthropic/OpenAI)
  and `microsoft.yaml` (Microsoft). Don't break parity by adding
  Anthropic-only fields without a Microsoft equivalent.
- **No over-claim.** Templates are scaffolds — the bodies describe capability
  and intent, not "production-ready" or "enterprise-grade." Edit phrasing
  toward "useful starting point" rather than "ready to ship."
- **Repo-self-contained.** The published repo carries no upstream references
  to other internal repositories, paths, or contracts. If a contribution
  references an outside artifact, rewrite the reference before merging.
- **MIT-licensed contributions.** All contributed content is MIT licensed
  per the repo's LICENSE.
