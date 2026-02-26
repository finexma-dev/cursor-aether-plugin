---
name: aether-unity-setup
description: Set up Aether in a Unity project. Use when the user asks how to install Aether, configure the bridge, set up MCP, or get started with AI-assisted Unity debugging.
---

# Aether Unity Setup

## When to Use

- User asks "how do I install Aether?", "how do I set up Aether?", or "how do I get started?"
- User is in a Unity project and wants to connect it to Cursor via Aether
- Aether tools are not available and the user needs setup instructions

## Setup Instructions

### One Command Install

From the **Unity project root** (the folder containing `Assets` and `ProjectSettings`):

```bash
npx aether-init
```

This does everything automatically:
- Downloads the Aether Bridge binary for the user's OS
- Installs the Unity SDK via UPM
- Writes `.cursor/mcp.json` so Cursor connects automatically

### After Install

1. **Reload Cursor:** Ctrl+Shift+P (or Cmd+Shift+P) → "Reload Window"
2. **Enter Play Mode** in Unity
3. **Ask a question:** e.g., "What's the state of my game?"

### Requirements

- Unity 2021.3 LTS or newer (including Unity 6)
- Node.js 18+ (for `npx`)
- Cursor with MCP support

### Windows SmartScreen

On first run, Windows may show a SmartScreen prompt for the bridge binary. Choose "More info" → "Run anyway." The binary is signed; this is a one-time prompt.

### Manual Setup

For users who prefer manual configuration, download the bridge from [getaether.dev/download](https://getaether.dev/download) and see the [Cursor MCP docs](https://docs.getaether.dev/docs/mcp/cursor) for manual `.cursor/mcp.json` configuration.

### Troubleshooting

- **"Tool not found" errors:** Run `npx aether-init` and reload Cursor.
- **Bridge not starting:** Check that the binary exists at `~/.aether/bin/` and that `.cursor/mcp.json` has the `aether` entry.
- **No data from Unity:** Make sure Unity is in Play Mode — the bridge needs a running game to capture state.
