---
name: media-kit-creation
description: |
  Use this skill to compose a creator's media kit from profile,
  audience, and historical performance data. Produces a structured
  asset ready for outbound brand pitching — the agency's standard
  pitch packet without the manual assembly.
license: MIT
---

# Media Kit Creation

## What this skill does

A media kit is the agency's pitch document for a creator: a one-or-two
page packet that summarizes who the creator is, who their audience is,
what they've done, what they're great at, and what kinds of brand
partnerships fit. Agencies maintain a standard template; the per-creator
assembly is what eats time. This skill produces the per-creator kit from
the structured profile, audience, and historical performance data — pulled
once, formatted consistently, and ready to drop into the agency's
outbound template.

The kit is the natural artifact for outbound new-business pitching.
Upstream of any proposal flow when the agency is introducing a creator
the brand client has not yet worked with. Pairs with
[content-strategy](../content-strategy/SKILL.md) (which informs the
"what we'd do with this creator" section) and feeds into
[proposal-drafting](../proposal-drafting/SKILL.md) when the kit becomes
the basis for a specific RFP response.

## Composed into

- `talent-dev` — composing creator media kits for outbound new-business pitching

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_talent_profile` | Read audience demographics + historical performance |
| `cloutdesk__list_collabs` | Surface past collab highlights for the kit's portfolio section |

## Required scopes

- `creators:read`
- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/media-kit-creation/SKILL.md` (project-scoped) or `~/.claude/skills/media-kit-creation/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/media-kit-creation/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
