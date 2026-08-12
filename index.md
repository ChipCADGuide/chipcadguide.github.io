---
title: Chip CAD Guide
nav_order: 1
---

# Chip CAD Guide

Welcome! This guide gives you two ways to learn chip layout at ~1 µm:

- **Track A: Python flow**
- **Track B: LayoutEditor flow**

Both tracks use **openCellLibrary** and **FET-based** examples.

---

## 0) Choose your track

### Track A — Python flow
- Best if you like scripting and repeatable design.
- You build geometry and circuits from code.

### Track B — LayoutEditor flow
- Best if you like visual drag-and-drop and hand drawing.
- You build directly in the editor with immediate feedback.

> Tip: You can switch tracks anytime. The project targets are the same.

---

## 1) Common setup (both tracks)

1. Install your chosen toolchain (Python tools or LayoutEditor).
2. Add and enable **openCellLibrary**.
3. Set your working assumptions to **~1 µm** features.
4. Use **FET-based** devices/cells in examples.

**[Image placeholder: setup overview diagram]**

**[Image placeholder: openCellLibrary install/enable screen]**

---

## 2) Diode tutorial

### 2A) LayoutEditor tutorial (draw by hand first)

1. Create a new cell: `diode_1um_manual`.

**[Image placeholder: new cell dialog in LayoutEditor]**

2. Set grid/snap for ~1 µm-friendly drawing.

**[Image placeholder: grid and snap settings panel]**

3. Draw active, diffusion, and contact regions layer-by-layer.

**[Image placeholder: first manual polygon draw]**

4. Add metal routing and labels.

**[Image placeholder: metal layer and label placement]**

5. Run visual checks (overlap/alignment) and save.

**[Image placeholder: completed manual diode cell]**

### 2B) Python tutorial (counterpart)

1. Create a Python script for `diode_1um_py`.
2. Define layers and geometry parameters near 1 µm scale.
3. Programmatically place diffusion/contact/metal shapes.
4. Export the layout and open for quick review.

**[Image placeholder: Python diode script snippet]**

**[Image placeholder: generated diode layout result]**

---

## 3) Simple AND gate tutorial

### 3A) Python version

1. Create `and2_fet_py` with two-input AND behavior.
2. Use openCellLibrary FET-compatible cells/primitives.
3. Route input A, input B, and output with simple metal paths.
4. Export and inspect connectivity.

**[Image placeholder: Python AND gate code snippet]**

**[Image placeholder: Python-generated AND gate layout]**

### 3B) LayoutEditor version (drag-and-drop focus)

1. Create `and2_fet_le` cell in LayoutEditor.

**[Image placeholder: new AND cell in LayoutEditor]**

2. Open openCellLibrary and drag needed FET-based cells into the canvas.

**[Image placeholder: openCellLibrary panel with selected cells]**

3. Drop two input structures and one output structure.

**[Image placeholder: drag-and-drop placement for A/B/output]**

4. Route short interconnects and align to ~1 µm-friendly grid.

**[Image placeholder: routing pass 1]**

5. Name ports and save the finished gate.

**[Image placeholder: finalized AND gate with labels]**

---

## 4) Multi-gate example (slightly larger block)

Goal: combine basic gates into a small educational logic block.

Example block: `Y = (A AND B) OR (C AND D)`

### Python path
1. Instantiate two AND gates and one OR stage.
2. Place blocks with clean spacing.
3. Route internal nets and top-level ports.
4. Export and review.

**[Image placeholder: Python multi-gate netlist/placement snippet]**

**[Image placeholder: completed multi-gate layout from Python]**

### LayoutEditor path
1. Drag-and-drop existing AND/OR cells from openCellLibrary/project library.

**[Image placeholder: selecting reusable gates from library]**

2. Arrange the three gates into a readable floorplan.

**[Image placeholder: initial multi-gate placement]**

3. Route shared nets, then mark A/B/C/D inputs and Y output.

**[Image placeholder: routed multi-gate block]**

4. Save as `logic_block_4in_1out`.

**[Image placeholder: final labeled multi-gate block]**

---

## 5) Simple FET amplifier tutorial (Sedra/Smith style)

Use a compact common-source style learning example at ~1 µm assumptions.

### 5A) Python version

1. Build a simple FET amplifier cell (`cs_amp_fet_py`).
2. Place FET, bias/load elements, and I/O markers.
3. Route gate, drain, source, and supply nets.
4. Export and run a quick visual sanity check.

**[Image placeholder: Python amplifier construction snippet]**

**[Image placeholder: Python-generated FET amplifier layout]**

### 5B) LayoutEditor version

1. Create `cs_amp_fet_le` and open openCellLibrary.

**[Image placeholder: amplifier cell creation screen]**

2. Drag-and-drop FET and support cells.

**[Image placeholder: amplifier devices placed]**

3. Route signal path and bias/supply paths.

**[Image placeholder: amplifier routing stage]**

4. Add labels (`VIN`, `VOUT`, `VDD`, `VSS`) and save.

**[Image placeholder: final labeled amplifier layout]**

---

## 6) Fully custom device flow (microfluidics example)

Use this when geometry is too complex for quick manual drawing.

1. Build the fluidic-layer geometry in **FreeCAD** or **SolidWorks**.
2. Export the geometry as **DXF**.
3. Import DXF into your downstream layout workflow.
4. Align scale/layers, then integrate with the rest of the chip design.

**[Image placeholder: complex microfluidic geometry in CAD tool]**

**[Image placeholder: DXF export options panel]**

**[Image placeholder: imported DXF inside layout workflow]**

**[Image placeholder: fluidic layer aligned with chip-level context]**

Why DXF here?
- It is a practical bridge from mechanical/CAD geometry into layout tooling.
- It keeps complex custom contours accurate and editable.

---

## 7) Suggested learning rhythm

For every module:

1. Do one short step.
2. Capture/check one visual.
3. Do the next short step.
4. Capture/check the next visual.

This keeps progress simple, fast, and beginner-friendly.
