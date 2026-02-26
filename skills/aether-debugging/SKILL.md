---
name: aether-debugging
description: Debug Unity gameplay behavior using Aether MCP tools. Use when the user reports a gameplay bug, unexpected object behavior, or needs to inspect live game state during Play Mode.
---

# Gameplay Debugging

## When to Use

- User mentions a Unity gameplay bug or unexpected behavior (not crashes — see aether-crash-investigation)
- User asks "why is this object falling through the floor?", "why isn't my animation playing?", or "what's wrong with my player controller?"
- User is in Play Mode and needs to inspect object state or recent events
- User references Aether tools or GTML

## Prerequisites

1. Bridge installed (plugin auto-downloads, or user ran `npx aether-init`)
2. Unity is in Play Mode

## Workflow

1. **Snapshot the object:** Use `aether_snapshot` to get the current state of the selected GameObject — transforms, components, fields.
2. **Check recent events:** Use `aether_tail` with a 5–15s window to see what happened recently — state changes, events, console messages.
3. **Search logs:** Use `aether_console` with text filters to find relevant log entries.
4. **Analyze GTML:** Look for `[ISSUE: ...]` tags in the output — these are detected problems (disabled colliders, zero velocity, missing references, etc.).
5. **Suggest a fix:** Based on the evidence, propose a targeted code change.

## Key Tools

| Tool | Use when |
|------|----------|
| `aether_snapshot` | Need current state of selected GameObject, scene, frame |
| `aether_tail` | Need recent events, console logs, state changes (last N seconds) |
| `aether_console` | Need to search/filter Unity stdout logs |
| `aether_docs` | Need full tool documentation |

## Output Format

Aether returns GTML (Game Temporal Markup Language) — structured XML that LLMs parse well. Look for `[ISSUE: ...]` tags for detected problems.
