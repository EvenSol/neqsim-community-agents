# Example: Separator Cutaway and Process Area Illustration

Public, synthetic data only. This walks through what the agent does for two
common requests and what it hands back. Human review is required before any
figure is issued.

## 1. Separator cutaway

**Request.** A cutaway of separator 20-VA-001 for a tie-in study report, plus a
STEP file for the layout group.

**Inputs collected**

| Input | Value | Source |
|---|---|---|
| Inside diameter | 3.0 m | Synthetic datasheet |
| Tan-tan length | 10.0 m | Synthetic datasheet |
| Wall thickness | 45 mm | Synthetic datasheet |
| Heads | 2:1 elliptical | Synthetic datasheet |
| Liquid level | 1.5 m above vessel bottom | Synthetic simulation result |
| Water interface | 0.6 m above vessel bottom | Synthetic simulation result |
| Weir | 1.3 m high at 78 % of length | Synthetic datasheet |

**Purpose and backend.** Report figure -> PyVista. CAD exchange -> CadQuery.

**Facts reconciled with the study**

| Fact | Value |
|---|---|
| Total volume | 77.8 m3 |
| Liquid volume at 1.5 m (half full) | 38.9 m3 |
| Water volume at 0.6 m | 10.8 m3 |

**Caption handed over**

> 20-VA-001 - horizontal vessel. ID 3.00 m x T/T 10.00 m, elliptical 2:1 heads.
> Liquid shown on the inlet side of the weir only. Front half cut away to show
> the inside. Nozzles shown as stubs at schematic positions. Drawn to scale.
> Illustration of calculated results - not a design or fabrication drawing.

**Delivered.** Isometric and front PNG, caption text, STEP, STL and glTF, and the
CadQuery script that built them.

## 2. Process area

**Request.** One picture of the separation and recompression area showing where
the capacity is used and how hot each line runs.

**Inputs collected.** Five equipment items with footprint position, size and
utilisation; six pipe runs with corner points, outside diameter and stream
temperature; four inline valves with tag, position along the run and kind.

**What the agent checks before drawing**

- Tags are unique, and every pipe run that carries a value has the unit stated.
- Routes go through the pipe-rack elevation, so no run passes through equipment.
- Utilisation is stated as a utilisation *of what* for each item.

**Caption handed over**

> Separation and recompression - process area. 5 equipment items, 6 pipe runs,
> 4 valves. Pipe colour: Temperature [C], 35 to 142. Colour by utilisation:
> green <= 0.70, amber 0.90, red >= 1.00. Equipment and valves shown as envelope
> shapes; pipe routes as supplied. Drawn to scale. Illustration of calculated
> results - not a design or fabrication drawing.

**Delivered.** Isometric and top PNG with tags, percentages and temperatures as
labels; STEP and OpenSCAD models; optionally a Blender render, which carries no
labels and accompanies the labelled figure.

## Review checklist

- [ ] Every number in the figures traces to the study.
- [ ] Captions are placed with the figures, including "not to scale" notes.
- [ ] The figures are described as illustrations, not design drawings.
- [ ] A qualified engineer has compared each figure with its calculation. This
      example does not replace engineering judgement.
