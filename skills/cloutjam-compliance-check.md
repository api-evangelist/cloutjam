---
name: compliance-check
description: |
  Use this skill to review contract terms and creator-facing language
  against compliance constraints — FTC disclosure rules, exclusivity
  windows, usage rights boundaries, and payment-term sanity. Flags risk
  before an agreement goes out the door or a payout clears.
license: MIT
---

# Compliance Check

## What this skill does

Influencer marketing has a compact set of compliance surfaces that
agencies routinely get wrong: FTC disclosure language on the creator's
posts, exclusivity windows that conflict with another active commitment,
usage-rights grants that exceed what the creator agreed to, payment terms
that violate the agency's standing playbook. This skill reviews a given
agreement or payout context against those constraints and produces a
short risk register — what's clean, what needs an edit, what blocks the
transaction.

The skill operates on already-structured agreement and collab data — it
does not extract terms from arbitrary documents. Pairs with
[influencer-contract-review](../influencer-contract-review/SKILL.md)
(which classifies inbound paperwork) and
[payout-orchestration](../payout-orchestration/SKILL.md) (which gates
disbursements on compliance pass).

## Composed into

- `agreement-reviewer` — final gate before an outbound agreement is sent for signature
- `finance-coordinator` — pre-payout check that terms were honored before disbursement

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_collab` | Read the collab's locked terms for cross-reference |

## Required scopes

- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/compliance-check/SKILL.md` (project-scoped) or `~/.claude/skills/compliance-check/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/compliance-check/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
