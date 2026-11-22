# Field Visualization Agent Tests

This folder documents how the Field Visualization Agent is validated in the community repository.

Structure validation is provided by the repository-level test suite:

```bash
python -m unittest discover -s tests
```

The repository tests confirm that this agent has:

- the required files (`AGENT.md`, `agent.yaml`, `README.md`, `examples`, `prompts`, `tests`)
- the required AGENT.md sections and front matter
- the required `agent.yaml` metadata keys, including `human_review_required: true`
- the declared required skills (`neqsim-offshore-field-map`, `neqsim-pipeline-profile-plot`)
- human review language in `AGENT.md` and `README.md`

The underlying logic is validated by the skill tests in the `neqsim-community-skills` repository:

- `skills/subsea/offshore-field-map/tests` - Sodir query building and paging, normalization of synthetic Sodir-shaped GeoJSON, EMODnet depth conversion and profile spacing, route classification, GeoJSON, folium and matplotlib rendering (offline, injected fetchers).
- `skills/flow-assurance/pipeline-profile-plot/tests` - margin rule, section detection, validation errors, record round trip, all figure types, and a small NeqSim PipeBeggsAndBrills + hydrateFormationTemperature run when `neqsim` is installed.

The worked example in `examples/tie-back-map-and-profile.md` is reproducible with `examples/combined_map_and_profile.py` in the skills repository.
