# Example Prompts

These prompts use public, synthetic data only. Figures are illustrations of
calculated results and need human review before they are issued.

## Separator Cutaway

```text
Using public synthetic data, draw a cutaway of horizontal separator 20-VA-001: inside diameter 3.0 m, tan-tan length 10.0 m, wall thickness 45 mm, 2:1 elliptical heads, liquid level 1.5 m and water interface 0.6 m above the vessel bottom, a weir 1.3 m high at 78 % of the length, inlet and gas outlet on top, oil and water outlets underneath. Produce an isometric and a front view, a STEP file, and the caption. Report the liquid and water inventory in m3.
```

## Pipeline Result Along the Route

```text
Using public synthetic data, show the temperature along a 30 km, 12 inch tie-back flowline whose seabed profile and calculated temperatures I will paste as distance, elevation and temperature columns. Colour the pipe by temperature, mark the low points, and state the vertical exaggeration and any enlarged diameter in the caption.
```

## Process Area with Valves and Piping

```text
Using public synthetic data, draw a 3D view of a separation and recompression area: a horizontal separator, a suction scrubber, a compressor, a discharge cooler and an oil pump on one deck. Route the gas, discharge and oil lines through a pipe rack at 4.5 m, put a pressure control valve on the gas line, a level control valve on the oil line and a check valve on the pump discharge. Colour the equipment by utilisation and the pipes by stream temperature, and give me an isometric and a top view.
```

## From a NeqSim Model

```text
I have run a NeqSim Separator and a PipeBeggsAndBrills in Python. Read the geometry, level and profiles from the two objects and draw the separator cutaway and the pipeline coloured by pressure. Tell me which values came from NeqSim and which I still have to supply.
```

## OpenFOAM Figures

```text
The cfd-coupling agent has solved and quality-gated an OpenFOAM case for the bend on line 20-P-001. Draw the velocity magnitude on a cut plane and as streamlines, and the pressure on the surface. Put the field range, the time step and the source file in each caption.
```

## Presentation Render

```text
Render the separator cutaway for the front page of the study report with Blender at 1920 x 1080. If Blender is not installed here, give me the render job and the command to run it on my machine. Remind me which figure carries the labels and numbers.
```
