---
name: aether
description: Ask natural language questions about your running Unity game and get AI-powered debugging analysis with full runtime context.
---

# Aether

Ask questions about your running Unity game. Aether gives the AI full visibility into live game state, events, console logs, and crash history — no log pasting required.

## Examples

- "What's the state of my game?"
- "Why is the player falling through the floor?"
- "What happened before that crash?"
- "Show me the last Unity console errors"
- "Did my fix work?"
- "Why is the game stuttering?"
- "Save this moment for later"

## How It Works

When you ask a question, the AI uses Aether's MCP tools to query your running Unity game directly:

- **`aether_snapshot`** — current state of GameObjects, scenes, and components
- **`aether_tail`** — recent events, console logs, and state changes
- **`aether_console`** — search and filter Unity stdout logs
- **`aether_last_run_answer`** — causal analysis of crashes and bugs with receipts
- **`aether_mark`** — save a moment for later replay or sharing

## Requirements

- Aether installed (`npx aether-init` from your Unity project root)
- Unity in Play Mode (for live data)
- Cursor reloaded after install (Ctrl+Shift+P → "Reload Window")
