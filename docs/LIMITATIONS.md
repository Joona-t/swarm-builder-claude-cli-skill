# Limitations

## Evaluation Gaps

1. **No output quality data.** No extension builds have been scored, compared against manual development, or reviewed by external developers.

2. **No run data at all.** This repository contains zero metrics, logs, or experiment results. All empirical claims reference Research Swarm, which has its own limitations.

3. **External evidence, internal claims.** Research Swarm's ablation data comes from a research automation pipeline with different agents, different tasks, and different evaluation. Applying those findings to browser extension development is a reasonable design bet, not a validated transfer.

## System Limitations

4. **Claude Code dependency.** Only works within Claude Code. Not portable to other AI coding tools.

5. **Hardcoded paths.** `scripts/swarm-build.py` contains paths like `/Users/darkfire/Claude x LoveSpark`. Other users would need to modify the script.

6. **Domain-specific prompts.** All agent prompts are written for Manifest V3 browser extensions (LoveSpark ecosystem). Adapting to web apps, mobile apps, or backend services would require substantial prompt rewriting.

7. **No automated quality gate.** Unlike Research Swarm's critic+judge pipeline, Swarm Builder relies on the Linus Gate (a single agent) for quality decisions. There is no automated scoring or keep/discard mechanism.

8. **Token cost.** A full swarm-build costs an estimated 100-140k tokens. This is a non-trivial expense.

## Design Limitations

9. **Position-locked cross-feed untested.** The protocol is implemented but its effect on extension architecture quality has not been measured.

10. **Scope boundaries not validated for this domain.** OUT OF SCOPE declarations were added based on Research Swarm findings from a different domain. Whether they correctly partition the extension development design space is unknown.

11. **No rollback mechanism.** If Wave 4 introduces bugs, there is no automated way to revert to the pre-build state.
