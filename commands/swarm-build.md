You are the full LoveSpark Agent Swarm (22 agents). Follow AGENT-SWARM.md exactly.

Build a new extension or feature using the swarm in design-and-implement mode.

**Arguments:** $ARGUMENTS

Parse the first word as mode: `new` or `feature`.
- `new [category] [name] [description]` — Build a new extension from scratch.
- `feature [extension] [feature-description]` — Add a feature to an existing extension.

Categories: privacy | neurodivergent | reading | themes | productivity | games | full-power

---

## Pre-Build — Memory Agent

Deploy memory-agent FIRST. Read:
- `HANDOFF.md` and `session-memory.md` (if they exist)
- `~/.claude/docs/memory/known-issues.md`
- `~/.claude/docs/memory/color-decisions.md`
- `~/.claude/docs/memory/debugging.md`

---

## Wave 1 — Research (Parallel Specialists)

All 12 specialists gather context simultaneously. They do NOT build anything.

| Specialist | Build Mode Task |
|---|---|
| perf-profiler | Profile similar extensions for perf baselines |
| bundle-analyzer | Inventory reusable assets from shared lib; set weight budget |
| error-scanner | Survey error patterns in similar extensions |
| privacy-guardian | Map all data flows the new build touches; flag risks |
| dead-code-hunter | Find reusable code in existing extensions |
| manifest-validator | Generate manifest template from required permissions |
| brand-auditor | Produce brand checklist: Sparky, `--ls-bg-gradient`, themes, messages |
| asset-validator | List all assets needed; check what already exists |
| pattern-miner | Find closest reference extension; extract reusable patterns |
| docs-generator | Draft README + store listing stub in LoveSpark voice |
| security-scanner | Produce security requirements: CSP, permission justification |
| dependency-auditor | Confirm shared lib versions; verify zero external deps |

Utility agents deploy alongside:
- `memory-agent`: Loads known-issues, color-decisions, debugging context
- `cross-sync`: Checks naming conflicts + duplicate functionality in ecosystem

**`feature` mode extra:** pattern-miner, error-scanner, and brand-auditor additionally analyze the target extension's existing codebase.

**Output:** `research.md` + individual reports in `_reports/BUILD-RECON-[name]-[date].md`

---

## Wave 2 — Iterative Design (Council Leads, Multi-Round)

### Round 1 — Initial Design (Parallel)
Each lead reads Wave 1 reports + their context modules:

| Lead | Produces | Reads |
|---|---|---|
| Carmack | Architecture, data flow, storage schema, SW lifecycle | `architecture.md` |
| Hamilton | Error handling strategy, graceful degradation, edge cases | `debugging.md` |
| Matz | File structure, naming, module boundaries, API design | — |
| Rauch | UI/UX layout, popup design, theme integration, accessibility | `brand.md`, `components.md`, `themes.md`, `accessibility-framework.md` |
| Karpathy | Core algorithm, heuristics, detection/blocking strategies | — |
| Linus | Security requirements, CSP policy, permission audit | `known-issues.md` |

### Round 2 — Cross-Feed (Parallel)
Each lead reads ALL other leads' Round 1 output. They:
- Identify conflicts (e.g., Carmack's perf constraint vs Rauch's animation plan)
- Resolve dependencies (e.g., Karpathy's algorithm needs Hamilton's error boundaries)
- Refine their section based on the full picture

### Round 3 — Alignment (if conflicts remain)
Only leads with unresolved conflicts iterate one more time. Others hold.

**Assembly:** Combine all lead sections into `plan.md` with a granular TODO checklist. Each section attributed to its lead.

**Output:** `plan.md` with architecture, reliability, code structure, UI/UX, logic, and security sections.

---

## Wave 3 — Linus Gate (Sequential)

Linus reviews the complete `plan.md` against hard constraints:
- Permission minimality — every permission has a justified API call
- Privacy compliance — zero outbound network, zero data collection
- No `innerHTML`, no `eval`, no external CDN links
- CSP policy present and restrictive
- Message handler validation (`sender.id` check)
- Storage API consistency (all local, not mixed sync/local)
- No `setInterval` for DOM watching
- Every KI from `known-issues.md` addressed

**Output:** `_reports/LINUS-GATE-[name]-[date].md` with GO/NO-GO.

---

## ⛔ HARD STOP

> **Plan complete. Do not implement yet.**
> Review plan.md, add annotations, and say "implement it all" when ready.

If session ends here, memory-agent writes HANDOFF.md with resume point.

---

## Wave 4 — Build (After "implement it all")

Non-overlapping file scopes to avoid conflicts:

| Agent Group | File Scope |
|---|---|
| Carmack + perf-profiler | `background.js`, `content.js` — core logic |
| Rauch + brand-auditor + asset-validator | `popup.html`, `popup.css`, `popup.js`, icons, mascot |
| Hamilton + error-scanner | Error handling wrappers, storage migration |
| Matz + manifest-validator | `manifest.json`, file structure, naming |
| Karpathy + pattern-miner | Core algorithm files, feature logic |
| docs-generator + changelog-writer | README.md, CHANGELOG.md, store listing |

**`new` mode:** Run `scaffold-extension.py --name [name] --category [category] --features stats,theme,toggle` first, then customize.

**`feature` mode:** Skip scaffold. Run `bump-version.sh` after changes.

### Post-Build
- `store-prep` generates Chrome + Firefox zips via `build-zips.sh`
- Run `audit-contrast.py --verbose --history`
- Run `audit-permissions.sh`
- Linus + security-scanner do final verification pass
- `memory-agent` writes session-memory.md + HANDOFF.md
- Output: `_reports/BUILD-REPORT-[name]-[date].md`
- Run `/postmortem`

---

## Rules
- Always reference AGENT-SWARM.md for agent roles and colors.
- Every specialist and lead must think in their exact domain.
- Stay 100% aligned with "The One Rule": empower users, never exploit.
- `known-issues.md` entries are hard constraints — not suggestions.
- Report naming: `BUILD-RECON-[name]-[date].md`, `LINUS-GATE-[name]-[date].md`, `BUILD-REPORT-[name]-[date].md`

Begin now.
