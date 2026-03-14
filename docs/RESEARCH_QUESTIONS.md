# Research Questions

## RQ1: Do explicit scope boundaries (OUT OF SCOPE) prevent domain bleeding in parallel agent swarms?

**Why it matters:** When multiple agents work on related domains simultaneously, they often produce overlapping findings. This forces a synthesis step that averages out distinct recommendations into generic advice — a phenomenon called "integrative compromise."

**Status:** Implemented but not independently evaluated. Scope boundaries are defined for all 15 agents. Research Swarm found that adding OUT_OF_SCOPE declarations reduced technique overlap from 76% to 38% in its pipeline. Whether the same effect holds in this system's 4-wave architecture has not been measured.

## RQ2: Does position-locked cross-feed preserve more information than forced consensus?

**Why it matters:** In v1.0, leads were forced to converge in a third round, which may have caused them to weaken or abandon valid recommendations that conflicted with peers. Position-locking (flag conflicts but don't change conclusions) should preserve more distinct findings.

**Status:** Implemented in v2.0. Not evaluated. No before/after comparison of output quality between v1.0 (forced consensus) and v2.0 (position-locked) has been conducted.

## RQ3: What is the minimum agent count that maintains coverage for browser extension development?

**Why it matters:** Each agent costs tokens. If 15 agents have overlapping scope, fewer well-scoped agents might produce equivalent coverage at lower cost.

**Status:** Partially addressed. The 22→15 restructure removed 7 overlapping agents based on Research Swarm ablation data (from a different pipeline). Whether further reduction is possible for this specific domain has not been tested.

## RQ4: Does the Linus Gate (Wave 3 security review) catch issues that specialists miss?

**Why it matters:** Wave 3 is a single-agent bottleneck. If it rarely blocks and doesn't catch novel issues beyond what security-scanner and privacy-guardian find in Wave 1, it adds latency without value.

**Status:** Not measured. No data on Linus Gate GO/NO-GO decisions exists in this repository.
