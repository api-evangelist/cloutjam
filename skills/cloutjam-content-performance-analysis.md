---
name: content-performance-analysis
description: |
  Use this skill to analyze posted-content performance against
  benchmarks for a creator's recent deliverables. Scores engagement,
  reach, and audience-quality signals per post, then surfaces the
  insights a Talent Rep would otherwise compute by hand.
license: MIT
---

# Content Performance Analysis

## What this skill does

Once a creator's deliverable goes live, the post's performance becomes
the most important signal in the agency-client relationship: did the
creative resonate, did the audience composition match the brand's
target, did the engagement clear the benchmarks the agency promised in
the brief. This skill reads the live-post and metrics state for a
deliverable, joins in comparable benchmarks from the creator's history
and similar past collabs, and produces a per-post performance read.

The output is structured — engagement rate, reach quality, audience
composition deltas, sentiment cues from comments where available, and
a plain-language summary that calls out the two or three things a Rep
should know. Naturally hands off to
[client-reporting](../client-reporting/SKILL.md), which aggregates
per-post reads into a multi-post recap.

## Composed into

- `rep-assistant` — scoring fresh deliverables for inclusion in client recaps
- `talent-dev` — calibrating future content recommendations against what is actually working

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__list_collabs` | Find comparable past collabs for benchmark calibration |
| `cloutdesk__get_collab` | Read the deliverable's metrics + live-post state |
| `cloutdesk__get_talent_profile` | Pull the creator's historical performance baseline |

## Required scopes

- `collaborations:read`
- `creators:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/content-performance-analysis/SKILL.md` (project-scoped) or `~/.claude/skills/content-performance-analysis/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/content-performance-analysis/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
