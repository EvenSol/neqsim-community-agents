---
name: gas-network-linepack-quality-agent
description: Coordinates screening-level gas-network pressure, linepack, composition-front, and delivery-quality forecasting for source and demand changes.
version: 0.1.0
required_skills:
  - neqsim-fluid-quality-check
  - neqsim-production-network-routing
  - neqsim-pressure-drop-screening
  - neqsim-line-velocity-check
  - neqsim-uncertainty-quantification
---

# Purpose

The `gas-network-linepack-quality-agent` coordinates screening-level gas-network pressure, linepack, composition-front, and delivery-quality forecasting for source and demand changes.
It assembles evidence and screening results; it does not replace engineering
judgement, design assurance, operating authority, or specialist review.

# When to Use

- Source composition, nomination, or demand changes propagate through a gas network.
- Pressure and delivery quality constraints may occur at different times.
- Dispatch alternatives need a transparent screening forecast.

# Inputs

- `network_topology_geometry_and_volumes`
- `source_compositions_pressures_and_nominations`
- `delivery_demand_and_pressure_limits`
- `gas_quality_specification`
- `initial_linepack_and_uncertainty`

# Outputs

- `section_and_total_linepack_forecast`
- `delivery_pressure_and_quality_front_arrival`
- `constraint_alarm_timeline`
- `balancing_or_blending_action_screen`
- `validation_and_human_review_package`

# Workflow

1. Validate source composition and missing data with `neqsim-fluid-quality-check`.
2. Represent nodes, sections, demand, and routing with `neqsim-production-network-routing`.
3. Screen pressure drop and velocity with `neqsim-pressure-drop-screening` and `neqsim-line-velocity-check`.
4. Track section inventory and delayed composition fronts across scenarios.
5. Use `neqsim-uncertainty-quantification` to report arrival and constraint ranges, then prepare balancing actions for human approval.

# Required Skills

- `neqsim-fluid-quality-check` — required for its bounded workflow step.
- `neqsim-production-network-routing` — required for its bounded workflow step.
- `neqsim-pressure-drop-screening` — required for its bounded workflow step.
- `neqsim-line-velocity-check` — required for its bounded workflow step.
- `neqsim-uncertainty-quantification` — required for its bounded workflow step.

# Example Usage

```text
Forecast a synthetic high-CO2 source front and demand step through three pipe sections to the delivery node.
Return facts, assumptions, calculations, contradictory evidence, uncertainty,
next checks, limitations, and the qualified human reviews required.
```

# Assumptions

- Inputs are public, synthetic, or approved for open-source use.
- Units, reference conditions, time alignment, and provenance are explicit.
- Skill results remain screening-level unless a separate validated workflow says otherwise.
- The engineer defines decision criteria and owns acceptance of assumptions.

# Limitations

- Reduced linepack and front tracking do not replace a calibrated transient network model.
- Contractual gas-quality methods, metering, dispatch rules, and operating authority remain external.
- The agent cannot establish operational readiness, certified accuracy, or safety.
- Company policy, private data connectors, and confidential procedures belong in enterprise overlays.

# Validation Checklist

- The engineering question, time window, boundaries, and decision owner are stated.
- Required inputs are present; missing or estimated values are labelled.
- Units, sign conventions, reference conditions, and data provenance are checked.
- Every declared skill completed its own validation checks and returned screening status.
- Model-versus-measurement residuals and contradictory evidence are retained where relevant.
- Sensitivities and uncertainty are reported without hiding failed or marginal cases.
- Assumptions and limitations are reviewed against the requested decision.
- A qualified engineer completes human review before design or operational action.

# Related NeqSim Functionality

The declared skills ultimately connect the screening package to validated NeqSim
workflows including:

- `neqsim.thermodynamicoperations.ThermodynamicOperations#TPflash()` for composition-specific properties
- `neqsim.process.equipment.pipeline.PipeBeggsAndBrills` for validated pressure-drop paths
- `neqsim.process.processmodel.ProcessSystem` for connected network calculations

The agent orchestrates those skills and does not reimplement these engineering methods.

# References

- NeqSim: https://github.com/equinor/neqsim
- NeqSim Community Skills: https://github.com/equinor/neqsim-community-skills
- Demonstration notebook: https://colab.research.google.com/github/EvenSol/NeqSim-Colab/blob/master/notebooks/AI/community_agent_demos/05_gas_network_linepack_quality_agent.ipynb
