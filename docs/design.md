# Kernel Design Doc

## What is a Task?
A task is a small, independent unit of work — a function pointer that runs periodically or on demand. Each has an ID, priority, state, timing parameters, and entry point.

## Task States
- READY: Eligible to run when scheduler chooses it
- RUNNING: Currently executing
- BLOCKED: Waiting on a resource (e.g., mutex)
- SUSPENDED: Manually paused (not used yet)
- DEAD: Terminated (cleanup possible)

## What Causes a Context Switch?
- Higher-priority task becomes READY (preemption)
- Current task yields (cooperative)
- Current task blocks (e.g., mutex wait)
- Deadline or watchdog forces intervention

## How is Time Represented?
Global `system_ticks` counter, incremented by `kernel_tick()` each loop iteration. Tasks use relative periods/deadlines in ticks.

## Scheduler Guarantees
- Highest-priority READY task always runs (fixed-priority)
- Preemptive: higher prio interrupts lower
- Deterministic: no randomness, no threads
- Detects violations (deadline misses, stalls) and logs them

## Kernel Responsibilities
- Schedule tasks based on priority
- Manage time (ticks, releases)
- Handle IPC (mutexes with inheritance)
- Detect and log faults (misses, overflows, stalls)
