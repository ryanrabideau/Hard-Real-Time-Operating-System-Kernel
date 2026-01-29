# Memory Model

## Static & Deterministic Allocation
- No dynamic allocation (no malloc/free) in real-time paths
- Fixed task array: max 10 tasks (tasks[10])
- Per-task stack: 512 bytes embedded in TCB struct (static)
- Stack canaries: filled with 0xA5 pattern + sentinel at bottom
- Overflow detection: checked after each task step

## Why Static?
- Predictable memory usage (no fragmentation)
- Deterministic timing (no allocation latency)
- Safety: canary corruption = overflow detected & logged

## Stack Simulation
- Grows downward from top of array
- Pointer tracks current top
- Overflow if bottom sentinel (STACK_CANARY) overwritten

No heap and no dynamic pools. Everything compile-time or pre-init.
