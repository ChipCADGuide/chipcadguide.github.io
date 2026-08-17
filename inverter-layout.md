---
title: 3. Inverter Layout
nav_order: 4
---

# 3. Generate and Route the Inverter Layout

## Create the layout from the schematic

1. Open the inverter `schematic`.
2. Click **Tools → Layout Generation**.
3. Create a new `layout` view from the schematic.
4. Keep **Create m factor instances** enabled.
5. Use the schematic placement method.
6. Click **OK**.

![Create layout dialog](./media/Glade-CreateLayout.png)

Glade places the PCells and shows yellow fly-lines for nets that still need routing.

![Initial generated layout](./media/Glade-CreatedLayout.png)

## Arrange the devices

1. Put the PMOS above the NMOS.
2. Keep the shared gate path short.
3. Keep the drain/output connection short.
4. Put `vdd` at the top and `vss` at the bottom.

![Arranged inverter layout](./media/Glade-ArrangedLayout.png)

## Route

1. Route the common gate with metal/contact as required.
2. Route the common drain to `vout`.
3. Route PMOS source/body to `vdd`.
4. Route NMOS source/body to `vss`.
5. Finish all yellow fly-lines.

![Completed inverter layout](./media/Chip-Completed.png)

## Check the layout

1. Set the grid to **0.25 µm**.
2. Run the CNM25 DRC.
3. Fix every reported violation before continuing.

Optional 3D view:

![3D view of the inverter](./media/Chip3D.png)
