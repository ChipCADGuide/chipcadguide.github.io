---
title: 1-Bit Half Adder
parent: Python Path
nav_order: 2
---

# 1-Bit Half Adder with Python

Target logic:
- `SUM = A XOR B`
- `CARRY = A AND B`

## Build steps

1. Create `half_adder_1um_py.py`.
2. Place/connect XOR and AND subcircuits in one top-level cell.
3. Expose pins `A`, `B`, `SUM`, `CARRY`, `VDD`, `VSS`.
4. Export `half_adder_1um_py.gds`.

## Simulate with Python + NGSpice

Use Python to run a small NGSpice transient simulation and validate the truth table.

```python
import subprocess
from pathlib import Path

deck = Path("half_adder_tb.sp")
deck.write_text("""
* Half adder transient testbench (placeholder)
VDD VDD 0 1.8
VA A 0 PULSE(0 1.8 0n 1n 1n 20n 40n)
VB B 0 PULSE(0 1.8 0n 1n 1n 40n 80n)
.tran 1n 160n
.control
run
plot v(A) v(B) v(SUM) v(CARRY)
.endc
.end
""")

subprocess.run(["ngspice", "-b", str(deck)], check=True)
```

### What to check

- `SUM` is high for `01` and `10` only.
- `CARRY` is high for `11` only.
- Timing of outputs matches the expected propagation behavior.
