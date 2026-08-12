---
title: 1-Bit Half Adder
parent: LayoutEditor Path
nav_order: 3
---

# 1-Bit Half Adder in LayoutEditor

Build the half adder with two outputs:
- `SUM = A XOR B`
- `CARRY = A AND B`

## Layout steps

1. Create `half_adder_1um_manual`.
2. Place/compose XOR and AND gate blocks.
3. Route `A` and `B` to both logic paths.
4. Route outputs to `SUM` and `CARRY`.
5. Add `VDD`/`VSS` rails and top-level pin labels.
6. Run DRC-style spacing checks used in your tutorial flow.

## Simulate in LayoutEditor

1. Open the extracted/schematic view associated with your half-adder cell.
2. Apply pulse sources to `A` and `B` (00, 01, 10, 11 sequence).
3. Run transient simulation.
4. Verify:
   - `SUM` toggles high only for 01 and 10.
   - `CARRY` toggles high only for 11.

> **Image placeholders:**
> - Half-adder placement/routing
> - Simulation setup dialog
> - Waveforms for `A`, `B`, `SUM`, `CARRY`
