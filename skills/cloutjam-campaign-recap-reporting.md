---
name: campaign-recap-reporting
description: |
  Use this skill to produce a campaign performance recap after a
  marketer's influencer campaign wraps. Assembles participating
  creators, posted deliverables, engagement metrics, and outcomes
  against the original brief into a stakeholder-ready report.
license: MIT
---

# Campaign Recap Reporting

## What this skill does

After an influencer campaign wraps, the marketer needs to write up what
happened: which creators participated, what they posted, how those posts
performed against benchmarks, what the brand learned, what to repeat or
change next time. This skill assembles the recap directly from the
live collab, deliverable, and metrics data — no manual pasting from
five surfaces.

The recap is marketer-side. It mirrors the structure of the original
brief (audience, channels, deliverable counts, success metrics) and
fills in the actuals, then narrates the deltas in language suitable
for internal stakeholders. Pairs naturally with
[campaign-brief-drafting](../campaign-brief-drafting/SKILL.md) so a
recap directly references the brief it scores.

## Composed into

Available as a standalone skill — not composed into any of the four
templates in this repo. Marketer-side agents can compose it directly.

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__list_collabs` | Enumerate the collabs that ran under the campaign |
| `cloutdesk__get_collab` | Read per-collab deliverable + metrics state |
| `cloutdesk__emit_event` | Log the recap-generated event for audit trail |

## Required scopes

- `collaborations:read`
- `events:emit`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/campaign-recap-reporting/SKILL.md` (project-scoped) or `~/.claude/skills/campaign-recap-reporting/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/campaign-recap-reporting/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
