---
title: 1. Install the CNM25 Tools
nav_order: 2
---

# 1. Install the CNM25 Tools

## Download

1. Open the [CNM25 APDK page](http://www.cnm.es/users/pserra/apdk).
2. Download **Glade** for your OS.
3. Download **SpiceOpus** for your OS.
4. Download the **CNM25 APDK** and extract it.

You should have:

```text
apdk/
├── doc/
├── glade/
└── spiceopus/
```

## Windows setup

### Glade

1. Open `apdk/glade/glade.bat` in a text editor.
2. Find:

```bat
set GLADE_HOME=path_to_glade
```

3. Replace `path_to_glade` with your Glade install folder.
4. Save the file.
5. Launch Glade with **`glade.bat`**.

### SpiceOpus

1. Open `apdk/spiceopus/spiceopus.bat`.
2. Find:

```bat
set OPUSHOME=path_to_spiceopus
```

3. Replace `path_to_spiceopus` with your SpiceOpus install folder.
4. Save the file.
5. Launch SpiceOpus with **`spiceopus.bat`**.

> Always launch Glade and SpiceOpus using the APDK `.bat`/`.sh` scripts, not the bare executables.

## Linux setup

1. Edit `apdk/glade/glade.sh` and set `GLADE_HOME` to your Glade install path.
2. Edit `apdk/spiceopus/spiceopus.sh` and set `OPUSHOME` to your SpiceOpus install path.
3. Launch only with those `.sh` scripts.

## Quick check

In Glade, the Library Browser should contain at least:

- `CNM25TechLib`
- `SPICE3Lib`
- `ExampleLib`

Then continue to the inverter.
