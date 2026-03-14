# Claims and Evidence

## Design Claims

### "OUT OF SCOPE boundaries prevent domain bleeding"
- **Evidence:** Research Swarm overlap reduction (76% → 38%) after adding scope boundaries (different pipeline)
- **Strength:** Moderate (for Research Swarm), Weak (for this system — not independently tested)
- **Caveats:** Research Swarm uses different agents for a different task. Transfer to extension development is a reasonable bet, not a proven result.

### "Position-locked cross-feed preserves more information than forced consensus"
- **Evidence:** Research Swarm brief on parallel vs sequential pipelines (run 39)
- **Strength:** Weak — the brief describes the problem theoretically. No measurement of information loss in either v1.0 or v2.0 of this system.
- **Caveats:** v1.0 was never evaluated before being replaced, so no before/after comparison exists.

### "7 agents were merged with zero coverage loss"
- **Evidence:** Qualitative assessment during restructure. No coverage measurement.
- **Strength:** Weak — "zero coverage loss" is a claim, not a measured result.
- **Caveats:** Coverage was assessed by reviewing agent scope definitions, not by running comparative builds.

### "Integrative compromise causes up to 37.6% quality loss"
- **Evidence:** Research Swarm brief citing multi-agent literature (not own measurement)
- **Strength:** Weak — this is a number from a secondary source in a research brief, not from a controlled experiment in this codebase.
- **Caveats:** The 37.6% figure should be attributed to its original source, not presented as an own finding.

## Cost Claims

### "Token costs reduced 20-30% from v1.0 to v2.0"
- **Evidence:** Agent count reduction (22→15). Token estimates in CHANGELOG.md.
- **Strength:** Moderate — proportional reduction in agents should reduce tokens proportionally.
- **Caveats:** Estimates, not measurements. Actual token usage may differ due to prompt complexity and output length.

### "Research Swarm ablation: 8 agents matched 14-agent quality (6.1 vs 5.9)"
- **Evidence:** Research Swarm metrics.jsonl, 12-run ablation
- **Strength:** Moderate (for Research Swarm) — small sample, single evaluator
- **Caveats:** This is Research Swarm's finding. Agent roles, tasks, and evaluation criteria differ between that system and this one.
