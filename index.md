---
title: Home
nav_order: 1
---

# Chip CAD Guide

A beginner-friendly tutorial site for learning basic `.GDS` chip design flows at around **1 µm** feature sizes.

This guide uses:
- **GDSFactory (Python)** for scriptable layout generation
- **Xschem** for simple schematic capture and netlist-oriented thinking
- **KLayout** for viewing and sanity-checking generated geometry

---

## 0. Prerequisites

1. Install Python 3.10+.
2. Install GDSFactory:

```bash
pip install gdsfactory
```

3. Install KLayout and Xschem from their official releases.
4. Create a working folder for your tutorial files.

> **Screenshot placeholder (KLayout):** KLayout launch screen and loaded technology/layer view.

---

## 1. Tutorial A — Very Simple Diode-Style Structure

This first example focuses on basic geometry operations in a `.gds` file.

### 1.1 Create the layout in Python (GDSFactory)

```python
import gdsfactory as gf

c = gf.Component("diode_like_1um")

# Simple educational geometry, not a fabrication-ready PDK device
active = c << gf.components.rectangle(size=(20.0, 8.0), layer=(1, 0))
n_contact = c << gf.components.rectangle(size=(4.0, 4.0), layer=(2, 0))
p_contact = c << gf.components.rectangle(size=(4.0, 4.0), layer=(2, 0))

n_contact.move((2.0, 2.0))
p_contact.move((14.0, 2.0))

c.write_gds("diode_like_1um.gds")
```

### 1.2 View in KLayout

1. Open `diode_like_1um.gds` in KLayout.
2. Verify shapes and spacing visually.
3. Measure critical dimensions and keep values near the 1 µm learning scale.

> **Screenshot placeholder (KLayout):** Diode-like geometry with layer colors and ruler measurement.

### 1.3 Optional Xschem companion

Create a very simple two-terminal symbol/schematic that conceptually maps to the layout.

> **Screenshot placeholder (Xschem):** Two-terminal diode symbol and net labels.

---

## 2. Tutorial B — Simple AND Gate (Layout-Oriented Intro)

This section introduces a minimal gate-level layout concept.

### 2.1 Draw a simple logic block in Xschem

1. Create an `and2` schematic with labeled pins: `A`, `B`, `Y`, `VDD`, `VSS`.
2. Keep transistor sizing simple and symmetric for teaching purposes.

> **Screenshot placeholder (Xschem):** AND2 schematic with input/output labels.

### 2.2 Build a corresponding block in GDSFactory

```python
import gdsfactory as gf

c = gf.Component("and2_block_1um")

# Educational block-level layout placeholders
pmos_row = c << gf.components.rectangle(size=(30.0, 6.0), layer=(1, 0))
nmos_row = c << gf.components.rectangle(size=(30.0, 6.0), layer=(1, 0))
metal_y = c << gf.components.rectangle(size=(4.0, 14.0), layer=(3, 0))

pmos_row.move((0.0, 10.0))
nmos_row.move((0.0, 0.0))
metal_y.move((26.0, 1.0))

c.write_gds("and2_block_1um.gds")
```

### 2.3 Inspect and annotate

- Open the generated GDS in KLayout.
- Add text labels to identify `A`, `B`, and `Y` routes.
- Keep a table of widths/spacings for repeatability.

> **Screenshot placeholder (KLayout):** AND2 block with highlighted output path.

---

## 3. Tutorial C — Simple Amplifier Block

This section demonstrates a basic analog block progression after logic.

### 3.1 Schematic first (Xschem)

1. Draw a common-source style stage (`VIN`, `VOUT`, `VDD`, `VSS`).
2. Add a resistive/active load according to your educational target.

> **Screenshot placeholder (Xschem):** Basic amplifier schematic and operating point notes.

### 3.2 Layout sketch in GDSFactory

```python
import gdsfactory as gf

c = gf.Component("simple_amplifier_block_1um")

input_device = c << gf.components.rectangle(size=(10.0, 6.0), layer=(1, 0))
load_device = c << gf.components.rectangle(size=(10.0, 6.0), layer=(1, 0))
out_metal = c << gf.components.rectangle(size=(2.0, 10.0), layer=(3, 0))

input_device.move((2.0, 2.0))
load_device.move((16.0, 2.0))
out_metal.move((12.0, 2.0))

c.write_gds("simple_amplifier_block_1um.gds")
```

### 3.3 Verify visually in KLayout

- Confirm that blocks are separated clearly.
- Label `VIN`, `VOUT`, and supply rails.
- Record lessons learned before moving to tighter nodes.

> **Screenshot placeholder (KLayout):** Amplifier block with labeled nodes and dimensions.

---

## 4. Suggested Next Steps

1. Add real design-rule targets for your chosen process.
2. Replace geometric placeholders with true device generators.
3. Add screenshots in each placeholder section.
4. Add downloadable script files per tutorial.

