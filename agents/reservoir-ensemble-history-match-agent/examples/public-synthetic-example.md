# Public Synthetic Example

## Objective

Update a synthetic GIIP-aquifer-productivity ensemble with six years of pressure and rate history and pass posterior facility-feed percentiles downstream.

## Input Package

- `prior_ensemble_and_parameter_provenance`: synthetic, unit-labelled, and source-traceable
- `pressure_rate_and_fluid_history`: synthetic, unit-labelled, and source-traceable
- `observation_error_model`: synthetic, unit-labelled, and source-traceable
- `forecast_controls_and_constraints`: synthetic, unit-labelled, and source-traceable
- `facility_boundary_conditions`: synthetic, unit-labelled, and source-traceable

## Expected Agent Actions

1. Audit ensemble provenance, realization identity, controls, and observation units.
2. Use `neqsim-reservoir-depletion-screening` to establish a bounded depletion response.
3. Use `neqsim-model-calibration-and-data-reconciliation` to define residuals and observation handling.
4. Use `neqsim-uncertainty-quantification` to update weights or members and preserve posterior identity.
5. Use `neqsim-production-network-routing` to hand posterior rate and pressure ranges to wells and facilities.
6. Report match metrics, posterior collapse risks, plausibility checks, and human decisions.

## Expected Decision Package

- `posterior_ensemble_weights_or_members`
- `history_match_metrics_and_diagnostics`
- `forecast_p10_p50_p90_with_realization_identity`
- `well_and_facility_load_handoff`
- `plausibility_limitations_and_human_review_record`

The package must distinguish calculated evidence, assumptions, warnings, and
recommended next checks. It must not turn a screening result into an operational
instruction.

## Human Review

A qualified multidisciplinary engineering team reviews the package before any
design, maintenance, intervention, dispatch, or operating decision.
