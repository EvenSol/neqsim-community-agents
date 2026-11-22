# engineering-3d-illustration-agent

Turns the designs and calculated results of a NeqSim study into 3D figures, using
open tools only. It assists engineers and does not replace engineering judgement.

```
study results (NeqSim process model, DEXPI P&ID, design data, layout study,
               datasheet values, stated assumptions)
        |
        v
  what is the figure for?  ->  report figure | CAD exchange | editable model | presentation
        |
        v
  build one scene
        +--> vessel cutaway: levels, interface, weir, demister, nozzles
        +--> pipeline: tube coloured by temperature, pressure or holdup, low points
        +--> layout: equipment coloured by utilisation
        +--> process area: equipment, valves, routed piping with a stream value
        +--> a NeqSim ProcessSystem or a DEXPI P&ID, drawn as it is
        +--> tie-in scope: existing grey, new blue, modified orange
        |
        v
  read the caption  ->  every assumed thickness, exaggeration and enlarged
                        diameter is listed; facts reconciled with the study
        |
        v
  draw with the tool that fits
        +--> PyVista   PNG with labels, legend and caption
        +--> CadQuery  STEP, STL, glTF
        +--> OpenSCAD  editable .scad
        +--> Blender   Cycles render
        |
        +--> OpenFOAM  fields of a solved case: surface, cut plane, clip, streamlines
        |              vessel wetted volume as STL for a mesher
        v
  figure + caption + validation checklist  ->  human review
```

A tool that is not installed is not a blocker: the agent still writes the
generated script and gives the command to run it elsewhere.

## Loaded skills

- `neqsim-engineering-3d-illustration`
- `neqsim-cfd-coupling`, `neqsim-fem-coupling`, `neqsim-separator-modelling`,
  `neqsim-pipe-route-profile`, `neqsim-subsea-layout-geometry` (as relevant)
- From the NeqSim main repository, as relevant: `neqsim-pid-process-operations`,
  `neqsim-dexpi-conformance-validation`, `neqsim-plant-layout-study`,
  `neqsim-plant-layout-geometry`, `neqsim-capacity-and-utilization-analysis`,
  `neqsim-engineering-design-package`

## Typical requests

- "Draw a cutaway of the inlet separator with the levels from the simulation."
- "Show the flowline temperature along the route and mark the low points."
- "Give me a 3D picture of the process area with the valves and piping, coloured
  by utilisation and stream temperature."
- "Draw this process model in 3D and show the new booster compressor as the tie-in."
- "Turn this DEXPI P&ID into a 3D picture."
- "Export the scrubber as a STEP file."
- "Make figures of the velocity field from the OpenFOAM bend case."
- "Render the separator for the front page of the report."

## Human review

Required. Every figure is handed over with its caption and a validation
checklist, and a qualified engineer compares it with the calculation it
illustrates before it is issued.

See `AGENT.md` for the full workflow, inputs, outputs and limitations.
