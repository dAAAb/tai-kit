# Changelog

## Unreleased — 2026-05-14

- Added an A0 poster exploration gallery: 14 variants (8 design rounds, color
  + mono pairs where applicable) under `assets/v0.1/posters/`, documented in
  [`docs/POSTERS.md`](docs/POSTERS.md). The variants depict a pre-curation
  candidate pool, not the released 100 items — see POSTERS.md for the
  honesty note. The canonical poster at `assets/v0.1/tai-kit-v0.1-poster.png`
  remains the only one aligned with the released item set.

## v0.1.0-beta — 2026-04-21

First beta release.

- 100 selected 3D models across 24 functional categories
- Mobile-optimized GLB format (mesh + PBR texture)
- Bilingual metadata (English + Traditional Chinese)
- A0 hero poster (`assets/v0.1/tai-kit-v0.1-poster.png`)
- MIT licensed, generic-only naming to avoid disclosing any specific product

**Known limitations**
- Low source resolution (single thumbnail per object) yields some reconstruction
  artifacts: occasional floor plates, back-side hallucination, and texture
  fragmentation under non-trivial UV unwrapping.
- Material labels are heuristic (detected from visual cues + keywords); treat
  as approximate.
- Real-world dimensions (`dimensions_cm` in metadata) are provided for 92/100
  items; 8 items lack source dimension data.
