---
title: Sedra/Smith Two-Stage CMOS Op-Amp
parent: LayoutEditor Path
nav_order: 4
---

# Sedra/Smith Two-Stage CMOS Operational Amplifier (LayoutEditor)

This tutorial targets a two-stage CMOS op-amp topology with:
- **7 MOSFETs**
- **1 compensation capacitor**
- **A basic MOSFET current mirror**

## Layout steps

1. Create `sedra_smith_opamp_1um_manual`.
2. Place the differential input pair devices.
3. Place current-mirror MOSFETs for the active-load/bias branch.
4. Place second-stage gain transistor(s) to complete the 7-MOSFET structure.
5. Route the high-impedance internal node and output path.
6. Place the compensation capacitor between first-stage output node and second-stage node per your schematic intent.
7. Label key nodes (`VINP`, `VINN`, `VOUT`, `VBIAS`, `VDD`, `VSS`) and check symmetry/matching.

## Validation checklist

- Confirm total transistor count = 7.
- Confirm one explicit compensation capacitor is present.
- Confirm at least one MOSFET current mirror pair is correctly connected.
- Export `sedra_smith_opamp_1um_manual.gds`.

> **Image placeholders:**
> - Device floorplan
> - Current mirror routing
> - Capacitor placement
> - Final labeled op-amp layout
