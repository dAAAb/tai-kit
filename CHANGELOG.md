# Changelog

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
- Object real-world scale is best-effort.
