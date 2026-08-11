# Public Synthetic Example

## Objective

Diagnose a 9 percent synthetic gas-condensate production shortfall after a pressure-drop event and rank flowline, compressor, well-inflow, and allocation explanations.

## Input Package

- `production_loss_question_and_time_window`: synthetic, unit-labelled, and source-traceable
- `validated_operating_tags_and_events`: synthetic, unit-labelled, and source-traceable
- `fluid_and_process_model_basis`: synthetic, unit-labelled, and source-traceable
- `healthy_reference_or_expected_case`: synthetic, unit-labelled, and source-traceable
- `operating_constraints_and_uncertainties`: synthetic, unit-labelled, and source-traceable

## Expected Agent Actions

1. Define the shortfall, time window, comparison basis, and decision owner.
2. Use `neqsim-plant-data` to qualify tags, events, sampling, and provenance.
3. Use `neqsim-model-calibration-and-data-reconciliation` to establish a healthy reference and residuals.
4. Use `neqsim-root-cause-analysis` to rank physical hypotheses and contradictory evidence.
5. Use `neqsim-production-optimization` only to screen recoverable operating margin within declared constraints.
6. Use `neqsim-professional-reporting` to produce the evidence, uncertainty, action, and review package.

## Expected Decision Package

- `reconciled_shortfall_and_loss_allocation`
- `ranked_physical_hypotheses`
- `evidence_for_and_against_each_hypothesis`
- `discriminating_checks_and_next_measurements`
- `assumptions_limitations_and_human_review_record`

The package must distinguish calculated evidence, assumptions, warnings, and
recommended next checks. It must not turn a screening result into an operational
instruction.

## Human Review

A qualified multidisciplinary engineering team reviews the package before any
design, maintenance, intervention, dispatch, or operating decision.
