---
name: production-shortfall-diagnostics-agent
description: Coordinates screening-level production shortfall diagnosis across measured data, calibrated models, physical root causes, and production-loss allocation.
version: 0.1.0
required_skills:
  - neqsim-plant-data
  - neqsim-model-calibration-and-data-reconciliation
  - neqsim-root-cause-analysis
  - neqsim-production-optimization
  - neqsim-professional-reporting
---

# Purpose

The `production-shortfall-diagnostics-agent` coordinates screening-level production shortfall diagnosis across measured data, calibrated models, physical root causes, and production-loss allocation.
It assembles evidence and screening results; it does not replace engineering
judgement, design assurance, operating authority, or specialist review.

# When to Use

- An asset has an unexplained rate or allocation shortfall.
- Several well, flowline, process, compressor, or metering causes are plausible.
- A traceable diagnostic package is needed before intervention planning.

# Inputs

- `production_loss_question_and_time_window`
- `validated_operating_tags_and_events`
- `fluid_and_process_model_basis`
- `healthy_reference_or_expected_case`
- `operating_constraints_and_uncertainties`

# Outputs

- `reconciled_shortfall_and_loss_allocation`
- `ranked_physical_hypotheses`
- `evidence_for_and_against_each_hypothesis`
- `discriminating_checks_and_next_measurements`
- `assumptions_limitations_and_human_review_record`

# Workflow

1. Define the shortfall, time window, comparison basis, and decision owner.
2. Use `neqsim-plant-data` to qualify tags, events, sampling, and provenance.
3. Use `neqsim-model-calibration-and-data-reconciliation` to establish a healthy reference and residuals.
4. Use `neqsim-root-cause-analysis` to rank physical hypotheses and contradictory evidence.
5. Use `neqsim-production-optimization` only to screen recoverable operating margin within declared constraints.
6. Use `neqsim-professional-reporting` to produce the evidence, uncertainty, action, and review package.

# Required Skills

- `neqsim-plant-data` — required for its bounded workflow step.
- `neqsim-model-calibration-and-data-reconciliation` — required for its bounded workflow step.
- `neqsim-root-cause-analysis` — required for its bounded workflow step.
- `neqsim-production-optimization` — required for its bounded workflow step.
- `neqsim-professional-reporting` — required for its bounded workflow step.

# Example Usage

```text
Diagnose a 9 percent synthetic gas-condensate production shortfall after a pressure-drop event and rank flowline, compressor, well-inflow, and allocation explanations.
Return facts, assumptions, calculations, contradictory evidence, uncertainty,
next checks, limitations, and the qualified human reviews required.
```

# Assumptions

- Inputs are public, synthetic, or approved for open-source use.
- Units, reference conditions, time alignment, and provenance are explicit.
- Skill results remain screening-level unless a separate validated workflow says otherwise.
- The engineer defines decision criteria and owns acceptance of assumptions.

# Limitations

- Hypothesis ranking is conditional on the declared model and available tags.
- The agent does not authorize operational changes or equipment intervention.
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

- `neqsim.process.processmodel.ProcessSystem` for the governed process reference
- `neqsim.process.equipment.separator.Separator` and `neqsim.process.equipment.compressor.Compressor` for equipment residuals
- `neqsim.thermodynamicoperations.ThermodynamicOperations#TPflash()` for state reconciliation

The agent orchestrates those skills and does not reimplement these engineering methods.

# References

- NeqSim: https://github.com/equinor/neqsim
- NeqSim Community Skills: https://github.com/equinor/neqsim-community-skills
- Demonstration notebook: https://colab.research.google.com/github/EvenSol/NeqSim-Colab/blob/master/notebooks/AI/community_agent_demos/01_production_shortfall_diagnostics_agent.ipynb
