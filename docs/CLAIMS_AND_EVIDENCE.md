# Claims and Evidence

## Design Claims

### "OUT OF SCOPE boundaries prevent domain bleeding"
- **Evidence:** Research Swarm overlap reduction (76% → 38%) after adding scope boundaries (different pipeline). Additionally, council-review experiment on Anti-Brainrot (2026-03-14) measured 6/7 specialists fully compliant with scope boundaries, 1/7 partial overstep. Specialist overlap dropped from 55% (old 22-agent, no boundaries) to 37.2% (new 15-agent, with boundaries).
- **Strength:** Moderate — now validated in this system with one live test
- **Caveats:** Single extension test (Anti-Brainrot). The remaining 37.2% overlap is largely cross-domain findings that legitimately appear in multiple specialist domains. n=1 for this system.

### "Position-locked cross-feed preserves more information than forced consensus"
- **Evidence:** Research Swarm brief on parallel vs sequential pipelines (run 39). Additionally, council-review experiment (2026-03-14) surfaced 4 explicit conflicts between leads using position-locked format. Old 22-agent config with forced consensus surfaced 0 conflicts on the same extension. The 4 conflicts revealed a legitimate scope disagreement (Karpathy GO vs Hamilton/Linus NO-GO) that would have been averaged into a false CONDITIONAL under the old protocol.
- **Strength:** Moderate — one live test demonstrates the mechanism works as designed
- **Caveats:** v1.0 was never evaluated before being replaced, so the comparison is against stored baseline data, not a parallel A/B run. n=1.

### "7 agents were merged with zero coverage loss"
- **Evidence:** Qualitative assessment during restructure confirmed by systematic coverage gap analysis (2026-03-14). Every domain from 7 removed agents was mapped to a surviving agent with specific evidence from AGENT-SWARM.md line references. In one case (external CDN detection), coverage improved from 1 agent to 3. Council-review experiment found 27 unique findings vs 18 in old audit — +50% more findings with 42% fewer specialists.
- **Strength:** Moderate — structural analysis complete, one live test confirms coverage maintained
- **Caveats:** Coverage gap analysis is structural (checking definitions), not empirical (running both configs on identical inputs). The +50% finding increase may partially reflect extension changes since the old audit.

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
