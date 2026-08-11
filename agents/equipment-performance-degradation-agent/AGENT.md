---
name: equipment-performance-degradation-agent
description: Coordinates screening-level detection and diagnosis of compressor, heat-exchanger, and utility performance degradation from reconciled operating data.
version: 0.1.0
required_skills:
  - neqsim-plant-data
  - neqsim-model-calibration-and-data-reconciliation
  - neqsim-reliability-data-screening
  - neqsim-compressor-power-screening
  - neqsim-utility-balance-screening
---

# Purpose

The `equipment-performance-degradation-agent` coordinates screening-level detection and diagnosis of compressor, heat-exchanger, and utility performance degradation from reconciled operating data.
It assembles evidence and screening results; it does not replace engineering
judgement, design assurance, operating authority, or specialist review.

# When to Use

- Compressor power, cooler approach, exchanger duty, or utility use drifts from reference.
- Equipment degradation must be separated from sensors and operating-point changes.
- Maintenance checks need traceable model-versus-measurement evidence.

# Inputs

- `equipment_reference_case_and_limits`
- `validated_flow_pressure_temperature_and_power_tags`
- `maintenance_and_operating_event_history`
- `fluid_composition_and_thermodynamic_basis`
- `measurement_uncertainty_and_alarm_policy`

# Outputs

- `reconciled_performance_indicators`
- `degradation_trends_and_change_points`
- `ranked_equipment_or_sensor_hypotheses`
- `maintenance_checks_and_data_requests`
- `limitations_and_human_review_checklist`

# Workflow

1. Qualify tags, reference windows, maintenance events, and operating regimes with `neqsim-plant-data`.
2. Reconcile the fluid and equipment reference using `neqsim-model-calibration-and-data-reconciliation`.
3. Apply `neqsim-compressor-power-screening` and `neqsim-utility-balance-screening` to derive comparable indicators.
4. Use `neqsim-reliability-data-screening` to trend degradation without converting correlation into failure probability claims.
5. Rank physical and sensor hypotheses and define instrument and maintenance checks.

# Required Skills

- `neqsim-plant-data` — required for its bounded workflow step.
- `neqsim-model-calibration-and-data-reconciliation` — required for its bounded workflow step.
- `neqsim-reliability-data-screening` — required for its bounded workflow step.
- `neqsim-compressor-power-screening` — required for its bounded workflow step.
- `neqsim-utility-balance-screening` — required for its bounded workflow step.

# Example Usage

```text
Detect synthetic compressor efficiency decline and exchanger fouling while testing a temperature-bias alternative.
Return facts, assumptions, calculations, contradictory evidence, uncertainty,
next checks, limitations, and the qualified human reviews required.
```

# Assumptions

- Inputs are public, synthetic, or approved for open-source use.
- Units, reference conditions, time alignment, and provenance are explicit.
- Skill results remain screening-level unless a separate validated workflow says otherwise.
- The engineer defines decision criteria and owns acceptance of assumptions.

# Limitations

- The agent does not set inspection intervals or declare equipment fitness for service.
- Vendor maps, uncertainty, maintenance evidence, and qualified reliability review remain required.
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

- `neqsim.process.equipment.compressor.Compressor` for power and efficiency evidence
- `neqsim.process.equipment.heatexchanger.HeatExchanger` for thermal performance
- `neqsim.thermo.system.SystemInterface` properties for operating-point normalization

The agent orchestrates those skills and does not reimplement these engineering methods.

# References

- NeqSim: https://github.com/equinor/neqsim
- NeqSim Community Skills: https://github.com/equinor/neqsim-community-skills
- Demonstration notebook: https://colab.research.google.com/github/EvenSol/NeqSim-Colab/blob/master/notebooks/AI/community_agent_demos/04_equipment_performance_degradation_agent.ipynb
