---
title: Sedra/Smith Two-Stage CMOS Op-Amp
parent: LayoutEditor Path
nav_order: 4
---

## Sedra/Smith Two-Stage CMOS Operational Amplifier (LayoutEditor)

This tutorial targets a two-stage CMOS op-amp topology with:

- **7 MOSFETs**
- **1 compensation capacitor**
- **A basic MOSFET current mirror**

## SchematicEditor build steps

1. Open LayoutEditor and create or open the project folder that will hold the op-amp tutorial files.

Image placeholder: Add a screenshot of the project open in LayoutEditor.

1. Create a new top cell named `sedra_smith_opamp_1um_manual` so the schematic, layout, and simulation artifacts stay grouped.

Image placeholder: Add a screenshot of the new cell creation dialog.

1. Switch to SchematicEditor for that cell before placing any devices, because the op-amp is easier to verify when the topology is clear first.

Image placeholder: Add a screenshot of the blank cell in SchematicEditor.

1. Open the openCellLibrary panel and locate the MOSFET devices, capacitor primitives, and any bias/current-mirror helper blocks available in your library.

Image placeholder: Add a screenshot of the openCellLibrary browser.

1. Place the differential input pair devices first, since they define the front end of the op-amp.

Image placeholder: Add a screenshot of the differential pair placed in the schematic.

1. Add the current-mirror devices that form the active load or bias branch for the first stage.

Image placeholder: Add a screenshot of the current mirror devices placed in the schematic.

1. Add the second-stage gain transistor(s) so the schematic matches the intended 7-MOSFET structure.

Image placeholder: Add a screenshot of the second stage devices placed in the schematic.

1. Place the compensation capacitor between the first-stage output node and the second-stage node so the Miller compensation path is explicit.

Image placeholder: Add a screenshot of the compensation capacitor in the schematic.

1. Add the top-level pins `VINP`, `VINN`, `VOUT`, `VBIAS`, `VDD`, and `VSS`, then wire them to the correct device terminals.

Image placeholder: Add a screenshot showing the named pins and top-level connections.

1. Check the schematic for correct transistor orientation, node naming, and any accidentally floating gates or drains before moving on.

Image placeholder: Add a screenshot of the finished schematic with labels visible.

## LayoutEditor placement steps

1. Switch from SchematicEditor to LayoutEditor for the same `sedra_smith_opamp_1um_manual` cell.

Image placeholder: Add a screenshot of the layout view open for the op-amp cell.

1. Place the differential input pair close together so matching and symmetry are easier to preserve.

Image placeholder: Add a screenshot of the input pair placement.

1. Place the current-mirror devices adjacent to the input stage so the high-impedance first-stage nodes stay compact.

Image placeholder: Add a screenshot of the current mirror placement.

1. Place the second-stage gain device(s) so the output side has a clear route to `VOUT`.

Image placeholder: Add a screenshot of the second-stage placement.

1. Route the shared bias connections and supply connections first so the layout has a stable power and bias backbone.

Image placeholder: Add a screenshot of the bias and supply routing.

1. Route the high-impedance internal node carefully and keep it short to reduce unwanted parasitics.

Image placeholder: Add a screenshot of the internal-node routing.

1. Place the compensation capacitor between the first-stage node and the second-stage node in the layout, matching the schematic intent.

Image placeholder: Add a screenshot of the compensation capacitor placement.

1. Route `VINP` and `VINN` symmetrically into the differential pair so the input path stays balanced.

Image placeholder: Add a screenshot of the symmetric input routing.

1. Route `VOUT` with enough clearance for export and later probing or simulation checks.

Image placeholder: Add a screenshot of the output routing.

1. Add all node labels and then run your spacing/design-rule checks to catch overlaps, shorts, or mismatched symmetry before export.

Image placeholder: Add a screenshot of the labeled, DRC-clean layout.

1. Export `sedra_smith_opamp_1um_manual.gds` when the full layout looks correct.

Image placeholder: Add a screenshot of the export dialog or final GDS output.

## Simulate in LayoutEditor with NGSpice

NGSpice is the best choice for this tutorial because it is widely used, works well with `.op`, `.ac`, and `.tran` checks, and matches the repo's existing simulation flow.

1. Open the schematic or extracted view that corresponds to the op-amp cell so you can build a simulation setup around the real device connections.

Image placeholder: Add a screenshot of the simulation-ready schematic or extracted view.

1. Set up a testbench with the same `VDD` and `VSS` supplies used by the design, then apply the intended bias network at `VBIAS`.

Image placeholder: Add a screenshot of the supply and bias setup.

1. Add a small-signal input source at `VINP` and hold `VINN` at the reference point used by your testbench.

Image placeholder: Add a screenshot of the input stimulus setup.

1. Run an `.op` operating-point check first so you can confirm the bias current, node voltages, and output common-mode level before doing anything more advanced.

Image placeholder: Add a screenshot of the `.op` setup or results.

1. Run an `.ac` analysis next to verify that the two-stage op-amp shows reasonable gain and phase behavior for the tutorial target.

Image placeholder: Add a screenshot of the AC analysis setup or Bode plot.

1. If you want to check settling or stability behavior, run a transient simulation with a small input step or pulse and inspect `VOUT`.

Image placeholder: Add a screenshot of the transient setup or waveform view.

1. Confirm that the bias current mirror is active, the first stage is amplifying, the second stage is driving the output, and the compensation capacitor is producing the expected response.

Image placeholder: Add a screenshot of the final waveform or measurement results.

## Validation checklist

- Confirm total transistor count = 7.
- Confirm one explicit compensation capacitor is present.
- Confirm at least one MOSFET current mirror pair is correctly connected.
- Confirm the input pair is laid out symmetrically.
- Confirm the NGSpice `.op`, `.ac`, or `.tran` results look reasonable for the tutorial target.
- Export `sedra_smith_opamp_1um_manual.gds`.
