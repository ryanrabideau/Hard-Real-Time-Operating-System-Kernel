# Schedulability Analysis (Rate Monotonic)

## Task Set
- Task 1 (prio 3): period ~50 ticks, WCET measured 20–40 ticks
- Task 2 (prio 8): period ~100 ticks (assumed), WCET ~8 ticks
- Task 3 (prio 15): period ~150 ticks (assumed), WCET ~6 ticks

## Liu & Layland Utilization Bound
n = 3 → bound = 3 × (2^(1/3) - 1) ≈ 0.7797 (78%)

Measured U ≈ (30/50) + (8/100) + (6/150) = 0.72 (72%)

U < bound → schedulable.

## Worst-Case Response Time (Joseph & Pandya)
R1 ≈ WCET1 = 30 ticks  
R2 ≈ WCET2 + ceiling(R2 / P1) × WCET1 ≈ 8 + 1×30 = 38 ticks  
R3 ≈ WCET3 + ceiling(R3 / P1) × WCET1 + ceiling(R3 / P2) × WCET2 ≈ 6 + 1×30 + 1×8 = 44 ticks

All R_i < period_i → schedulable.

## Conclusion
System is schedulable with margin. Measured WCET higher than assumed → add safety margin in real systems.
