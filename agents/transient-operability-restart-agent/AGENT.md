---
name: transient-operability-restart-agent
description: Coordinates screening-level shutdown and restart qualification against transient hydraulic, thermal, liquid-inventory, control, and compressor-protection limits.
version: 0.1.0
required_skills:
  - neqsim-dynamic-process-preparation
  - neqsim-dynamic-simulation
  - neqsim-controllability-operability
  - neqsim-surf-cooldown-screening
  - neqsim-compressor-antisurge-recycle
---

# Purpose

The `transient-operability-restart-agent` coordinates screening-level shutdown and restart qualification against transient hydraulic, thermal, liquid-inventory, control, and compressor-protection limits.
It assembles evidence and screening results; it does not replace engineering
judgement, design assurance, operating authority, or specialist review.

# When to Use

- A shutdown duration or restart ramp must be screened before a detailed study.
- Pressure, temperature, liquid inventory, control, or compressor limits may interact.
- Alternative restart procedures need a common evidence package.

# Inputs

- `shutdown_duration_and_initial_state`
- `restart_sequence_and_ramp_candidates`
- `boundary_conditions_and_trip_events`
- `pressure_temperature_level_and_compressor_limits`
- `fluid_route_control_and_inventory_basis`

# Outputs

- `event_timeline_and_state_trajectories`
- `operating_envelope_violations`
- `restart_strategy_comparison`
- `hold_points_abort_criteria_and_required_studies`
- `assumptions_and_human_review_record`

# Workflow

1. Define event chronology, initial state, boundary conditions, and immutable limits.
2. Use `neqsim-dynamic-process-preparation` to qualify the steady-to-dynamic handover.
3. Use `neqsim-surf-cooldown-screening` to establish the shutdown thermal state.
4. Use `neqsim-dynamic-simulation` to execute each restart and trip scenario.
5. Use `neqsim-controllability-operability` and `neqsim-compressor-antisurge-recycle` to evaluate control and map margins.
6. Compare procedures, document violations, and define engineer-approved hold points.

# Required Skills

- `neqsim-dynamic-process-preparation` — required for its bounded workflow step.
- `neqsim-dynamic-simulation` — required for its bounded workflow step.
- `neqsim-controllability-operability` — required for its bounded workflow step.
- `neqsim-surf-cooldown-screening` — required for its bounded workflow step.
- `neqsim-compressor-antisurge-recycle` — required for its bounded workflow step.

# Example Usage

```text
Compare aggressive and staged restart ramps after a four-hour synthetic shutdown with a compressor trip during recovery.
Return facts, assumptions, calculations, contradictory evidence, uncertainty,
next checks, limitations, and the qualified human reviews required.
```

# Assumptions

- Inputs are public, synthetic, or approved for open-source use.
- Units, reference conditions, time alignment, and provenance are explicit.
- Skill results remain screening-level unless a separate validated workflow says otherwise.
- The engineer defines decision criteria and owns acceptance of assumptions.

# Limitations

- Screening dynamics do not constitute an approved operating procedure.
- Hydrate, wax, terrain, control logic, trips, and vendor limits require validated project models.
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

- `neqsim.process.processmodel.ProcessSystem#runTransient()` for dynamic execution
- `neqsim.process.equipment.pipeline.TwoPhasePipeLine` and separator inventory models for transient states
- `neqsim.process.controllerdevice.ControllerDeviceBaseClass` and compressor protection calculations for control evidence

The agent orchestrates those skills and does not reimplement these engineering methods.

# References

- NeqSim: https://github.com/equinor/neqsim
- NeqSim Community Skills: https://github.com/equinor/neqsim-community-skills
- Demonstration notebook: https://colab.research.google.com/github/EvenSol/NeqSim-Colab/blob/master/notebooks/AI/community_agent_demos/03_transient_operability_restart_agent.ipynb
