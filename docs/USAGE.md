# Usage

All models are **glTF 2.0 binary** (`.glb`) with embedded PBR textures.

## File layout

```
assets/v0.1/
├── models/
│   ├── bowl/tk_0002.glb       # organized by category
│   ├── cup/tk_0007.glb
│   └── ...
├── previews/
│   └── <same layout>.png      # 600px reference renders
├── metadata.json              # all item metadata
└── tai-kit-v0.1-poster.png    # A0 overview
```

## Loading examples

### three.js

```js
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';

const loader = new GLTFLoader();
loader.load('assets/v0.1/models/bowl/tk_0002.glb', (gltf) => {
  scene.add(gltf.scene);
});
```

### Blender

`File → Import → glTF 2.0 (.glb/.gltf)` — textures are embedded.

### Python (trimesh)

```python
import trimesh
m = trimesh.load('assets/v0.1/models/bowl/tk_0002.glb', force='mesh')
print(m.vertices.shape, m.faces.shape)
```

### Unity / Unreal

Use any standard glTF importer (e.g.,
[UnityGLTF](https://github.com/KhronosGroup/UnityGLTF) or
[glTFRuntime for Unreal](https://github.com/rdeioris/glTFRuntime)).

## Querying by category or material

`metadata.json` is a flat JSON array; every entry contains `id`, `name_en`,
`name_zh`, `category`, `tags`, `face_count`, and `extent_m`.

```bash
# All spoons
jq '.[] | select(.category=="spoon")' assets/v0.1/metadata.json

# All stainless steel items
jq '.[] | select(.tags | index("stainless_steel"))' assets/v0.1/metadata.json

# Items under 10k faces
jq '.[] | select(.face_count < 10000) | .id' assets/v0.1/metadata.json
```

## Categories (v0.1)

`bowl`, `cup`, `plate`, `spoon`, `cookware`, `ladle`, `cart`, `jar`,
`pitcher`, `basket`, `chopstick`, `container`, `steamer_insert`, `scrubber`,
`kettle`, `bottle`, `tongs`, `fork`, `spatula`, `lid`, `whisk`,
`honey_dipper`, `strainer`, `torch`, `funnel`.

## Physics / simulation notes

- Meshes are **not** guaranteed to be watertight or manifold. Run a repair
  pass if you need convex decomposition for rigid-body simulation.
- `extent_m` is the axis-aligned bounding box in meters (reconstruction
  frame, not necessarily real-world calibrated).
- Models are **Y-up** (TRELLIS.2 convention).
