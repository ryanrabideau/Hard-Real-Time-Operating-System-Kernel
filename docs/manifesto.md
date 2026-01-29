# Project Manifesto

This minimal RTOS project is all about building a tiny, predictable brain for time-critical tasks, simulated on my Linux desktop.  
We stick to strict rules: pure C11 code, no dynamic memory in hot paths, no threads or OS tricks. Just our own fake scheduling in a single loop.  
Out-of-scope: no multi-core, no hardware, no filesystems, no fancy GUIs.  

Why? Scope creep kills fun projects. This keeps us laser-focused on deterministic scheduling, IPC, and timing analysis, so I can test everything easily and learn kernel guts without headaches.
