# Field Visualization Agent

The Field Visualization Agent makes maps and pipeline profile illustrations for NeqSim tie-in and flow-assurance studies. It combines open data - Norwegian Offshore Directorate (Sodir) FactMaps facilities, pipelines and fields, and EMODnet Bathymetry - with NeqSim pipeline results, and delivers an interactive field map, a stacked depth/pressure/temperature/hydrate-margin profile, a P-T path over the hydrate curve, and a combined one-page figure with the route coloured by hydrate-margin status.

This agent supports illustration and early screening only. It does not design routes or pipelines and does not perform transient, cooldown or inhibitor design. A qualified human review is always required, and this agent does not replace flow assurance, pipeline or project assurance reviews.

## Required Skills

- `offshore-field-map` (`neqsim-offshore-field-map`)
- `pipeline-profile-plot` (`neqsim-pipeline-profile-plot`)

Context skills: `neqsim-pipe-route-profile`, `neqsim-bathymetry-profile-screening`, `neqsim-hydrate-margin-check`, `neqsim-field-layout-import`, `neqsim-norwegian-continental-shelf-data`.

## Quick Start

```bash
python -m pip install -e "skills/subsea/offshore-field-map[map,plot]" \
                      -e "skills/flow-assurance/pipeline-profile-plot[plot,neqsim]"
python skills/flow-assurance/pipeline-profile-plot/examples/combined_map_and_profile.py out/
```

(run from a checkout of `neqsim-community-skills`).

## Public Scope

Sodir data are used under NLOD 2.0 and EMODnet data under CC BY 4.0, with attribution on every figure. Examples use synthetic wells, routes and fluids. Network access is needed only for live Sodir and EMODnet queries and for map tiles in the browser.

## Related Agents

Hands over to the `tie-in-screening-agent` (host capacity and separation), the `pipe-route-screening-agent` (velocity and pressure-drop screening), the `subsea-layout-screening-agent` (step-out and layout geometry) and the `flow-assurance-engineer-agent` (hydrate and wax mitigation discussion) when a task goes beyond illustration.
