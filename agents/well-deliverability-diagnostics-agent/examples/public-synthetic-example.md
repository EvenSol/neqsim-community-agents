# Public Synthetic Example

## Objective

Use a synthetic gas-well test at one choke setting to distinguish a tubing restriction from skin loss and host backpressure.

## Input Package

- `reservoir_and_fluid_basis`: synthetic, unit-labelled, and source-traceable
- `well_completion_and_tubing_description`: synthetic, unit-labelled, and source-traceable
- `well_test_rates_and_pressures`: synthetic, unit-labelled, and source-traceable
- `facility_backpressure_and_choke_state`: synthetic, unit-labelled, and source-traceable
- `operating_events_and_uncertainty`: synthetic, unit-labelled, and source-traceable

## Expected Agent Actions

1. Confirm well-test conditions, fluid basis, units, and pressure references.
2. Use `neqsim-subsea-and-wells` to define the bounded well calculation path.
3. Use `neqsim-production-network-routing` to connect well, choke, flowline, and facility pressure.
4. Use `neqsim-model-calibration-and-data-reconciliation` to compare scenarios with the well test.
5. Use `neqsim-root-cause-analysis` to rank constraints and select the most discriminating next test.

## Expected Decision Package

- `screening_ipr_vlp_operating_points`
- `ranked_deliverability_constraints`
- `rate_and_pressure_residuals`
- `recommended_discriminating_well_tests`
- `validation_and_human_review_checklist`

The package must distinguish calculated evidence, assumptions, warnings, and
recommended next checks. It must not turn a screening result into an operational
instruction.

## Human Review

A qualified multidisciplinary engineering team reviews the package before any
design, maintenance, intervention, dispatch, or operating decision.
