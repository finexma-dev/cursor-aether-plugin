---
name: aether-crash-investigation
description: Investigate Unity crashes, NullReferenceExceptions, and runtime exceptions. Use when the user hits a crash in Play Mode, reports a null ref, or asks why their game threw an exception.
---

# Crash Investigation

## When to Use

- User reports a crash, freeze, or unhandled exception in Unity
- NullReferenceException, MissingReferenceException, or similar runtime error
- User asks "why did my game crash?", "what caused this exception?", or "what was happening when it broke?"

## Workflow

1. **Get the causal chain:** Start with `aether_last_run_answer` — ask it what led to the crash. It returns a timeline with suspects and receipts.
2. **Search logs:** Use `aether_console` with `level: "error"` or `level: "exception"` to find the exact error messages and stack traces.
3. **Check state at crash time:** Use `aether_tail` with a short window (5–10s) to see what events and state changes happened right before the crash.
4. **Inspect the object:** If a specific GameObject is implicated, use `aether_snapshot` to check its current state (or last known state).
5. **Identify root cause:** Cross-reference the timeline, logs, and state to pinpoint the bug. Look for `[ISSUE: ...]` tags in GTML output.

## Key Tools

| Tool | Role in crash investigation |
|------|----------------------------|
| `aether_last_run_answer` | Primary — causal chain with suspects and receipts |
| `aether_console` | Search for error/exception logs with stack traces |
| `aether_tail` | Timeline of events leading up to the crash |
| `aether_snapshot` | State of implicated GameObjects |

## Tips

- If `aether_last_run_answer` returns suspects with confidence scores, focus on the highest-confidence suspect first.
- NullReferenceExceptions often trace back to destroyed objects or uninitialized references — check `aether_snapshot` for missing component refs.
- For intermittent crashes, ask the user to reproduce and then immediately query `aether_tail` for the last 10 seconds.
