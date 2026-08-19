---
name: influencer-contract-drafting
description: |
  Use this skill to draft a creator agreement from a collab's locked
  terms — rate, deliverables, exclusivity windows, usage rights, and
  payment schedule. Produces a clean first draft ready for review and
  redline by the agency's contract owner.
license: MIT
---

# Influencer Contract Drafting

## What this skill does

Once a collab's commercial terms are locked in (the rate is agreed, the
deliverable count is agreed, the timeline is set), drafting the actual
contract is largely mechanical: pull the agency's standard creator
agreement template, populate the variable fields from the collab record,
and hand off a clean first draft. This skill does that — reads the
collab's locked terms, fills in rate, deliverables, exclusivity windows,
usage rights, and payment schedule, and produces a draft contract a
human can review without rebuilding from scratch.

Drafting is the easiest of the three contract skills in this catalog.
Pairs with [influencer-contract-review](../influencer-contract-review/SKILL.md)
(reviews the inbound counter-signature) and
[influencer-contract-negotiation](../influencer-contract-negotiation/SKILL.md)
(handles back-and-forth term changes), and is gated by
[compliance-check](../compliance-check/SKILL.md) before the draft goes
to signature.

## Composed into

- `agreement-reviewer` — drafting the initial outbound agreement once commercial terms are locked

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_collab` | Read the collab's locked commercial terms |

## Required scopes

- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/influencer-contract-drafting/SKILL.md` (project-scoped) or `~/.claude/skills/influencer-contract-drafting/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/influencer-contract-drafting/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
