# Evaluation

## Current State

First validation run completed 2026-03-14: council-review on Anti-Brainrot extension, compared against stored baseline from 22-agent SWARM-AUDIT-2026-03-11.

### Measured Results (n=1)

| Metric | Old (22-agent) | New (15-agent) | Change |
|---|---|---|---|
| Specialists deployed | 12 | 7 | -42% |
| Unique findings | 18 | 27 | +50% |
| Findings per specialist | 1.5 | 3.86 | +157% |
| Cross-specialist overlap | 55% | 37.2% | -17.8pp |
| OUT OF SCOPE compliance | 0% (no blocks) | 86% (6/7) | New capability |
| CRITICAL findings caught | 0 | 1 | popup.js syntax corruption |
| Conflicts surfaced | 0 | 4 | Position-locked format works |
| Incorrect GO verdicts | 4 | 1 | -75% false positives |

**Caveat:** This is a single comparison against a stored baseline, not a controlled A/B test. The extension may have changed between audits. The old baseline had no OUT OF SCOPE blocks, so the overlap reduction reflects both fewer agents and better scoping.

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
4. **Gate effectiveness:** Frequency and accuracy of Linus Gate NO-GO decisions — *partially measured: 1 NO-GO issued on Anti-Brainrot, correctly identified a broken popup*
5. **Scope boundary effectiveness:** Whether agents stay within declared scope — *measured: 86% compliance (6/7 specialists) in first test*
6. **Coverage completeness:** Whether the 15 agents cover all aspects of extension development — *measured: structural coverage gap analysis found 0 gaps, live test found +50% more findings than old config*

## What Has Been Measured (2026-03-14)

Full experiment report: `experiment-results.md` in the LoveSpark project root.
Detailed council review: `_reports/COUNCIL-REVIEW-anti-brainrot-2026-03-14.md`
Supporting reports: `_reports/structural-verification-2026-03-14.md`, `_reports/coverage-gap-analysis-2026-03-14.md`
