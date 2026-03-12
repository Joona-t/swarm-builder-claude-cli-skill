# 🐝 LoveSpark Agent Swarm
> The Council evolved. 6 leads. 12 specialists. 4 utility agents. 22 minds, one mission.
> Drop this into any LoveSpark extension repo's `.claude/` directory.

---

## Architecture

```
                         ┌──────────────────────┐
                         │    YOU (Orchestrator) │
                         │  /swarm-audit         │
                         │  /swarm-build         │
                         │  /ship-day            │
                         │  /council-review      │
                         │  /brand-sweep         │
                         │  /quick-fix           │
                         └──────────┬───────────┘
                                    │
                    ┌───────────────┼───────────────┐
                    │         MEMORY-AGENT          │
                    │  session-memory.md             │
                    │  HANDOFF.md                    │
                    └───────────────┬───────────────┘
                                    │
        ┌───────────┬───────────┬───┴───┬───────────┬───────────┐
        │           │           │       │           │           │
   ⚡ CARMACK  🛡️ HAMILTON  🎨 MATZ  ✨ RAUCH  🤖 KARPATHY  💀 LINUS
   Performance  Reliability  Quality   UX/Brand  Intelligence  Security
   (Opus)       (Opus)       (Opus)    (Opus)    (Opus)        (Opus)
        │           │           │       │           │           │
   ┌────┴────┐ ┌────┴────┐ ┌───┴───┐ ┌─┴──┐  ┌────┴────┐ ┌───┴────┐
   │perf-    │ │error-   │ │dead-  │ │brand│  │pattern- │ │security│
   │profiler │ │scanner  │ │code-  │ │audit│  │miner    │ │scanner │
   │(Sonnet) │ │(Sonnet) │ │hunter │ │(Son)│  │(Sonnet) │ │(Sonnet)│
   │         │ │         │ │(Son)  │ │     │  │         │ │        │
   │bundle-  │ │privacy- │ │manif- │ │asset│  │docs-    │ │depend- │
   │analyzer │ │guardian │ │est-   │ │valid│  │generat- │ │ency-   │
   │(Sonnet) │ │(Sonnet) │ │valid  │ │(Son)│  │or       │ │auditor │
   └─────────┘ └─────────┘ │(Son)  │ └────┘  │(Sonnet) │ │(Sonnet)│
                            └───────┘         └─────────┘ └────────┘

   UTILITY LAYER: memory-agent | store-prep | cross-sync | changelog-writer
```

---

## The 22 Agents

### Tier 1: Council Leads (Opus) — Think, decide, sign off
| Agent | Role | Owns | Color |
|-------|------|------|-------|
| ⚡ carmack | Performance & Architecture | Startup time, SW lifecycle, storage speed, memory | Red |
| 🛡️ hamilton | Reliability & Data Safety | Error handling, storage integrity, graceful degradation | Blue |
| 🎨 matz | Code Quality & API Design | Naming, structure, dead code, readability | Green |
| ✨ rauch | UX & LoveSpark Brand | Popup UI, animations, brand system, store listings | Pink |
| 🤖 karpathy | Smart Features & Intelligence | Blocking heuristics, streak logic, bypass friction | Cyan |
| 💀 linus | Code Review & Security | Final GO/NO-GO, vulnerability review, permission audit | Yellow |

### Tier 2: Specialists (Sonnet) — Scan, measure, report
| Agent | Reports To | Task |
|-------|-----------|------|
| perf-profiler | Carmack | Measure load times, memory, CPU, bundle weight |
| bundle-analyzer | Carmack | Extension size, unused files, bloat detection |
| error-scanner | Hamilton | Find unhandled errors, missing try/catch, silent failures |
| privacy-guardian | Hamilton | Verify zero tracking, no outbound network, no analytics |
| dead-code-hunter | Matz | Unused functions, commented code, orphaned files |
| manifest-validator | Matz | Cross-extension manifest consistency |
| brand-auditor | Rauch | CSS variables, voice tone, state coverage, Sparky presence |
| asset-validator | Rauch | Icon sizes, screenshots, store asset completeness |
| pattern-miner | Karpathy | Cross-extension code pattern discovery |
| docs-generator | Karpathy | README, store listings, changelogs in LoveSpark voice |
| security-scanner | Linus | CSP, XSS, eval, permissions, injection vectors |
| dependency-auditor | Linus | Zero-dependency verification, no external scripts |

### Tier 3: Utility (Sonnet) — Coordinate, package, persist
| Agent | Task |
|-------|------|
| memory-agent | Session state, HANDOFF.md, continuity across sessions |
| store-prep | Package zips for Chrome/Firefox/Edge submission |
| cross-sync | Ecosystem-wide pattern consistency verification |
| changelog-writer | Generate CHANGELOG.md from code changes |

---

## Orchestration Commands

| Command | What It Does | Agents Deployed | Token Cost |
|---------|-------------|-----------------|------------|
| `/swarm-audit` | Full ecosystem audit, all extensions | All 22 | ~100-150k |
| `/ship-day [ext] [ver]` | Release one extension to stores | ~12-15 | ~50-80k |
| `/council-review [ext]` | Full council review, one extension | ~15 | ~60-90k |
| `/brand-sweep` | Brand consistency across all extensions | ~8 | ~30-50k |
| `/quick-fix [ext] [type]` | Targeted fix, 1-3 agents | 1-3 | ~10-20k |
| `/swarm-build new [cat] [name] [desc]` | Build new extension from scratch | All 22 | ~150-200k |
| `/swarm-build feature [ext] [desc]` | Build new feature for existing ext | ~15-18 | ~80-120k |

---

## Execution Waves

