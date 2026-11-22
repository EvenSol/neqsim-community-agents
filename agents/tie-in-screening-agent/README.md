# Tie-In Screening Agent

The Tie-In Screening Agent supports early-stage screening of tie-in opportunities by combining fluid quality checks, hydrate screening, and separator screening.

It helps engineers review available fluid data, identify potential flow assurance risks, identify required studies, generate screening reports, and suggest NeqSim workflows. It is intended for transparent concept screening only.

## Capabilities

- Review available fluid data
- Identify potential flow assurance risks
- Map a project maturity stage to a public resource classification category
- Identify required studies
- Generate screening reports
- Suggest NeqSim workflows
- For an NCS host: pull public host production, GOR/water-cut trend, an
  indicative ullage proxy and nearby undeveloped discoveries (Sodir), and frame
  gas-export availability (Gassco UMM)

## Required Skills

- `fluid-quality-check`
- `hydrate-screening`
- `separator-modelling`
- `resource-classification-screening`

## Context Skills

- `norwegian-continental-shelf-data` (`neqsim-norwegian-continental-shelf-data`),
  used when the host is on the Norwegian Continental Shelf

## Directory Contents

- [AGENT.md](AGENT.md) defines the human-readable agent standard.
- [agent.yaml](agent.yaml) defines machine-readable metadata.
- [examples/](examples/) contains public example workflows.
- [prompts/](prompts/) contains reusable prompt examples.
- [tests/](tests/) contains validation notes for this agent.

## Human Review

Tie-in screening results require qualified process, flow assurance, safety, and project review before concept selection, design, or operational use.