# Well Deliverability Diagnostics Agent

Coordinates screening-level well deliverability diagnosis to distinguish reservoir, completion, tubing, artificial-lift, and facility-backpressure constraints.

This package is a thin orchestrator over declared NeqSim skills. It contains no
engineering method and produces screening evidence only.

## Contents

- [AGENT.md](AGENT.md) defines scope, workflow, validation, and limits.
- [agent.yaml](agent.yaml) provides machine-readable metadata.
- [examples/](examples/) contains a public synthetic decision package.
- [prompts/](prompts/) contains reusable prompts.
- [tests/](tests/) records package validation expectations.
- [Colab demonstration](https://colab.research.google.com/github/EvenSol/NeqSim-Colab/blob/master/notebooks/AI/community_agent_demos/02_well_deliverability_diagnostics_agent.ipynb) executes the public synthetic workflow.

## Human Review

Qualified human review is required. The agent does not replace engineering
judgement, specialist studies, design assurance, or operating authority.
