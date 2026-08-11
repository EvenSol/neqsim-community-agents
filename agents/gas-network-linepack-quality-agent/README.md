# Gas Network Linepack Quality Agent

Coordinates screening-level gas-network pressure, linepack, composition-front, and delivery-quality forecasting for source and demand changes.

This package is a thin orchestrator over declared NeqSim skills. It contains no
engineering method and produces screening evidence only.

## Contents

- [AGENT.md](AGENT.md) defines scope, workflow, validation, and limits.
- [agent.yaml](agent.yaml) provides machine-readable metadata.
- [examples/](examples/) contains a public synthetic decision package.
- [prompts/](prompts/) contains reusable prompts.
- [tests/](tests/) records package validation expectations.
- [Colab demonstration](https://colab.research.google.com/github/EvenSol/NeqSim-Colab/blob/master/notebooks/AI/community_agent_demos/05_gas_network_linepack_quality_agent.ipynb) executes the public synthetic workflow.

## Human Review

Qualified human review is required. The agent does not replace engineering
judgement, specialist studies, design assurance, or operating authority.
