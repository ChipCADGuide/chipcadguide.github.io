---
title: Home
nav_order: 1
---

# Chip CAD Guide

A brain-friendly tutorial track for **~1 µm** `.gds` design.

You can learn each topic in two ways:
1. **LayoutEditor path** (draw and place by hand)
2. **Python path** (script-based generation)

We use **openCellLibrary** cells and **FET-based** examples.

---

## 0) Quick Setup

### Step 1 — Install tools
- Install **LayoutEditor**
- Install **Python 3.10+**
- Install your preferred GDS Python package

> **Image placeholder:** LayoutEditor installed and opened.

### Step 2 — Prepare openCellLibrary
- Download/open your openCellLibrary files
- Keep all work at a **1 µm teaching scale**

> **Image placeholder:** openCellLibrary files/folders visible.

### Step 3 — Create a project folder
- Make one folder for diode, AND gate, amplifier, and custom-device files

> **Image placeholder:** clean project folder structure.

---

## 1) Tutorial A — Diode-Like Structure

### A1) LayoutEditor path (draw by hand)

**Step 1:** Create a new cell named `diode_1um_manual`.

> **Image placeholder:** New cell dialog with cell name filled in.

**Step 2:** Draw active area rectangle.

> **Image placeholder:** Active area drawn and dimension labels shown.

**Step 3:** Draw contact regions and place them symmetrically.

> **Image placeholder:** Contact rectangles added.

**Step 4:** Add metal pads for two terminals.

> **Image placeholder:** Terminal metal added and colored by layer.

**Step 5:** Label terminals `ANODE` and `CATHODE`.

> **Image placeholder:** Text labels placed on metal.

**Step 6:** Save as `diode_1um_manual.gds`.

> **Image placeholder:** Save/export dialog with file name.

### A2) Python path (openCellLibrary-oriented)

```python
# Example skeleton: adapt to your openCellLibrary/Python environment
# Goal: build a diode-like 2-terminal educational structure at ~1 µm scale

from opencelllibrary import Library

lib = Library("openCellLibrary")
cell = lib.new_cell("diode_1um_py")

cell.add_rect(layer="ACTIVE", x=0, y=0, w=20, h=8)
cell.add_rect(layer="CONTACT", x=2, y=2, w=4, h=4)
cell.add_rect(layer="CONTACT", x=14, y=2, w=4, h=4)
cell.add_rect(layer="METAL1", x=1, y=1, w=6, h=6)
cell.add_rect(layer="METAL1", x=13, y=1, w=6, h=6)

cell.add_label("ANODE", x=2, y=7, layer="TEXT")
cell.add_label("CATHODE", x=14, y=7, layer="TEXT")

cell.write_gds("diode_1um_py.gds")
```

> **Image placeholder:** Python script in editor.
>
> **Image placeholder:** Resulting diode GDS opened in LayoutEditor.

---

## 2) Tutorial B — Simple AND Gate (FET, openCellLibrary)

### B1) LayoutEditor path (drag and drop)

**Step 1:** Create `and2_1um_manual` cell.

> **Image placeholder:** New AND2 cell creation.

**Step 2:** Open openCellLibrary cell browser.

> **Image placeholder:** openCellLibrary browser panel.

**Step 3:** Drag PMOS and NMOS FET cells into layout.

> **Image placeholder:** FET devices placed into PMOS/NMOS rows.

**Step 4:** Route input nets `A` and `B`.

> **Image placeholder:** Input metal routes highlighted.

**Step 5:** Route output net `Y` and power rails `VDD`/`VSS`.

> **Image placeholder:** Completed routing with clear labels.

**Step 6:** Check spacing and keep dimensions near 1 µm learning rules.

> **Image placeholder:** Dimension rulers and spacing checks.

### B2) Python path (compose from openCellLibrary FET cells)

