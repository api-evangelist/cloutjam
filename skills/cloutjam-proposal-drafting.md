---
name: proposal-drafting
description: |
  Use this skill to compose a proposal slate against a talent agency's
  roster from an inbound brand brief or RFP. Reads the brief's audience
  and creative targets, scores the agency's available creators against
  them, and drafts a multi-creator pitch the rep can send.
license: MIT
---

# Proposal Drafting

## What this skill does

When a brief lands in a Talent Rep's inbox, the next action is almost
always: propose three to five creators from the agency's roster who
match the brief's audience, budget, and creative shape, in a format the
brand client can scan and react to. This skill does the matching and
the drafting in one pass — reads the brief, scores roster creators
against the audience + creative + budget targets, picks the slate, and
composes the proposal narrative around each creator's strongest signals
for this specific brief.

Naturally downstream of [talent-discovery](../talent-discovery/SKILL.md)
(the shortlist that becomes a slate) and upstream of
[talent-communications](../talent-communications/SKILL.md) (the
creator-facing notes that go out once the slate is approved).

## Composed into

- `rep-assistant` — drafting a multi-creator proposal slate in response to an inbound brand brief

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__list_collabs` | Surface past collab outcomes for proposal calibration |
| `cloutdesk__get_collab` | Read the source collab a brief attaches to |
| `cloutdesk__get_talent_profile` | Read per-creator audience + performance for slate scoring |

## Required scopes

- `collaborations:read`
- `creators:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/proposal-drafting/SKILL.md` (project-scoped) or `~/.claude/skills/proposal-drafting/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/proposal-drafting/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
