---
name: aether-verification
description: Verify that a code fix actually resolved the bug. Use when the user asks "did my fix work?", wants to compare before and after, or needs to check for regressions after making changes.
---

# Fix Verification

## When to Use

- User made a code change and wants to confirm it fixed the bug
- User asks "did that fix it?", "is it working now?", or "can you check if the bug is gone?"
- User wants before/after comparison of game state
- User is concerned about regressions from a recent change

## Workflow

1. **Ask the user to enter Play Mode** after their code change.
2. **Snapshot current state:** Use `aether_snapshot` to capture the state of the previously-buggy GameObject or system.
3. **Check recent events:** Use `aether_tail` with a short window (5–10s) to see if the problematic event pattern has stopped.
4. **Search for the original error:** Use `aether_console` with a text filter matching the original error message — if no results, the fix is working.
5. **Compare:** Contrast the new state/events with what was observed before the fix. Report whether the issue is resolved or persists.

## Key Tools

| Tool | Role in verification |
|------|---------------------|
| `aether_snapshot` | Current state of the fixed object/system |
| `aether_tail` | Recent events — check if bad pattern stopped |
| `aether_console` | Search for the original error (absence = fix works) |

## Tips

- Always ask the user to reproduce the original trigger (e.g., "jump again", "walk into the wall") before checking — a fix isn't verified until the trigger no longer causes the bug.
- If the original error still appears in `aether_console`, the fix didn't work — suggest further investigation with `aether_last_run_answer`.
- For regressions, compare the current `aether_tail` output against the expected behavior — new warnings or errors that weren't there before indicate a regression.
