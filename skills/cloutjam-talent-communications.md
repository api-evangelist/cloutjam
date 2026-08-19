---
name: talent-communications
description: |
  Use this skill to draft creator-facing communications across the
  collab lifecycle — initial outreach, status updates, deliverable
  feedback, and closeout notes. Calibrates voice and detail to the
  collab's stage and the creator's prior interaction pattern.
license: MIT
---

# Talent Communications

## What this skill does

A talent rep's relationship with their roster is sustained through
small, well-timed messages — the initial outreach when an opportunity
lands, the status update when a deliverable is approved, the gentle
nudge when a concept is overdue, the closeout note when a campaign
wraps. Each of those moments has a typical shape but also a personal
quality that comes from knowing the creator. This skill drafts those
communications by reading the collab's current state and the rep's
prior interaction pattern with the creator, then producing a message
calibrated to the stage and the relationship.

Pairs with [deliverable-tracking](../deliverable-tracking/SKILL.md)
(which surfaces the deliverable-status events that trigger most of
these messages) and emits an event when a communication is drafted so
the rep's activity timeline reflects the send.

## Composed into

- `rep-assistant` — drafting creator-facing messages across the collab lifecycle

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__get_collab` | Read the collab's current state + interaction history |
| `cloutdesk__emit_event` | Log the communication-drafted event for timeline |

## Required scopes

- `collaborations:read`
- `events:emit`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/talent-communications/SKILL.md` (project-scoped) or `~/.claude/skills/talent-communications/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/talent-communications/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
