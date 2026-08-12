---
title: 1-Bit Half Adder
parent: LayoutEditor Path
nav_order: 3
---

## 1-Bit Half Adder in LayoutEditor

Build the half adder with two outputs:

- `SUM = A XOR B`
- `CARRY = A AND B`

## SchematicEditor build steps

1. Open LayoutEditor and start a new project or open your existing tutorial project folder.

> **Image placeholder:**
> Add a screenshot of LayoutEditor with the project open.

1. Create a new top cell named `half_adder_1um_manual` so the schematic and layout stay grouped under one design.

> **Image placeholder:**
> Add a screenshot of the new cell creation dialog.

1. Switch to SchematicEditor for that cell so you can assemble the logic before drawing the physical layout.

> **Image placeholder:**
> Add a screenshot of the cell opened in SchematicEditor.

1. Open the openCellLibrary panel and locate the gate building blocks you need for the half adder, especially the XOR and AND logic resources.

> **Image placeholder:**
> Add a screenshot of the openCellLibrary gate list.

1. Place an XOR gate block first, because it defines the `SUM` path.

> **Image placeholder:**
> Add a screenshot of the XOR gate placed in the schematic.

1. Place an AND gate block next, because it defines the `CARRY` path.

> **Image placeholder:**
> Add a screenshot of the AND gate placed in the schematic.

1. Add the top-level input pins `A` and `B`, then connect both pins to the XOR and AND blocks so each logic path receives the same inputs.

> **Image placeholder:**
> Add a screenshot showing `A` and `B` routed to both blocks.

1. Add the output pins `SUM` and `CARRY`, then wire `SUM` to the XOR output and `CARRY` to the AND output.

> **Image placeholder:**
> Add a screenshot showing the two outputs connected.

1. Add `VDD` and `VSS` pins or rails if your openCellLibrary cells require them, and make sure the power names match the library conventions.

> **Image placeholder:**
> Add a screenshot of the power pins or rails in the schematic.

1. Check the schematic for pin naming consistency, missing connections, and any accidental floating nets before you move on.

> **Image placeholder:**
> Add a screenshot of the finished schematic with labels visible.

## LayoutEditor placement steps

1. Switch from SchematicEditor to LayoutEditor for the same `half_adder_1um_manual` cell.

> **Image placeholder:**
> Add a screenshot of the cell opened in LayoutEditor.

1. Place the library-derived XOR and AND blocks into the layout area with enough spacing to allow clean routing.

> **Image placeholder:**
> Add a screenshot of the initial block placement.

1. Align the blocks so input pins are reachable from the left side and output pins are reachable from the right side.

> **Image placeholder:**
> Add a screenshot showing the aligned block arrangement.

1. Route the `A` and `B` nets from the input side to both the XOR and AND blocks, keeping the wires as direct and readable as possible.

> **Image placeholder:**
> Add a screenshot of the input routing.

1. Route the `SUM` and `CARRY` outputs to their pin locations and verify each output is attached to the correct gate.

> **Image placeholder:**
> Add a screenshot of the output routing.

1. Add `VDD` and `VSS` rails or power connections that match the logic blocks used in the design.

> **Image placeholder:**
> Add a screenshot of the completed power routing.

1. Add top-level labels for every pin so the final layout is easy to understand when exported or reviewed later.

> **Image placeholder:**
> Add a screenshot of the labeled layout.

1. Run your spacing and design-rule checks, then fix any overlaps, shorts, or awkward routing before exporting.

> **Image placeholder:**
> Add a screenshot of the DRC-clean layout.

1. Save the final cell and export `half_adder_1um_manual.gds` when the schematic and layout both look correct.

> **Image placeholder:**
> Add a screenshot of the export dialog or final file output.

## Simulate in LayoutEditor

1. Open the extracted or schematic simulation view associated with your half-adder cell.

> **Image placeholder:**
> Add a screenshot of the simulation setup view.

1. Apply pulse sources to `A` and `B` so you can drive the four input cases `00`, `01`, `10`, and `11`.

> **Image placeholder:**
> Add a screenshot of the pulse source configuration.

1. Run the transient simulation.

> **Image placeholder:**
> Add a screenshot of the simulation running or completed.

1. Verify the output behavior against the half-adder truth table.

> **Image placeholder:**
> Add a screenshot of the waveform results.

1. Confirm that `SUM` is high only for `01` and `10`, and that `CARRY` is high only for `11`.

> **Image placeholder:**
> Add a screenshot of the final waveform verification.
