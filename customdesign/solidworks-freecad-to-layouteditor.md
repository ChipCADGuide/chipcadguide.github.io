---
title: SolidWorks/FreeCAD to LayoutEditor Workflow
parent: Custom Design Path
nav_order: 1
---

## SolidWorks/FreeCAD to LayoutEditor Workflow

This tutorial is for designs that begin as a complex 3D model or mechanical concept in SolidWorks or FreeCAD and need to be prepared for chip layout work.

## Step 1: Prepare the CAD model

1. Identify the 2D profile that should become the chip geometry.
2. Suppress or hide non-essential 3D details that do not belong in the layout.
3. Make sure the final profile is clean, closed, and dimensionally consistent.

## Step 2: Export to DXF

1. In SolidWorks or FreeCAD, export the selected sketch, face, or outline as `.dxf`.
2. Confirm the export uses the correct units and scale.
3. Prefer simple line and arc geometry over dense splines when possible.
4. If the model includes multiple features, export only the layers or contours you actually need.

## Step 3: Import into LayoutEditor

1. Open LayoutEditor and create a new cell for the imported geometry.
2. Import the `.dxf` file.
3. Check the import scale against a known dimension from the CAD model.
4. Move the geometry onto the correct origin and layer structure for your process.

## Step 4: Prepare for lithography/fabrication

1. Convert imported outlines into the process layers used by your flow.
2. Add alignment marks, frame geometry, and any required labels.
3. Remove stray segments, overlaps, and tiny fragments that could cause fabrication issues.
4. Run DRC-style spacing checks and verify minimum feature sizes.
5. Export the final layout to the format required by your fabrication flow.

## Checklist

- DXF import scale matches the source CAD model.
- Geometry is clean enough for lithography.
- The correct layers are assigned before export.
- Alignment and fabrication markers are present.

**Image placeholders:**

- SolidWorks or FreeCAD model view
- DXF export settings
- Imported geometry in LayoutEditor
- Final fabrication-ready layout
