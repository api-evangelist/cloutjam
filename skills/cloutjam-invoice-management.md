---
name: invoice-management
description: |
  Use this skill to track invoice issuance, payment status, and
  reconciliation against the collab terms that drove each invoice.
  Surfaces what is overdue, what is in dispute, and what is ready to
  release for payout.
license: MIT
---

# Invoice Management

## What this skill does

An agency's accounts-receivable surface is mostly: which invoices have
gone out, which have been paid, which are aging into overdue, which
have a dispute that needs human attention. This skill reads the
agency's invoice state alongside the collab terms that drove each
invoice (rate, deliverable completion gates, payment schedule
milestones), then produces a current AR view — what to chase, what to
escalate, what to reconcile.

Pairs with [payout-orchestration](../payout-orchestration/SKILL.md),
which moves money out to creators on the back of inbound payments
arriving — invoice-management is the inbound-money tracking surface,
payout-orchestration is the outbound. Together they close the loop
between client cash and creator disbursement.

## Composed into

- `finance-coordinator` — day-to-day accounts-receivable tracking across the agency's invoiced clients

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_revenue_summary` | Read the agency's current AR aging + invoice state |
| `cloutdesk__list_collabs` | Cross-reference invoice line items against active collabs |
| `cloutdesk__get_collab` | Read the collab terms that drove a specific invoice |

## Required scopes

- `transactions:read`
- `collaborations:read`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/invoice-management/SKILL.md` (project-scoped) or `~/.claude/skills/invoice-management/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/invoice-management/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
