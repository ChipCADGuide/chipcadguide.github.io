---
title: AND Gate
parent: Python Path
nav_order: 1
---

# AND Gate with Python

## Build steps

1. Create a new script `and2_1um_py.py`.
2. Load openCellLibrary and create `and2_1um_py`.
3. Place PMOS/NMOS devices in pull-up/pull-down arrangement.
4. Route/connect `A`, `B`, `Y`, `VDD`, `VSS`.
5. Export `and2_1um_py.gds`.

```python
from opencelllibrary import Library

lib = Library("openCellLibrary")
and2 = lib.new_cell("and2_1um_py")

and2.place(lib.cell("PMOS_1UM"), x=0, y=12)
and2.place(lib.cell("PMOS_1UM"), x=12, y=12)
and2.place(lib.cell("NMOS_1UM"), x=0, y=0)
and2.place(lib.cell("NMOS_1UM"), x=12, y=0)

for net in ["A", "B", "Y", "VDD", "VSS"]:
    and2.route(net)

and2.write_gds("and2_1um_py.gds")
```
