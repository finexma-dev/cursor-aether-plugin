---
name: aether-replay
description: Replay and share debugging sessions using clips, marks, and capsules. Use when the user asks to save a moment, create a clip, mark a point in time, package a capsule, or share debugging context with teammates.
---

# Replay and Sharing

## When to Use

- User asks to "save this moment", "mark this", or "bookmark this point"
- User wants to create a clip or capsule for later analysis
- User asks to package debugging context to share with a teammate or attach to a bug report
- User wants to replay or review a previous session

## Workflow

1. **Mark the moment:** Use `aether_mark` to save the current point in time with a label and optional context note.
2. **Review the window:** Use `aether_tail` to see the events around the marked moment — confirm it captured what the user intended.
3. **Package a capsule:** If the user wants a shareable artifact, guide them to use capsule packaging (Pro feature) — this bundles the timeline, suspects, and receipts into an export block.
4. **Verify the clip:** After marking or packaging, confirm the clip was saved by checking the output message.

## Key Tools

| Tool | Role in replay and sharing |
|------|---------------------------|
| `aether_mark` | Primary — save a moment with label and context |
| `aether_tail` | Review events around a marked moment |
| `aether_snapshot` | Capture object state at the marked moment |

## Tips

- Marks persist across Play Mode restarts — the user can stop and start Unity without losing saved moments.
- Capsules (Pro) include the full timeline, grouped errors, suspect hints, and an export block ready for an AI agent to consume.
- If the user asks to "share" a debugging session, suggest packaging a capsule — it's the most complete format.
