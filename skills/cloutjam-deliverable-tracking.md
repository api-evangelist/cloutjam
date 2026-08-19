---
name: deliverable-tracking
description: |
  Use this skill to surface deliverable status across an agency's
  active collabs, comment on specific deliverables to push them
  forward, and emit events when status changes. The day-to-day
  coordination layer beneath a Talent Rep's inbox.
license: MIT
---

# Deliverable Tracking

## What this skill does

A talent rep with twenty active collabs is mostly tracking deliverables:
which creator owes a concept, whose content is awaiting client approval,
which live post still needs metrics pulled, where a stalled status
should be nudged. This skill enumerates the rep's active deliverables
with their current stage, surfaces what is overdue or blocked, and
lets the agent comment on a specific deliverable to advance it — for
example, requesting revised concept artwork or acknowledging a
client-side approval.

Events emitted by the skill (status changes, comments posted) feed the
agency's activity timeline so other agents and humans see the state
change without polling. Pairs with
[talent-communications](../talent-communications/SKILL.md), which
drafts the creator-facing language that often accompanies a status
nudge.

## Composed into

- `rep-assistant` — day-to-day coordination across the Talent Rep's active collab portfolio

## Cloutdesk MCP tools typically called

| Tool | What for |
|---|---|
| `cloutdesk__list_collabs` | Enumerate the rep's active collabs |
| `cloutdesk__get_collab` | Read deliverable state for a specific collab |
| `cloutdesk__comment_on_deliverable` | Post a coordination note on a deliverable |
| `cloutdesk__emit_event` | Signal a deliverable status change to downstream consumers |

## Required scopes

- `collaborations:read`
- `collaborations:write` (for `comment_on_deliverable`)
- `events:emit`

## Standalone usage

Drop this skill into:

- **Claude Code / Claude Desktop** — `.claude/skills/deliverable-tracking/SKILL.md` (project-scoped) or `~/.claude/skills/deliverable-tracking/SKILL.md` (user-scoped)
- **OpenAI Codex** — `.codex/skills/deliverable-tracking/SKILL.md`
- **Other Anthropic Agent Skills-compliant runtimes** — per the runtime's documented skills directory

For Microsoft Agent Framework consumers, this skill's behavior is inlined into the
template-level `microsoft.yaml` manifests under their `instructions:` field rather
than dropped in as a separate file.
