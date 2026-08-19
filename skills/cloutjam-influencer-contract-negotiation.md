---
name: influencer-contract-negotiation
description: |
  Use this skill to counter-propose terms in an active creator agreement
  negotiation. Reads the other side's redlines, evaluates them against
  the agency's playbook, and drafts a counter-proposal that holds the
  agency's positions while acknowledging the creator's asks.
license: MIT
---

# Influencer Contract Negotiation

## What this skill does

Active contract negotiations are where the agreement-reviewer earns its
keep. The creator's side comes back with redlines — usually on payment
timing, exclusivity scope, usage rights duration, kill-fee terms — and
the agency needs to evaluate each ask against its playbook, decide where
to hold and where to give, and draft a coherent counter. This skill does
the evaluation-and-drafting pass: reads the inbound redlines, scores
each against the agency's policy, and proposes a counter that holds the
agency's load-bearing positions while showing movement on the asks that
genuinely don't matter.

Emits an event when a counter is drafted so the rep's activity timeline
shows negotiation state changes without polling. Sits between
[influencer-contract-review](../influencer-contract-review/SKILL.md)
(which classified the initial inbound) and the final round through
[compliance-check](../compliance-check/SKILL.md) before signature.

## Composed into

- `agreement-reviewer` — drafting counter-proposals during active negotiation rounds

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_collab` | Read the collab's locked terms + the agency's playbook context |
| `cloutdesk__emit_event` | Log the counter-drafted event for negotiation timeline |

## Required scopes

- `collaborations:read`
- `events:emit`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/influencer-contract-negotiation/SKILL.md` (project-scoped) or `~/.claude/skills/influencer-contract-negotiation/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/influencer-contract-negotiation/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
