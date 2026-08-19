---
name: payout-orchestration
description: |
  Use this skill to coordinate creator payouts across active collabs —
  computing the agency's commission split, routing the creator-side
  disbursement through Stripe Connect, and surfacing payout state for
  the finance team.
license: MIT
---

# Payout Orchestration

## What this skill does

When a brand client's payment lands, the agency owes the creator their
share — net of the agency's commission, on the schedule the contract
specified. This skill orchestrates that disbursement: reads the
inbound payment against the collab's payment schedule, computes the
agency commission and creator-side amount, and prepares the Stripe
Connect transfer that routes the creator share to the creator's
connected account.

The skill does not move money on its own — it stages the transfer
context for a human or downstream automation to execute. Gated by
[compliance-check](../compliance-check/SKILL.md) before disbursement
clears (terms must have been honored), and paired with
[invoice-management](../invoice-management/SKILL.md) which tracks the
inbound side of the same money flow.

## Composed into

- `finance-coordinator` — coordinating creator payouts as client payments arrive

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_revenue_summary` | Read the agency's payout queue + Connect-account state |
| `cloutdesk__list_collabs` | Cross-reference payout context against active collabs |
| `cloutdesk__get_collab` | Read the payment schedule + commission split for a specific collab |

## Required scopes

- `transactions:read`
- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/payout-orchestration/SKILL.md` (project-scoped) or `~/.claude/skills/payout-orchestration/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/payout-orchestration/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
