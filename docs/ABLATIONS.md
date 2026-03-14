# Ablations

## The 22→15 Restructure (v1.0 → v2.0)

This was the only major architectural change, and it was driven by external research, not internal measurement.

### 7 Agent Merges

| Removed | Merged Into | Hypothesis | Result |
|---------|-------------|------------|--------|
| bundle-analyzer | perf-analyzer | Both measure extension weight/speed — redundant scope | Merged. Not independently validated. |
| error-scanner | security-scanner | Error patterns and vulnerabilities overlap | Merged. Not independently validated. |
| dead-code-hunter | perf-analyzer | Unused files are a perf concern | Merged. Not independently validated. |
| docs-generator | Wave 4 | Docs before design is wasteful | Moved to build phase only. |
| changelog-writer | Wave 4 | Same reasoning | Moved to build phase only. |
| cross-sync | pattern-miner | Both do cross-extension analysis | Merged. Not independently validated. |
| dependency-auditor | manifest-auditor | Both check manifest + deps | Merged. Not independently validated. |

**Evidence basis:** Research Swarm ablation (12 runs) showed 8 agents matched 14-agent quality. Research brief on agent specialization confirmed overlapping specialists waste tokens. These findings are from a different pipeline (research automation, not extension building).

**What is NOT known:** Whether these specific 7 merges maintain full coverage for browser extension development. No before/after comparison of extension build quality was conducted.

### Cross-Feed Protocol Change

| Aspect | v1.0 | v2.0 |
|--------|------|------|
| Round 1 | Independent analysis | Independent analysis (unchanged) |
| Round 2 | Full cross-feed with consensus-seeking | Conflict detection only |
| Round 3 | Forced convergence | Removed |

**Evidence basis:** Research Swarm brief on parallel vs sequential pipelines found forced consensus degrades output.

**What is NOT known:** Whether position-locked cross-feed produces better extension architecture recommendations than forced consensus. No measurement exists.

### Token Cost Reduction

Estimated 20-30% token reduction from v1.0 to v2.0 based on agent count reduction (22→15). Not measured from actual runs.
