---
name: aether-performance
description: Diagnose Unity performance issues like frame drops, stuttering, and slow gameplay. Use when the user reports low FPS, hitches, lag spikes, or asks why their game is running slowly.
---

# Performance Diagnosis

## When to Use

- User reports frame drops, stuttering, or low FPS
- User asks "why is my game so slow?", "what's causing the lag?", or "why does it hitch when I do X?"
- User notices gameplay feels sluggish or unresponsive

## Workflow

1. **Get recent timeline:** Use `aether_tail` with a 10–30s window to capture frame timing data, events, and state changes during the slow period.
2. **Snapshot the scene:** Use `aether_snapshot` to see the current scene state — object count, active components, physics bodies.
3. **Search for warnings:** Use `aether_console` with `level: "warning"` to find Unity performance warnings (e.g., "%.2fms frame time", GC allocation warnings).
4. **Identify hot spots:** Look for patterns in the timeline — repeated events, rapid state changes, or expensive operations happening every frame.
5. **Recommend fixes:** Based on findings, suggest specific optimizations (object pooling, reducing physics bodies, disabling unnecessary components, etc.).

## Key Tools

| Tool | Role in performance diagnosis |
|------|-------------------------------|
| `aether_tail` | Primary — frame timing, event frequency, state change volume |
| `aether_snapshot` | Scene complexity, active object count, component state |
| `aether_console` | Unity performance warnings and GC logs |

## Tips

- High event frequency in `aether_tail` often points to per-frame operations that should be throttled.
- If `aether_snapshot` shows many active physics bodies, suggest reducing Rigidbody count or using layers to limit collision checks.
- Look for GC allocation patterns in console logs — frequent allocations cause frame hitches.
