# 🐝 LoveSpark Agent Swarm
> Leaner, meaner, measured. 6 leads. 7 specialists. 2 utility. 15 agents, zero overlap.
> Evolved from 22→15 based on ablation data + 3 research briefs (runs 38-40).

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
   ┌────┴────┐ ┌────┴────┐ ┌───┴────┐ ┌─┴──┐  ┌────┴────┐ ┌───┴────┐
   │perf-    │ │security-│ │manif-  │ │brand│  │pattern- │ │(direct)│
   │analyzer │ │scanner  │ │est-    │ │audit│  │miner    │ │        │
   │(Sonnet) │ │(Sonnet) │ │auditor │ │(Son)│  │(Sonnet) │ │        │
   │         │ │         │ │(Son)   │ │     │  │         │ │        │
   │         │ │privacy- │ │        │ │asset│  │         │ │        │
   │         │ │guardian │ │        │ │valid│  │         │ │        │
   │         │ │(Sonnet) │ │        │ │(Son)│  │         │ │        │
   └─────────┘ └─────────┘ └────────┘ └────┘  └─────────┘ └────────┘

   UTILITY: memory-agent | store-prep
```

---

## Why 15, Not 22

Ablation study (12 runs, 4 configs, 3 topics) proved **8 agents match 14-agent quality** with higher actionability. Research briefs (runs 38-40) confirmed overlapping specialists cause domain bleeding and integrative compromise.

**Merges applied:**
| Removed | Absorbed Into | Reason |
|---|---|---|
| `bundle-analyzer` | `perf-analyzer` | Both measure extension weight/speed/bloat |
| `error-scanner` | `security-scanner` | Error patterns and vulnerabilities overlap |
| `dead-code-hunter` | `perf-analyzer` | Unused files are a perf/bloat concern |
| `docs-generator` | Wave 4 only (docs-writer) | No docs needed before design exists |
| `changelog-writer` | Wave 4 only (docs-writer) | Same — build-phase only |
| `cross-sync` | `pattern-miner` | Both do cross-extension analysis |
| `dependency-auditor` | `manifest-auditor` | Both check manifest + deps |

---

## The 15 Agents

### Tier 1: Council Leads (Opus) — Think, decide, sign off

| Agent | Role | Owns | Color |
|-------|------|------|-------|
| ⚡ carmack | Performance & Architecture | Startup time, SW lifecycle, storage speed, memory | Red |
| 🛡️ hamilton | Reliability & Data Safety | Error handling, storage integrity, graceful degradation | Blue |
| 🎨 matz | Code Quality & API Design | Naming, structure, dead code, readability | Green |
| ✨ rauch | UX & LoveSpark Brand | Popup UI, animations, brand system, store listings | Pink |
| 🤖 karpathy | Smart Features & Intelligence | Blocking heuristics, streak logic, bypass friction | Cyan |
| 💀 linus | Code Review & Security | Final GO/NO-GO, vulnerability review, permission audit | Yellow |

#### Lead Scope Boundaries

Each lead MUST include these boundaries in their analysis. Do NOT address out-of-scope topics.

**⚡ Carmack**
- YOUR DOMAIN: Architecture, data flow, storage schema, SW lifecycle, performance, memory usage, startup time
- OUT OF SCOPE: UI layout, brand voice, security policy, documentation tone, naming conventions

**🛡️ Hamilton**
- YOUR DOMAIN: Error handling, graceful degradation, storage integrity, edge cases, data safety
- OUT OF SCOPE: Performance optimization, UI design, naming conventions, brand voice, algorithm design

**🎨 Matz**
- YOUR DOMAIN: File structure, naming, module boundaries, API design, readability, code conventions
- OUT OF SCOPE: Performance tuning, security policy, UI/UX layout, algorithm design, brand voice

**✨ Rauch**
- YOUR DOMAIN: Popup UI, animations, brand system, store listings, accessibility, theme integration
- OUT OF SCOPE: Architecture decisions, error handling strategy, security policy, algorithm design

**🤖 Karpathy**
- YOUR DOMAIN: Core algorithms, heuristics, detection logic, blocking strategies, smart features
- OUT OF SCOPE: UI design, naming conventions, store listings, file structure, error handling patterns

**💀 Linus**
- YOUR DOMAIN: Security, CSP, permission audit, vulnerability review, GO/NO-GO gate
- OUT OF SCOPE: Performance optimization, UI design, algorithm design, brand voice, naming style

---

### Tier 2: Specialists (Sonnet) — Scan, measure, report

| Agent | Reports To | Task | Domain | OUT OF SCOPE |
|-------|-----------|------|--------|-------------|
| perf-analyzer | Carmack | Measure load times, memory, CPU, bundle weight, unused files/code | Performance, bundle size, dead code | Security vulns, UI/brand, privacy flows, naming |
| security-scanner | Hamilton + Linus | CSP, XSS, eval, injection, unhandled errors, permissions, silent failures | Security, error patterns, vulnerabilities | Performance metrics, brand, documentation, UI |
| privacy-guardian | Hamilton | Verify zero tracking, no outbound network, no analytics, data flow mapping | Privacy, data flows, tracking | Performance, security vulns, code quality, brand |
| brand-auditor | Rauch | CSS variables, voice tone, Sparky presence, theme coverage, state coverage | Brand consistency, visual design | Performance, security, manifest, code structure |
| asset-validator | Rauch | Icon sizes, screenshots, store asset completeness | Asset inventory, store readiness | Code quality, security, performance, architecture |
| pattern-miner | Karpathy | Cross-extension patterns, reusable code, ecosystem consistency, naming conflicts | Code patterns, ecosystem sync | Security, performance metrics, brand voice, UI |
| manifest-auditor | Matz + Linus | Manifest fields, permissions, dependencies, version consistency, zero external deps | Manifest, deps, permissions | UI design, performance profiling, brand, algorithms |

---

### Tier 3: Utility (Sonnet) — Coordinate, package

| Agent | Task |
|-------|------|
| memory-agent | Session state, HANDOFF.md, continuity across sessions |
| store-prep | Package zips for Chrome/Firefox/Edge submission |

---

## Orchestration Commands

| Command | What It Does | Agents Deployed | Token Cost |
|---------|-------------|-----------------|------------|
| `/swarm-audit` | Full ecosystem audit, all extensions | All 15 | ~60-100k |
| `/ship-day [ext] [ver]` | Release one extension to stores | ~8-10 | ~40-60k |
| `/council-review [ext]` | Full council review, one extension | ~10 | ~40-60k |
| `/brand-sweep` | Brand consistency across all extensions | ~5 | ~20-35k |
| `/quick-fix [ext] [type]` | Targeted fix, 1-3 agents | 1-3 | ~10-20k |
| `/swarm-build new [cat] [name] [desc]` | Build new extension from scratch | All 15 | ~100-140k |
| `/swarm-build feature [ext] [desc]` | Build new feature for existing ext | ~10-12 | ~60-80k |

---

## Execution Waves

Every orchestration command follows the same wave pattern:

### Wave 1 — Recon (Parallel)
All 7 specialists scan and report simultaneously. They do NOT fix anything.
Each specialist stays within their OUT OF SCOPE boundaries.

### Wave 2 — Analysis (Position-Locked)

#### Round 1 — Independent Analysis (Parallel)
Each lead reads specialist reports and produces their FULL domain analysis independently.
Leads stay within their OUT OF SCOPE boundaries.

#### Round 2 — Conflict Detection (Parallel)
Each lead reads peer **conclusions only** (not full output). They:
- Flag CONFLICTS but do NOT change their own conclusions
- Output format per lead:
  - **My recommendation:** [unchanged from Round 1]
  - **My confidence:** [0.0-1.0]
  - **Conflicts with:** [list of leads and specific disagreements]
  - **Trade-off note:** [why this conflict exists and what the trade-off is]

**No Round 3.** Disagreements are preserved, not resolved by agents.

#### Assembly
Combine all lead sections into `plan.md`. Include a **Conflicts** section listing all disagreements with both sides' reasoning. The human resolves conflicts during annotation.

### Wave 3 — Gate (Sequential)
Linus reads everything. GO or NO-GO. Nothing ships without this.

### Wave 4 — Action (Sequential)
If fixes are needed, deploy the relevant council lead to fix.
Then re-run the relevant specialist to verify.
Documentation (README, CHANGELOG, store listing) is generated here by the orchestrator, not by a separate docs agent.

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
├── perf-[extension].md
├── security-[extension].md
├── privacy-[extension].md
├── brand-[extension].md
├── assets-[extension].md
├── patterns-ecosystem.md
├── manifests-[extension].md
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
| Utility | Sonnet | File management, packaging | Structured output, repeatable |

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

*LoveSpark Agent Swarm — 15 agents, zero overlap, measured improvements 🐝✨*
*Built in Finland, loved globally 🐰*
*Evolved: 22→15 agents based on ablation data + research (March 2026)*
