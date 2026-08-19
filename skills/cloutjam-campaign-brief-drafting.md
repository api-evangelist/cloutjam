---
name: campaign-brief-drafting
description: |
  Use this skill to draft an influencer campaign brief from a brand's
  objectives, budget, target audience, and channel preferences. Produces
  a structured brief that a Talent Rep can read, react to, and propose
  against — the inverse of the proposal-drafting flow.
license: MIT
---

# Campaign Brief Drafting

## What this skill does

A campaign brief is the marketer's articulation of what an influencer
campaign needs to accomplish: business objective, target audience, brand
guardrails, deliverable shape, budget envelope, success metrics. This
skill takes those inputs and produces a structured brief — clear enough
that a Talent Rep can react to it without a follow-up call, specific
enough that proposals can be scored against it. The natural downstream
consumer is [proposal-drafting](../proposal-drafting/SKILL.md), which
scores agency rosters against the brief.

The skill is marketer-side. It reads past briefs and collab outcomes to
calibrate budget and creative direction against what has worked in
similar campaigns, then drafts the new brief with explicit sections for
audience, channels, deliverable counts, usage rights, exclusivity
windows, and approval workflow.

## Composed into

Available as a standalone skill — not composed into any of the four
templates in this repo. Marketer-side agents can compose it directly.

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__list_collabs` | Enumerate past collabs in the brand's history for calibration |
| `cloutdesk__get_collab` | Read the structure and outcomes of a comparable past collab |

## Required scopes

- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/campaign-brief-drafting/SKILL.md` (project-scoped) or `~/.claude/skills/campaign-brief-drafting/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/campaign-brief-drafting/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
