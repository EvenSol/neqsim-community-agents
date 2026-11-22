# Engineering 3D Illustration Agent Tests

This folder documents how the Engineering 3D Illustration Agent is validated in
the community repository.

Structure validation is provided by the repository-level test suite:

```bash
python -m unittest discover -s tests
python scripts/validate_agent_manifests.py
```

The repository tests confirm that this agent has:

- the required files (`AGENT.md`, `agent.yaml`, `README.md`, `examples`, `prompts`, `tests`)
- the required AGENT.md sections and front matter
- the required `agent.yaml` metadata keys, including `human_review_required: true`
- the declared required skill (`neqsim-engineering-3d-illustration`)
- declared context skills and coordinated agents that exist in the catalogs
- human review language in `AGENT.md` and `README.md`

The drawing logic is validated by the skill tests in the
`neqsim-community-skills` repository under
`skills/visualization/engineering-3d-illustration/tests`. Those tests check the
drawn solids against closed-form vessel volumes, check that every out-of-scale
choice reaches the caption, and - where PyVista, CadQuery or OpenSCAD are
installed - draw and export for real.
