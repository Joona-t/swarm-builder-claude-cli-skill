# Methodology

## How This System Was Developed

Unlike Research Swarm (which has its own evaluation pipeline), Swarm Builder was developed through a research-then-apply cycle:

1. **Research phase:** Research Swarm ran 40 topics on multi-agent design, producing briefs on orchestration, parallelism, specialization, and cost optimization.
2. **Design phase:** Briefs from runs 38-40 directly informed the v2.0 restructure (22→15 agents, scope boundaries, position-locked cross-feed).
3. **Ablation reference:** Research Swarm's 12-run ablation (4 configs, 3 topics) provided the evidence for agent count optimization.

## What Was NOT Done

- No A/B testing of v1.0 vs v2.0 on identical extension builds
- No measurement of output quality, build time, or defect rates
- No user study or external validation
- No token cost tracking for actual swarm runs

## Variables

### Design Variables (Changed in v2.0)
- Agent count: 22 → 15
- Cross-feed protocol: forced consensus → position-locked
- Scope boundaries: implicit → explicit OUT OF SCOPE
- Wave 2 rounds: 3 → 2

### What Would Need to Be Measured (Future Work)
- Output quality per command (scored by human review)
- Build defect rate (bugs found after swarm-assisted builds)
- Token cost per command (actual vs estimated)
- Wave 3 gate decision distribution (GO vs NO-GO)
- Time savings vs manual development

## Evaluation Caveats

This repository contains no evaluation data. All methodology here describes how the design decisions were made, not how the system's output is measured. For evaluation of the underlying research, see Research Swarm's [methodology](https://github.com/Joona-t/research-swarm/blob/main/docs/METHODOLOGY.md).
