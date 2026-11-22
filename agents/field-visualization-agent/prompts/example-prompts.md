# Example Prompts

These prompts use public open data (Sodir FactMaps, EMODnet) and synthetic study data. They produce screening illustrations only.

## Field Map Around a Host

```text
Make a field map around TROLL A with a 40 km radius. Show fields, main pipelines (coloured by medium) and facilities from Sodir FactMaps, with the EMODnet bathymetry overlay. Add a synthetic new well at 3.45 E, 60.75 N and a straight candidate route to the host. Give me the interactive HTML map and a static PNG, list the route length and the sources, and spot-check the EMODnet depth at the host against the Sodir water depth.
```

## Pipeline Profile With Hydrate Margin

```text
Run NeqSim for a 25 km, 10-inch tie-back along the supplied KP/depth route: wet gas with 3.5 mol% water, 3 MSm3/d, 140 bara and 55 C at the wellhead, U = 6 W/m2K, 4 C seabed. Compute the hydrate equilibrium temperature at each station and plot depth, pressure, temperature against hydrate temperature, and hydrate margin along KP. Report the arrival P and T, the minimum margin and its KP, and the first KP where the margin drops below 3 C and below 0 C.
```

## Combined Map and Profile

```text
Combine the field map and the NeqSim pipeline profile into one figure: route on the map coloured by hydrate-margin status (ok, watch below 3 C, high below 0 C), P-T path over the hydrate curve, and the stacked profile. Also give the interactive map with KP, P, T and margin tooltips at each station. Add a short note with data sources and licences, model settings, assumptions, limitations and what needs human review.
```

## Case Comparison

```text
Repeat the combined figure for U = 6 and U = 2 W/m2K and summarize how far the first hydrate KP moves. Keep the same axes on both profiles so they can be compared side by side.
```
