# Public Synthetic Example

## Objective

Compare aggressive and staged restart ramps after a four-hour synthetic shutdown with a compressor trip during recovery.

## Input Package

- `shutdown_duration_and_initial_state`: synthetic, unit-labelled, and source-traceable
- `restart_sequence_and_ramp_candidates`: synthetic, unit-labelled, and source-traceable
- `boundary_conditions_and_trip_events`: synthetic, unit-labelled, and source-traceable
- `pressure_temperature_level_and_compressor_limits`: synthetic, unit-labelled, and source-traceable
- `fluid_route_control_and_inventory_basis`: synthetic, unit-labelled, and source-traceable

## Expected Agent Actions

1. Define event chronology, initial state, boundary conditions, and immutable limits.
2. Use `neqsim-dynamic-process-preparation` to qualify the steady-to-dynamic handover.
3. Use `neqsim-surf-cooldown-screening` to establish the shutdown thermal state.
4. Use `neqsim-dynamic-simulation` to execute each restart and trip scenario.
5. Use `neqsim-controllability-operability` and `neqsim-compressor-antisurge-recycle` to evaluate control and map margins.
6. Compare procedures, document violations, and define engineer-approved hold points.

## Expected Decision Package

- `event_timeline_and_state_trajectories`
- `operating_envelope_violations`
- `restart_strategy_comparison`
- `hold_points_abort_criteria_and_required_studies`
- `assumptions_and_human_review_record`

The package must distinguish calculated evidence, assumptions, warnings, and
recommended next checks. It must not turn a screening result into an operational
instruction.

## Human Review

A qualified multidisciplinary engineering team reviews the package before any
design, maintenance, intervention, dispatch, or operating decision.
