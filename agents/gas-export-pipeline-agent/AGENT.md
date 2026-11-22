---
name: gas-export-pipeline-agent
description: Performs preliminary gas-export pipeline screening by chaining line velocity, pressure drop, and export compression power checks.
version: 0.2.0
agent_type: community-agent
required_skills:
- neqsim-line-velocity-check
- neqsim-pressure-drop-screening
- neqsim-compressor-power-screening
context_skills:
- neqsim-norwegian-continental-shelf-data
---

# Purpose

The Gas Export Pipeline Agent assists with preliminary screening of a gas-export pipeline and its export compression for public, reproducible engineering workflows. It chains an erosional and recommended line-velocity check, a single-phase pressure-drop screening against a recommended gradient guideline, and an indicative export-compression power estimate. Together these provide an early view of whether an export line size and compression duty are in a sensible range.

The agent supports early-stage engineering screening. It does not replace validated multiphase pipeline simulation, detailed compressor selection, mechanical design, or specialist review.

# When to Use

Use this agent when an engineer needs to:

- Screen an export-line diameter for erosional and recommended gas velocity
- Estimate the single-phase pressure drop along an export line and compare it to a gradient guideline
- Estimate the export-compression power needed to deliver gas to the export pressure
- Identify missing data needed for a rigorous export pipeline study
- Prepare a transparent preliminary export-system note
- For NCS export routes: check planned and unplanned unavailability in the
  Gassco system (fields, processing plants, exit terminals) for a time window
  from a Gassco UMM export the user has saved

# Inputs

Typical inputs include:

- Gas flow rate and gas density / molecular weight
- Pipeline internal diameter, length, and roughness
- Inlet and required export (delivery) pressure
- Gas temperature and compressibility information
- Compression suction and discharge pressure and efficiency assumptions
- Optionally, for NCS routes: a user-saved Gassco UMM export (event table CSV
  or Atom feed), the export asset name, a time window, and the export's time zone

# Outputs

Typical outputs include:

- Line-velocity screening result against erosional and recommended limits
- Pressure-drop screening result against a recommended gradient guideline
- Indicative export-compression power estimate
- Optionally, a gas-export availability window: peak concurrent unavailable
  capacity (MSm3/d) with Gassco's uncertainty band and available capacity at
  peak for the export asset
- Missing input list
- Recommended NeqSim pipeline and compressor follow-up analysis
- Assumptions and limitations
- Human review checklist

# Workflow

1. Confirm the export flow rate, line geometry, and inlet and export pressures.
2. Use `line-velocity-check` to screen the line velocity against erosional and recommended limits.
3. Use `pressure-drop-screening` to estimate the single-phase pressure drop and compare it to a recommended gradient guideline.
4. Use `compressor-power-screening` to estimate the export-compression power for the required pressure rise.
5. For an NCS export route with a saved Gassco UMM export, use
   `norwegian-continental-shelf-data` `parse_umm_csv()` / `parse_umm_atom()` and
   `capacity_impact()` to report the availability window for the export asset.
   Never scrape umm.gassco.no, and quote Gassco's disclaimer.
6. Identify missing fluid, multiphase, terrain, and thermal data.
7. Explain uncertainty and screening assumptions.
8. Recommend appropriate NeqSim pipeline and compressor follow-up analysis.
9. Document limitations and human review requirements.

# Required Skills

- `line-velocity-check` mapped to community catalog ID `neqsim-line-velocity-check`
- `pressure-drop-screening` mapped to community catalog ID `neqsim-pressure-drop-screening`
- `compressor-power-screening` mapped to community catalog ID `neqsim-compressor-power-screening`

# Context Skills

- `neqsim-norwegian-continental-shelf-data`: load it for NCS export routes. It
  parses Gassco Urgent Market Messages the user has saved and screens the worst
  concurrent unavailability for an export asset, with Gassco's stated
  uncertainty band and caveats.

# Example Usage

```text
Screen this public example gas-export pipeline and its export compression. Check the line velocity, estimate the pressure drop along the line, and estimate the export-compression power. State the assumptions, identify missing information, and recommend what a pipeline engineer should check next.
```

# Assumptions

- Screening inputs are public, synthetic, or approved for open-source use.
- The agent provides preliminary triage only.
- Single-phase gas behaviour is assumed; multiphase, terrain, and thermal effects require explicit data and review.

# Limitations

- The agent does not replace validated multiphase pipeline simulation or transient analysis.
- The agent does not perform detailed compressor selection or surge analysis.
- The agent does not confirm a safe or optimal export-line size.
- The agent does not account for elevation, slugging, or compositional effects unless supplied and reviewed.
- Gassco UMM availability is screening context, not a nomination or capacity-booking basis. Events below Gassco's 5 MSm3/d threshold are not published, and summed concurrent events can overstate the net impact.

# Validation Checklist

- Flow rate, diameter, length, and roughness units are stated.
- Inlet and export pressure units are stated.
- Gas density / molecular weight and temperature assumptions are documented.
- Compression suction, discharge, and efficiency assumptions are documented.
- Velocity, pressure-drop, and power results are reported with their guidelines.
- Follow-up analysis recommendations are included.
- If Gassco UMM events are used: they are latest revisions, read in the right time zone, and quoted with Gassco's disclaimer.
- Qualified human review is completed before design decisions.

# Related NeqSim Functionality

The screening produced by this agent maps to validated, rigorous NeqSim Java functionality that a qualified engineer should use for design-grade work:

- `neqsim.process.equipment.pipeline.PipeBeggsAndBrills` — multiphase pipeline pressure and temperature profile.
- `neqsim.process.equipment.compressor.Compressor` — rigorous compression power with performance curves.

In Python these classes are reachable through the `neqsim` package (for example `from neqsim import jneqsim`).

# References

- NeqSim: https://github.com/equinor/neqsim
- NeqSim Community Skills: https://github.com/equinor/neqsim-community-skills
- Community skills: `line-velocity-check`, `pressure-drop-screening`, `compressor-power-screening`; context skill `norwegian-continental-shelf-data`
- Gassco Urgent Market Messages: https://umm.gassco.no/
- Gassco, Principles for publication on umm.gassco.no: https://umm.gassco.no/resources/Principles%20for%20publication%20on%20umm.pdf
