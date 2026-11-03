# Project: Minecraft Terrain

> - **Files:** minecraft-terrain.html
> - **Dates:** 2026-11-03 → 2026-11-03
> - **Defaults:** Kiro · Auto
> - **Status:** prototype
> - **Use:** none yet
> - **Reusability:** artifact TBD · prompt pattern TBD
> - **Tags:** single-file-html, canvas, data-viz
> - **Takeaway:** A p5.js WEBGL voxel world where layered 3D Perlin noise drives a blocky, Minecraft-styled heightmap with biomes, water, and trees.
> - **Story value:** TBD
> - **Surprises:** TBD

# Prompt 1 (p5.js 3D Perlin noise Minecraft terrain):

> - **Tool:** Kiro · Auto · 2026-11-03
> - **Session:** fresh · attached: CONVENTIONS.md
> - **Verified:** syntax-checked
> - **Human edits:** none

Create a new folder. We are going to start with a project. I want to create a project where it uses p5.js to perlin noise in 3D. I want to make it Minecraft Simulation themed and that accurately represents Minecraft. Keep it Vanilla HTML, CSS, and JS and ensure it is optimized. Also, follow the CONVENTIONS.md.

## Output 1:

I built [minecraft-terrain.html](minecraft-terrain.html), a single self-contained file. It pulls p5.js from a CDN and keeps all the HTML, CSS, and JS in the one file. I verified the markup is well-formed and ran the inline JS through `node --check` (syntax OK), but I haven't watched it render in a browser yet.

**The world**
- The terrain is a voxel heightmap generated from layered 3D Perlin noise (4-octave fractal Brownian motion). The third noise dimension is driven by the seed, so "New Seed" walks to a fresh slice of the noise field instead of reseeding mid-draw.
- Blocks use Minecraft-accurate color approximations: grass with a dirt side, dirt, stone, sand/sandstone, snow, gravel, bedrock at the floor, mycelium, logs, and leaves.
- Water fills everything below the sea level as one translucent sheet; shorelines read as sand or gravel.
- Trees/features are biome-specific: oak blobs, stacked spruce cones, desert cacti, and giant red mushrooms.

**Biomes**
- Plains, Desert, Snowy Tundra, Extreme Hills (with snow caps), and Mushroom Fields. Each has its own surface block, filler, feature type, roughness, and sky tint.

**Controls (top bar)**
- Biome selector, Size (grid 16–56), Hills (vertical amplitude), Sea level.
- Trees on/off, Spin on/off, New Seed.
- Drag to orbit, scroll to zoom, WASD / arrow keys to pan. Space toggles spin, R reseeds.

**Optimization**
- The whole terrain is baked into a single `p5.Geometry` once per regen, so `draw()` issues one GPU call for the land instead of thousands of `box()` calls.
- Hidden-face culling: only block tops and the faces exposed toward a shorter neighbor are emitted, which cuts triangle count sharply.
- Per-face directional shading approximates Minecraft's ambient lighting, and a live stats panel shows seed, grid, triangle count, tree count, and FPS.
