---
name: client-reporting
description: |
  Use this skill to compose client-facing performance recaps for a
  talent agency's brand clients. Reads active and recently completed
  collabs across the agency's roster, then narrates the agency's
  contribution in language calibrated for a client deck.
license: MIT
---

# Client Reporting

## What this skill does

A talent agency's value to a brand client is most visible in the recap:
what the agency's roster delivered, how those deliverables performed,
where the agency drove outcomes the brand cares about. This skill
composes that recap by reading active and recently completed collabs
across the agency's roster, joining in deliverable performance metrics,
and structuring the narrative around brand-side outcomes (reach,
engagement, conversion proxies) rather than agency-internal process.

Downstream of [content-performance-analysis](../content-performance-analysis/SKILL.md):
that skill scores individual posts; this skill stitches multiple scored
posts into a coherent client-facing story. The output is typically a
multi-section markdown or slide-ready summary the rep can hand to a
client without further editing.

## Composed into

- `rep-assistant` — composing the periodic client recap a Talent Rep sends to their brand client
- `talent-dev` — preparing performance highlights for inclusion in new-business pitches

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__list_collabs` | Enumerate the agency's collabs for the client period |
| `cloutdesk__get_collab` | Read per-collab deliverable + metrics state |
| `cloutdesk__get_talent_profile` | Pull creator-side context for recap callouts |

## Required scopes

- `collaborations:read`
- `creators:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/client-reporting/SKILL.md` (project-scoped) or `~/.claude/skills/client-reporting/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/client-reporting/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
