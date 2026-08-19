---
name: influencer-contract-review
description: |
  Use this skill to review an inbound creator agreement for risk
  coverage and term completeness. Classifies redlines by risk level,
  flags missing standard clauses, and produces a short summary the
  contract owner can act on without reading the full document.
license: MIT
---

# Influencer Contract Review

## What this skill does

Inbound agreements arrive in many shapes — sometimes a creator's
manager-drafted contract, sometimes a brand client's pre-populated
template with an unusual exclusivity ask, sometimes a paid-media
addendum that adds new usage rights. The first pass is always the same:
classify the document, flag the high-risk clauses, identify missing
standard clauses the agency's playbook expects, and summarize. This
skill performs that first pass and produces a structured risk
register the contract owner can scan in under a minute.

The skill does not negotiate — it surfaces. The negotiation pass lives
in [influencer-contract-negotiation](../influencer-contract-negotiation/SKILL.md).
A clean review can hand off directly to signature via
[compliance-check](../compliance-check/SKILL.md); a dirty review
escalates to the negotiation skill or to a human contract owner.

## Composed into

- `agreement-reviewer` — first-pass triage of every inbound agreement before deciding negotiate-vs-sign

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_collab` | Read the collab context the agreement attaches to |
| `cloutdesk__emit_event` | Log the review-completed event for collab timeline |

## Required scopes

- `collaborations:read`
- `events:emit`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/influencer-contract-review/SKILL.md` (project-scoped) or `~/.claude/skills/influencer-contract-review/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/influencer-contract-review/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
