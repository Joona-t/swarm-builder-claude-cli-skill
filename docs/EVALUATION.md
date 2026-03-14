# Evaluation

## Current State

No evaluation framework exists for this system. There are no quality metrics, no scoring rubrics, and no run data.

## Token Cost Estimates (Not Measured)

These estimates are from documentation, not from actual tracked runs:

| Command | Estimated Tokens (v2.0) | Estimated Tokens (v1.0) | Reduction |
|---------|------------------------|------------------------|-----------|
| `/swarm-build new` | ~100-140k | ~150-200k | ~30% |
| `/swarm-audit` | ~60-100k | ~100-150k | ~33% |
| `/council-review` | ~40-60k | ~60-90k | ~33% |
| `/ship-day` | ~40-60k | ~50-80k | ~20% |
| `/brand-sweep` | ~20-35k | ~30-50k | ~30% |

**Caveat:** These are estimates based on agent count and expected prompt/response sizes. Actual token usage has not been measured.

## What Would Need to Be Measured

1. **Build quality:** Human review of swarm-assisted extension builds, scored on correctness, completeness, and code quality
2. **Defect rate:** Bugs found after initial build vs. manual development
3. **Token cost:** Actual API costs per command
4. **Gate effectiveness:** Frequency and accuracy of Linus Gate NO-GO decisions
5. **Scope boundary effectiveness:** Whether agents stay within declared scope
6. **Coverage completeness:** Whether the 15 agents cover all aspects of extension development
