# Roadmap

## Validated Next Steps

1. **Add run tracking.** Log actual token usage, build time, and agent outputs per swarm command execution. Without data, this system cannot be evaluated.

2. **Remove hardcoded paths.** Make `scripts/swarm-build.py` configurable so other users can adopt the tool.

3. **Score 5 extension builds.** Manually review and score 5 extension builds (swarm-assisted vs not) on code quality, completeness, and defect rate to establish a baseline.

4. **Track Linus Gate decisions.** Log every GO/NO-GO decision with the reason to evaluate whether Wave 3 adds value.

## Speculative Ideas

5. **Add automated quality scoring.** Port Research Swarm's critic+judge pipeline as a post-build evaluation step.

6. **Domain adaptation guide.** Document how to modify agent prompts and scope boundaries for non-extension projects.

7. **Agent count ablation for extension builds.** Run the same extension build with 15, 10, and 7 agents to find the optimal count for this domain specifically.

8. **Integration with Research Swarm.** Automatically run Research Swarm on extension development topics before starting a swarm-build, so the build is informed by fresh research.
