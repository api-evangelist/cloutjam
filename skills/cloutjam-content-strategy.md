---
name: content-strategy
description: |
  Use this skill to recommend content directions for a creator based
  on their audience composition, brand fit signals, and what is
  currently working in adjacent creators' recent posts. Read-and-advise,
  not action-taking.
license: MIT
---

# Content Strategy

## What this skill does

Talent development is partly about giving a creator credible, specific
advice on what to make next: which formats to lean into, which angles
match the audience they actually have (not the one they think they have),
which brand-adjacent themes are converting on the platform right now.
This skill produces those recommendations by reading the creator's
audience demographics and recent performance, then proposing directional
content ideas calibrated to brand opportunities the agency is currently
working.

The skill is intentionally read-and-advise. It surfaces intelligence —
the Talent Dev role decides what to do with it. Pairs upstream of
[proposal-drafting](../proposal-drafting/SKILL.md) (when a content
direction firms into a pitchable proposal) and
[media-kit-creation](../media-kit-creation/SKILL.md) (when the
direction is packaged for outbound brand pitching).

## Composed into

- `talent-dev` — generating directional content ideas for an active creator in development

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_talent_profile` | Read audience demographics + historical performance |
| `cloutdesk__list_collabs` | Surface the creator's past collab themes + outcomes |

## Required scopes

- `creators:read`
- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/content-strategy/SKILL.md` (project-scoped) or `~/.claude/skills/content-strategy/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/content-strategy/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
