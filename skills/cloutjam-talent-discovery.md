---
name: talent-discovery
description: |
  Use this skill to discover and shortlist talent candidates from an
  agency's roster based on audience demographics, brand fit signals,
  and historical performance. The starting point for any
  proposal-slate or new-business-pitch flow.
license: MIT
---

# Talent Discovery

## What this skill does

The agency's roster is its inventory; talent discovery is how that
inventory gets matched to demand. Given a brief — even a thin one
("looking for fitness creators with a 25-40 female-skewing audience
who've worked with athleisure brands") — this skill scans the roster,
scores candidates against the brief's audience and brand-fit targets,
and produces a shortlist with the signals (audience composition,
historical category fit, past brand collaborations) that justify each
pick.

Discovery is the upstream skill behind multiple downstream flows:
[proposal-drafting](../proposal-drafting/SKILL.md) (when the shortlist
becomes a client-facing slate) and
[content-strategy](../content-strategy/SKILL.md) (when discovery is
used for internal talent-development triage rather than client
response). The skill is read-only and judgment-light — it surfaces
candidates with their signals; the rep picks.

## Composed into

- `rep-assistant` — drafting the candidate shortlist that becomes a client proposal slate
- `talent-dev` — finding roster creators who fit emerging brand opportunities

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_talent_profile` | Read per-creator audience demographics + performance |
| `cloutdesk__list_collabs` | Surface historical brand-fit signals from past collabs |

## Required scopes

- `creators:read`
- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/talent-discovery/SKILL.md` (project-scoped) or `~/.claude/skills/talent-discovery/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/talent-discovery/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