Every orchestration command follows the same wave pattern:

### Wave 1 — Recon (Parallel)
Specialist sub-agents scan and report. They do NOT fix anything.
All specialists in this wave run simultaneously for maximum speed.

### Wave 2 — Analysis (Parallel)
Council leads read specialist reports and produce their domain verdicts.
Council leads in this wave run simultaneously.

### Wave 3 — Gate (Sequential)
Linus reads everything. GO or NO-GO. Nothing ships without this.

### Wave 4 — Action (Sequential)
If fixes are needed, deploy the relevant council lead to fix.
Then re-run the relevant specialist to verify.

---

## Context Management

### The Memory Agent Protocol
1. **Deploy memory-agent FIRST** in every session
2. It reads `HANDOFF.md` and `session-memory.md` if they exist
3. It creates `session-memory.md` if it doesn't exist
4. Every agent reads session-memory before starting
5. Every agent writes results to session-memory after completing
6. memory-agent writes `HANDOFF.md` before session ends

### Context Overflow Protocol
When context gets heavy (>60% estimated):
1. Write current state to session-memory.md immediately
2. Complete the current atomic task — do not stop mid-function
3. Write HANDOFF.md with exact resume point
4. Stop cleanly — clean stop > messy continuation
5. New session starts: "Read HANDOFF.md and session-memory.md. Resume."

### Report File Discipline
All reports go to `_reports/` directory with predictable naming:
```
_reports/
├── perf-profile-[extension].md
├── errors-[extension].md
├── security-[extension].md
├── dead-code-[extension].md
├── brand-[extension].md
├── assets-[extension].md
├── privacy-[extension].md
├── bundle-[extension].md
├── deps-[extension].md
├── manifests-consistency.md
├── cross-sync-ecosystem.md
├── patterns-ecosystem.md
├── SWARM-AUDIT-[date].md
├── COUNCIL-REVIEW-[extension]-[date].md
├── BRAND-SWEEP-[date].md
├── SHIP-REPORT-[extension]-v[version].md
├── BUILD-RECON-[name]-[date].md
├── LINUS-GATE-[name]-[date].md
└── BUILD-REPORT-[name]-[date].md
```

---

## Model Tiering Strategy

| Tier | Model | Use For | Why |
|------|-------|---------|-----|
| Orchestrator | You (Opus) | Command interpretation, wave coordination, synthesis | Complex reasoning, judgment calls |
| Council Leads | Opus | Domain analysis, architectural decisions, verdicts | Need deep expertise and judgment |
| Specialists | Sonnet | Scanning, measuring, pattern matching, report generation | Mechanical tasks, cost-efficient |
| Utility | Sonnet | File management, packaging, documentation | Structured output, repeatable |

**Cost rule**: If the task is "find X in Y files" → Sonnet. If the task is "decide what to do about X" → Opus.

---

## The LoveSpark Extensions

| Extension | Code | Status | Key Domain |
|-----------|------|--------|------------|
| Anti Brainrot | AB | Shipped (Chrome, Firefox, Edge) | YouTube distraction blocking |
| LoveSpark AdBlock | LAdB | Shipped | Comprehensive ad blocking |
| I Don't Want Cookies | IDWC | Shipped | Cookie banner auto-rejection |
| Porn Blocker Rewire Brain | PBRB | Shipped | Content blocking + streak system |
| Focus Blossom | FB | In development | Site blocking + virtual garden |

---

## When To Deploy What

| Situation | Command | Why Not Bigger? |
|-----------|---------|-----------------|
| Shipping a new version | `/ship-day` | Focused pipeline, right agents for release |
| Something feels broken | `/quick-fix [ext] error` | Don't audit everything for one bug |
| Pre-launch full check | `/swarm-audit` | You want the comprehensive picture |
| "Does it all look LoveSpark?" | `/brand-sweep` | Brand-specific, skip perf/security |
| Deep dive on one extension | `/council-review [ext]` | All perspectives, one target |
| Just fixed a security concern | `/quick-fix [ext] security` | Linus + security-scanner, fast |
| Preparing store screenshots | `/quick-fix [ext] brand` | Rauch + brand-auditor only |
| Context from previous session | Read HANDOFF.md first | Don't re-audit, resume |
| Building a new extension | `/swarm-build new privacy my-ext "desc"` | Full design-then-build pipeline |
| Adding a feature to existing ext | `/swarm-build feature focus-blossom "desc"` | Analyzes existing code first |

---

## Installation

Copy the `.claude/` directory structure into any LoveSpark extension repo or into `~/.claude/` for global access:

```bash
# Global install (available in all projects)
cp -r .claude/agents/ ~/.claude/agents/
cp -r .claude/commands/ ~/.claude/commands/

# Or project-level (one repo)
cp -r .claude/ /path/to/extension/.claude/
```

Then in Claude Code:
```
/agents                    # See all available agents
/swarm-audit               # Deploy the full swarm
/swarm-build new privacy link-cleaner "Strips tracking params"
/ship-day anti-brainrot 1.1.0   # Ship a specific extension
/council-review porn-blocker     # Full council review
/brand-sweep               # Brand consistency check
/quick-fix focus-blossom perf    # Targeted fix
```

---

## 💖 The One Rule

> Does this empower users or exploit them?

Free tier stays genuinely useful. Pro adds real power. No dark patterns. No tracking. No attention extraction. This is not just ethics — it is the competitive advantage with the exact demographic LoveSpark serves.

---

*LoveSpark Agent Swarm — 22 agents, one ecosystem, zero compromises 🐝✨*
*Built in Finland, loved globally 🐰*
*Evolved from the Agent Council — March 2026*
