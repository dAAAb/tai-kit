# Posters

The v0.1 release ships with one canonical A0 poster
([`assets/v0.1/tai-kit-v0.1-poster.png`](../assets/v0.1/tai-kit-v0.1-poster.png))
and a small gallery of **exploration variants** that document the design
process. All artwork is A0 (2384 × 3371 pt), MIT-licensed, free to print or
remix.

## Honesty note about the exploration gallery

The single canonical poster shows **the actual 100 items in v0.1**.

The exploration variants under [`assets/v0.1/posters/`](../assets/v0.1/posters/)
were rendered earlier in the day, from a **pre-curation candidate pool of 100
items** that overlapped with the final release by only ~5 items. Around 95 of
the items shown in any exploration poster are *not* in the released kit. They
are preserved here as design-process artefacts, not as item indices.

If you need a poster that depicts the released kit verbatim, use the canonical
one. If you want to look at how the layout/rotation/palette decisions were
made, the gallery is for you.

---

## Canonical release poster

| | |
|---|---|
| File | `assets/v0.1/tai-kit-v0.1-poster.png` (and `.pdf`) |
| Layout | 10 × 10 grid, A0 portrait |
| Render style | Per-item 3-axis Euler tumble, full mesh, color PBR |
| Item set | Final v0.1 (100 items, `tk_0001`–`tk_0100`) |

![Canonical v0.1 poster](../assets/v0.1/tai-kit-v0.1-poster.png)

The canonical poster picks the tumble rotation (each tile is rotated freely on
three axes) because it shows silhouette variety across all 100 cells while
still reading as a single composition.

---

## Exploration gallery

All eight exploration sets below live in
[`assets/v0.1/posters/`](../assets/v0.1/posters/) as PNG + PDF.

### 01 — Baseline

![exploration-01-baseline](../assets/v0.1/posters/exploration-01-baseline.png)

First pass. Single-view renders, no per-tile rotation, default lighting.
Establishes the 10 × 10 grid and the A0 page geometry that every later
variant inherits. Used as the visual control.

### 02 — 3D perspective

![exploration-02-3d](../assets/v0.1/posters/exploration-02-3d.png)

Same grid, but each tile is shot from a fixed three-quarter camera. Reads
more like a product catalogue page. Dropped because the unified camera
angle masked the silhouette differences between objects.

### 03 — Rhythmic (v2)

| Color | Mono |
|---|---|
| ![v2 rhythmic color](../assets/v0.1/posters/exploration-03-rhythmic-color.png) | ![v2 rhythmic mono](../assets/v0.1/posters/exploration-03-rhythmic-mono.png) |

First rotation experiment. Per-tile azimuth follows a deterministic wave
across the grid, producing a horizontal "breathing" pattern. Color variant
keeps the PBR texture; mono variant flat-shades to test composition without
material noise.

### 04 — Upright (v3)

| Color | Mono |
|---|---|
| ![v3 upright color](../assets/v0.1/posters/exploration-04-upright-color.png) | ![v3 upright mono](../assets/v0.1/posters/exploration-04-upright-mono.png) |

Y↔Z axis swap plus an azimuth wave. Snaps every item to a recognisably
upright pose (cups stand, plates lie flat), which makes the grid read as a
product taxonomy. This is the rotation later reused for the per-item
preview thumbnails shipped in `assets/v0.1/previews/`.

### 05 — Radial (v4)

| Color | Mono |
|---|---|
| ![v4 radial color](../assets/v0.1/posters/exploration-05-radial-color.png) | ![v4 radial mono](../assets/v0.1/posters/exploration-05-radial-mono.png) |

Each tile rotated toward the grid centre, so the whole composition leans
inward. Strong as a single image but loses the "catalogue of items"
reading; treated as a poster-only layout, not a preview format.

### 06 — Upright, full mesh (v3 + full)

| Color | Mono |
|---|---|
| ![v3 upright full color](../assets/v0.1/posters/exploration-06-upright-fullmesh-color.png) | ![v3 upright full mono](../assets/v0.1/posters/exploration-06-upright-fullmesh-mono.png) |

Same rotation as 04, but rendered against the *full* triangulated mesh with
no decimation (~13 s per tile). Edges are sharper and silhouettes are
cleaner under print, at the cost of render time. Compare to 04 to see the
sub-sampling cost.

### 07 — Radial, full mesh (v4 + full)

| Color | Mono |
|---|---|
| ![v4 radial full color](../assets/v0.1/posters/exploration-07-radial-fullmesh-color.png) | ![v4 radial full mono](../assets/v0.1/posters/exploration-07-radial-fullmesh-mono.png) |

Same as 05 but full-mesh. Same trade-off as 06.

### 08 — Tumble, full mesh (v5)

| Color | Mono |
|---|---|
| ![v5 tumble full color](../assets/v0.1/posters/exploration-08-tumble-fullmesh-color.png) | ![v5 tumble full mono](../assets/v0.1/posters/exploration-08-tumble-fullmesh-mono.png) |

Three-axis Euler tumble — each tile gets an independent random pose. Loses
the upright pose-as-taxonomy of 06 but gains the strongest visual rhythm.
The mono version reads almost like a typography specimen. The color
variant became the basis for the canonical release poster (after the item
set was re-curated to the final 100).

---

## Design notes

A few decisions are constant across every variant:

- **Grid:** 10 × 10, A0 portrait (2384 × 3371 pt). Each cell is square.
- **Render size:** 600 × 600 px per tile before composition.
- **Background:** flat off-white. No drop-shadows; the mesh's own AO does
  the lifting.
- **Type:** kept off the grid itself; metadata is set in the bottom margin.
- **Color palette:** PBR materials as-rendered; no global tint. The "mono"
  variants use flat shading with no texture, so material differences
  disappear and silhouette dominates.

### Why three rotation strategies?

Each strategy answers a different question:

- **Upright (v3)** — *what objects are these?* (pose-as-taxonomy)
- **Radial (v4)** — *what do these look like as a single image?*
  (composition-first)
- **Tumble (v5)** — *what is the silhouette variety in this collection?*
  (variety-first)

The release picks tumble because the kit's interest is in the *spread*
across categories, not in any single object's identity.

---

## Reusing the poster

All posters are MIT licensed. You may print, remix, redistribute, or use
them commercially. Attribution to TAI KIT is appreciated but not required.

The general image-to-3D pipeline that produced the per-item meshes is
described in [METHODOLOGY.md](METHODOLOGY.md). The poster compositor
itself is a thin layer on top (per-tile camera + grid layout); it isn't
part of the v0.1 release surface.
