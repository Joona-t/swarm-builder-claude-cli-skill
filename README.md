# Swarm Builder — Claude Code CLI Skill

A 15-agent orchestration skill for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) that builds, audits, and ships browser extensions using specialized AI agents with explicit scope boundaries and position-locked cross-feed.

## What It Does

Drop these files into your Claude Code setup and get 6 slash commands that deploy coordinated agent swarms:

| Command | What It Does | Agents |
|---------|-------------|--------|
| `/swarm-build new [cat] [name] [desc]` | Build a new extension from scratch | All 15 |
| `/swarm-build feature [ext] [desc]` | Add a feature to an existing extension | 10-12 |
| `/swarm-audit` | Full ecosystem audit across all extensions | All 15 |
| `/council-review [ext]` | Deep review of one extension | ~10 |
| `/ship-day [ext] [ver]` | Prepare extension for store release | 8-10 |
| `/brand-sweep` | Brand consistency check across ecosystem | ~5 |
| `/quick-fix [ext] [type]` | Targeted fix with 1-3 agents | 1-3 |

## Architecture

```
                         ┌──────────────────────┐
                         │    YOU (Orchestrator) │
                         └──────────┬───────────┘
                                    │
        ┌───────────┬───────────┬───┴───┬───────────┬───────────┐
        │           │           │       │           │           │
   CARMACK     HAMILTON      MATZ    RAUCH     KARPATHY     LINUS
   Perf/Arch   Reliability  Quality  UX/Brand  Intelligence Security
   (Opus)      (Opus)       (Opus)   (Opus)    (Opus)       (Opus)
        │           │           │       │           │           │
   perf-       security-   manifest- brand-   pattern-    (direct)
   analyzer    scanner     auditor   auditor  miner
   (Sonnet)    (Sonnet)    (Sonnet)  (Sonnet) (Sonnet)
               privacy-              asset-
               guardian              validator
               (Sonnet)             (Sonnet)

   UTILITY: memory-agent | store-prep
```

**15 agents total:** 6 Opus leads + 7 Sonnet specialists + 2 Sonnet utility

## Key Design Decisions

### OUT OF SCOPE Boundaries
Every agent has explicit negative scope — what they must NOT address. This prevents domain bleeding where parallel agents produce overlapping findings, causing "integrative compromise" (up to 37.6% quality loss per research).

### Position-Locked Cross-Feed
Leads produce independent analyses, then flag conflicts without changing their own conclusions. No forced consensus. Disagreements are preserved for human review.

### Why 15, Not 22
Ablation study (12 runs, 4 configs, 3 topics) proved 8 agents match 14-agent quality with higher actionability. Research briefs confirmed overlapping specialists waste tokens. 7 agents were merged into existing ones with zero coverage loss.

## 4-Wave Execution

1. **Wave 1 — Recon (Parallel):** 7 specialists scan and report simultaneously
2. **Wave 2 — Analysis (Position-Locked):** 6 leads analyze independently, then flag conflicts
3. **Wave 3 — Gate (Sequential):** Linus reviews everything, GO/NO-GO
4. **Wave 4 — Action (Sequential):** Fix issues, verify, ship

## Installation

```bash
# Copy commands to Claude Code
cp commands/*.md ~/.claude/commands/

# Copy AGENT-SWARM.md to your project root
cp AGENT-SWARM.md ~/your-project/

# Then in Claude Code:
/swarm-build new privacy link-cleaner "Strips tracking params from URLs"
/swarm-audit
/council-review my-extension
```

## Built For

Originally built for the [LoveSpark](https://github.com/Joona-t) browser extension suite — free, open-source, privacy-first productivity tools for neurodivergent coders. The architecture generalizes to any Claude Code project.

## Research-Backed

The 22→15 restructure was driven by the [Research Swarm](https://github.com/Joona-t/research-swarm) — a separate 8-agent AI research pipeline that produced 3 briefs on multi-agent orchestration, parallelism quality tradeoffs, and agent specialization. All changes are empirically motivated, not guesswork.

## License

MIT
