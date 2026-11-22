# Example: Tie-Back Map and Pipeline Profile

This example uses public synthetic data. It reproduces `examples/combined_map_and_profile.py` in the `neqsim-community-skills` repository (skill `neqsim-pipeline-profile-plot`), which runs offline with synthetic map layers and uses NeqSim when it is installed.

## Scenario

A new gas-condensate well (NEW-1) is tied back 25 km to a host platform (HOST A). The question for the figure set: where along the line does the fluid cool into the hydrate region, and how does that look on the map?

Public synthetic inputs:

- Route stations (KP km, water depth m, lon, lat): (0, 345, 3.300, 60.780), (4, 352, 3.350, 60.752), (9, 330, 3.420, 60.720), (14, 338, 3.480, 60.685), (20, 318, 3.545, 60.640), (25, 303, 3.600, 60.600)
- Fluid (mol): N2 0.8, CO2 2.0, C1 80.0, C2 6.5, C3 3.2, iC4 0.6, nC4 1.0, nC5 0.5, nC6 0.4, nC10 1.5, water 3.5; NeqSim `SystemSrkCPAstatoil`, mixing rule 10
- 3.0 MSm3/d at 140 bara and 55 C
- Inner diameter 0.254 m, roughness 50 um, U = 6 W/m2K, seabed 4 C
- Hydrate margin guideline: 3 C

## Steps

1. `neqsim-offshore-field-map`: load the (synthetic) Sodir-shaped fields, pipelines and facilities; highlight HOST A; add NEW-1.
2. `neqsim-pipeline-profile-plot`: `run_route_pipeline` over the six stations (five PipeBeggsAndBrills legs, 51 stations), then `add_hydrate_temperatures`.
3. `PipelineProfile.evaluate(min_margin=3.0)`.
4. Add the route to the map with `values=profile.hydrate_margin_c` and per-station tooltips; save the HTML map.
5. `plot_combined(profile, map_builder=fm, hydrate_curve=...)`.

## Result (NeqSim 3.x, synthetic case)

| Quantity | Value |
| --- | --- |
| Route length | 25.0 km |
| Arrival pressure / temperature | 111.9 bara / 16.2 C |
| Hydrate equilibrium temperature at arrival | about 21 C |
| First KP with margin below 3 C | about 17 km |
| First KP inside hydrate region | 20 km (station spacing 0.5 km) |
| Minimum margin | -4.7 C at KP 25 |
| Margin warning | high |

The combined figure shows the route on the map turning from green to amber near KP 17 and red from KP 20, the P-T path crossing the hydrate curve before arrival, and the temperature panel with the subcooled area shaded from KP 20 to the host.

## Interpretation and Follow-Up

- Steady-state flowing conditions already enter the hydrate region in the last 5 km; inhibition, insulation (lower U), or a higher arrival temperature needs to be studied.
- Shut-in cooldown and restart are not covered; use the `subsea-cooldown-agent` route for that.
- The figures are screening illustrations; a qualified flow assurance engineer must review the model settings and results.
