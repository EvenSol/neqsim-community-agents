# Public Synthetic Example

## Objective

Detect synthetic compressor efficiency decline and exchanger fouling while testing a temperature-bias alternative.

## Input Package

- `equipment_reference_case_and_limits`: synthetic, unit-labelled, and source-traceable
- `validated_flow_pressure_temperature_and_power_tags`: synthetic, unit-labelled, and source-traceable
- `maintenance_and_operating_event_history`: synthetic, unit-labelled, and source-traceable
- `fluid_composition_and_thermodynamic_basis`: synthetic, unit-labelled, and source-traceable
- `measurement_uncertainty_and_alarm_policy`: synthetic, unit-labelled, and source-traceable

## Expected Agent Actions

1. Qualify tags, reference windows, maintenance events, and operating regimes with `neqsim-plant-data`.
2. Reconcile the fluid and equipment reference using `neqsim-model-calibration-and-data-reconciliation`.
3. Apply `neqsim-compressor-power-screening` and `neqsim-utility-balance-screening` to derive comparable indicators.
4. Use `neqsim-reliability-data-screening` to trend degradation without converting correlation into failure probability claims.
5. Rank physical and sensor hypotheses and define instrument and maintenance checks.

## Expected Decision Package

- `reconciled_performance_indicators`
- `degradation_trends_and_change_points`
- `ranked_equipment_or_sensor_hypotheses`
- `maintenance_checks_and_data_requests`
- `limitations_and_human_review_checklist`

The package must distinguish calculated evidence, assumptions, warnings, and
recommended next checks. It must not turn a screening result into an operational
instruction.

## Human Review

A qualified multidisciplinary engineering team reviews the package before any
design, maintenance, intervention, dispatch, or operating decision.