```python
# Example skeleton for scripted AND2 composition from openCellLibrary cells
from opencelllibrary import Library

lib = Library("openCellLibrary")
and2 = lib.new_cell("and2_1um_py")

pmos = lib.cell("PMOS_1UM")
nmos = lib.cell("NMOS_1UM")

and2.place(pmos, x=0, y=12)
and2.place(pmos, x=12, y=12)
and2.place(nmos, x=0, y=0)
and2.place(nmos, x=12, y=0)

and2.route("A")
and2.route("B")
and2.route("Y")
and2.route("VDD")
and2.route("VSS")

and2.write_gds("and2_1um_py.gds")
```

> **Image placeholder:** Python-based cell placement result.
>
> **Image placeholder:** Final AND2 block view with labels.

---

## 3) Tutorial C — Multi-Gate Example (More Advanced)

Build a small logic macro by combining multiple gates.

### C1) LayoutEditor path

**Step 1:** Create `logic_macro_1um_manual`.

> **Image placeholder:** Empty macro cell.

**Step 2:** Drag and drop `INV`, `NAND2`, `AND2` from openCellLibrary.

> **Image placeholder:** Gate instances arranged by rows.

**Step 3:** Connect gates into one useful function (example: `(A AND B) -> INV`).

> **Image placeholder:** Interconnect routing complete.

**Step 4:** Label top-level pins and export GDS.

> **Image placeholder:** Final macro pins and export settings.

### C2) Python path

```python
from opencelllibrary import Library

lib = Library("openCellLibrary")
macro = lib.new_cell("logic_macro_1um_py")

macro.place(lib.cell("AND2_1UM"), x=0, y=0)
macro.place(lib.cell("INV_1UM"), x=40, y=0)

macro.connect("AND2_1UM.Y", "INV_1UM.A")
macro.expose_pin("AND2_1UM.A", "A")
macro.expose_pin("AND2_1UM.B", "B")
macro.expose_pin("INV_1UM.Y", "F")

macro.write_gds("logic_macro_1um_py.gds")
```

> **Image placeholder:** Python macro net connectivity view.

---

## 4) Tutorial D — Simple FET Amplifier (Sedra/Smith Style Intro)

### D1) LayoutEditor path

**Step 1:** Create `cs_amp_1um_manual` cell.

> **Image placeholder:** New amplifier cell.

**Step 2:** Drag one NMOS input device and one load device from openCellLibrary.

> **Image placeholder:** Devices dropped in place.

**Step 3:** Route `VIN`, `VOUT`, `VDD`, `VSS`.

> **Image placeholder:** Routed amplifier nets.

**Step 4:** Add labels and check simple geometry consistency.

> **Image placeholder:** Final labeled amplifier layout.

### D2) Python path

```python
from opencelllibrary import Library

lib = Library("openCellLibrary")
amp = lib.new_cell("cs_amp_1um_py")

amp.place(lib.cell("NMOS_1UM"), x=0, y=0)
amp.place(lib.cell("PMOS_1UM"), x=18, y=10)  # load example

amp.route("VIN")
amp.route("VOUT")
amp.route("VDD")
amp.route("VSS")

amp.write_gds("cs_amp_1um_py.gds")
```

> **Image placeholder:** Python amplifier placement view.
>
> **Image placeholder:** Final amplifier GDS in LayoutEditor.

---

## 5) Fully Custom Device Track — Microfluidics Layer

For complex non-standard geometry (example: microfluidics), CAD-mechanical workflows are often easier.

### Step 1 — Model channel geometry in FreeCAD or Solidworks

> **Image placeholder:** 3D model / sketch of microfluidic channels.

### Step 2 — Export 2D layer to `.dxf`

> **Image placeholder:** Export menu and DXF settings.

### Step 3 — Import `.dxf` into LayoutEditor

> **Image placeholder:** DXF import dialog and scale settings.

### Step 4 — Assign target layers and clean geometry

> **Image placeholder:** Layer mapping panel and cleaned polygons.

### Step 5 — Export final `.gds`

> **Image placeholder:** Final microfluidic mask layer and exported GDS.

---

## 6) What to Add Next

1. Replace placeholders with your screenshots.
2. Add a downloadable file bundle for each tutorial.
3. Add a one-page “common mistakes” section.
