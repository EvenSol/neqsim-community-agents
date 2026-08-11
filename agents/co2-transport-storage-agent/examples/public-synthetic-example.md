# Public Synthetic Example

## Objective

Screen a synthetic 97 percent CO2 stream and two impurity envelopes through a 120 km dense-phase pipeline into an 18-well storage development.

## Input Package

- `co2_stream_composition_envelope`: synthetic, unit-labelled, and source-traceable
- `transport_inlet_state_and_pipeline_geometry`: synthetic, unit-labelled, and source-traceable
- `operating_and_phase_margin_limits`: synthetic, unit-labelled, and source-traceable
- `reservoir_injection_and_fracture_basis`: synthetic, unit-labelled, and source-traceable
- `uncertainty_scenarios_and_decision_criteria`: synthetic, unit-labelled, and source-traceable

## Expected Agent Actions

1. Validate composition basis and contaminants with `neqsim-fluid-quality-check`.
2. Use `neqsim-ccs-hydrogen` and `neqsim-phase-envelope` to establish property and phase margins.
3. Use `neqsim-pressure-drop-screening` for transport pressure, velocity, and sensitivity cases.
4. Build a transparent multi-well injectivity screen without claiming geomechanical qualification.
5. Use `neqsim-uncertainty-quantification` to propagate composition and reservoir ranges.
6. Use `neqsim-process-safety` to list loss-of-containment and operating studies requiring qualified review.

## Expected Decision Package

- `phase_property_and_impurity_screen`
- `pipeline_pressure_temperature_and_velocity_margins`
- `multi_well_injectivity_screen`
- `ranked_transport_storage_constraints`
- `required_detailed_studies_and_human_review_record`

The package must distinguish calculated evidence, assumptions, warnings, and
recommended next checks. It must not turn a screening result into an operational
instruction.

## Human Review

A qualified multidisciplinary engineering team reviews the package before any
design, maintenance, intervention, dispatch, or operating decision.
