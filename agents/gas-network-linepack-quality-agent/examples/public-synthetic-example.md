# Public Synthetic Example

## Objective

Forecast a synthetic high-CO2 source front and demand step through three pipe sections to the delivery node.

## Input Package

- `network_topology_geometry_and_volumes`: synthetic, unit-labelled, and source-traceable
- `source_compositions_pressures_and_nominations`: synthetic, unit-labelled, and source-traceable
- `delivery_demand_and_pressure_limits`: synthetic, unit-labelled, and source-traceable
- `gas_quality_specification`: synthetic, unit-labelled, and source-traceable
- `initial_linepack_and_uncertainty`: synthetic, unit-labelled, and source-traceable

## Expected Agent Actions

1. Validate source composition and missing data with `neqsim-fluid-quality-check`.
2. Represent nodes, sections, demand, and routing with `neqsim-production-network-routing`.
3. Screen pressure drop and velocity with `neqsim-pressure-drop-screening` and `neqsim-line-velocity-check`.
4. Track section inventory and delayed composition fronts across scenarios.
5. Use `neqsim-uncertainty-quantification` to report arrival and constraint ranges, then prepare balancing actions for human approval.

## Expected Decision Package

- `section_and_total_linepack_forecast`
- `delivery_pressure_and_quality_front_arrival`
- `constraint_alarm_timeline`
- `balancing_or_blending_action_screen`
- `validation_and_human_review_package`

The package must distinguish calculated evidence, assumptions, warnings, and
recommended next checks. It must not turn a screening result into an operational
instruction.

## Human Review

A qualified multidisciplinary engineering team reviews the package before any
design, maintenance, intervention, dispatch, or operating decision.
