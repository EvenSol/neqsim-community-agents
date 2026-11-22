# NCS Production Analysis Agent

Coordinates an early-stage, public-data analysis of production on the Norwegian
Continental Shelf (NCS). It loads a source-attributed database of headline NCS
facts (production, resources, exports, field inventory) from
[norskpetroleum.no](https://www.norskpetroleum.no/en/) and the Norwegian
Offshore Directorate FactPages, answers inventory and resource-accounting
questions, and can chain a screening reservoir-depletion profile into asset-value
(NPV) and energy/emissions screening.

For tie-in and export work it also pulls a host field's monthly production,
facilities and nearby undeveloped discoveries live from the Sodir DataService
REST API. From these it derives GOR and water-cut trends and a historic-peak
ullage proxy. It also reads Gassco Urgent Market Messages the user has saved, to
frame gas-export availability. It hands that context to the
`tie-in-screening-agent` and the `gas-export-pipeline-agent`.

This agent supports screening and orientation only. It **does not replace**
reservoir simulation, official production statistics, commercial evaluation, or
qualified reservoir, production-technology, and economics engineering. A
qualified **human review** is always required before any decision.

## Required Skills

- `neqsim-norwegian-continental-shelf-data`
- `neqsim-reservoir-depletion-screening`
- `neqsim-asset-value-npv-screening`
- `neqsim-energy-emissions-screening`

## Attribution

Facts are reused with attribution to Norwegian Petroleum
(www.norskpetroleum.no), the Norwegian Ministry of Energy, and the Norwegian
Offshore Directorate. Every reused figure keeps its source and reference year.
Live Sodir data is open data under the Norwegian Licence for Open Government
Data (NLOD). Gassco UMM data comes from the user's own export of umm.gassco.no,
quoted with Gassco's disclaimer, and the agent never scrapes the site.

## Layout

- `AGENT.md` — agent definition and workflow.
- `agent.yaml` — machine-readable manifest.
- `prompts/example-prompts.md` — example prompts.
- `examples/ncs-production-analysis-checklist.md` — walkthrough checklist.
- `tests/README.md` — how to exercise the agent through its skills.

See `AGENT.md` for the full workflow, assumptions, limitations, and the validated
NeqSim path.
