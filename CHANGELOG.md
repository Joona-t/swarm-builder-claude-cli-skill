# Changelog

## [2.0.0] — 2026-03-14

### Restructured: 22 → 15 Agents

**Merged 7 overlapping specialists:**

| Removed | Absorbed Into | Reason |
|---------|--------------|--------|
| `bundle-analyzer` | `perf-analyzer` | Both measure extension weight/speed/bloat |
| `error-scanner` | `security-scanner` | Error patterns and vulnerabilities overlap |
| `dead-code-hunter` | `perf-analyzer` | Unused files are a perf/bloat concern |
| `docs-generator` | Wave 4 (build phase only) | No docs needed before design exists |
| `changelog-writer` | Wave 4 (build phase only) | Same — build-phase only |
| `cross-sync` | `pattern-miner` | Both do cross-extension analysis |
| `dependency-auditor` | `manifest-auditor` | Both check manifest + deps |

### Added: OUT OF SCOPE Boundaries

Every agent (6 leads + 7 specialists) now has explicit negative scope defining what they must NOT address. Prevents domain bleeding and integrative compromise.

### Changed: Position-Locked Cross-Feed

- **Before:** Leads read all peer output, "resolve conflicts", forced to converge in Round 3
- **After:** Leads read peer conclusions only, flag conflicts but don't change their own recommendations. Round 3 removed. Disagreements preserved for human review.

### Changed: Wave 2 Structure

- Round 1: Independent analysis (unchanged)
- Round 2: Conflict detection only (was: full cross-feed with consensus-seeking)
- Round 3: Removed (was: forced convergence)

### Updated: All 6 Commands

All slash commands updated from "22 agents" to "15 agents" with references to merged agents removed:
- `swarm-build.md`
- `swarm-audit.md`
- `brand-sweep.md`
- `council-review.md`
- `ship-day.md`
- `quick-fix.md`

### Updated: Token Cost Estimates

| Command | Before | After |
|---------|--------|-------|
| `/swarm-build new` | ~150-200k | ~100-140k |
| `/swarm-audit` | ~100-150k | ~60-100k |
| `/council-review` | ~60-90k | ~40-60k |
| `/ship-day` | ~50-80k | ~40-60k |
| `/brand-sweep` | ~30-50k | ~20-35k |

### Research Basis

Changes driven by 3 research swarm briefs (runs 38-40):
1. "Multi-agent orchestration cost optimization" — sufficiency gates, scope injection, cost routing
2. "Parallel vs sequential agent pipelines" — position-lock anchoring, consensus-free synthesis, DAG execution
3. "Agent role specialization vs generalist agents" — empirical data on specialist overlap

Plus own ablation study (runs 20-31): 8 agents matched 14-agent quality (6.1 vs 5.9 avg) with higher actionability (5.3 vs 4.3).

---

## [1.0.0] — 2026-03-12

### Initial Release

- 22-agent swarm (6 Opus leads + 12 Sonnet specialists + 4 Sonnet utility)
- 4-wave execution pattern (Recon → Analysis → Gate → Action)
- 6 slash commands: swarm-build, swarm-audit, council-review, ship-day, brand-sweep, quick-fix
- Memory agent protocol with HANDOFF.md for session continuity
- Built for LoveSpark browser extension ecosystem
