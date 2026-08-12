---
title: Sedra/Smith Two-Stage CMOS Op-Amp
parent: Python Path
nav_order: 3
---

# Sedra/Smith Two-Stage CMOS Operational Amplifier (Python)

Implement a two-stage CMOS op-amp with:
- **7 MOSFETs**
- **1 compensation capacitor**
- **A basic MOSFET current mirror**

## Build steps

1. Create `sedra_smith_opamp_1um_py.py` and top cell `sedra_smith_opamp_1um_py`.
2. Instantiate seven MOSFET devices matching your chosen Sedra/Smith-style topology.
3. Wire a MOSFET current mirror for bias/active load.
4. Connect second-stage gain device and output stage node.
5. Add one compensation capacitor between first-stage and second-stage nodes.
6. Expose pins `VINP`, `VINN`, `VOUT`, `VBIAS`, `VDD`, `VSS`.
7. Export `sedra_smith_opamp_1um_py.gds`.

## Optional NGSpice check flow

1. Generate a SPICE netlist from your scripted topology.
2. Run `.op` and `.ac` analyses using NGSpice.
3. Confirm bias currents, output common-mode level, and reasonable gain/phase trend for the tutorial target.
