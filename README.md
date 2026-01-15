# Quantum Volume (Blender Add-on)

[![Watch the video](https://img.youtube.com/vi/Up2ETR4RYWI/hqdefault.jpg)](https://www.youtube.com/embed/Up2ETR4RYWI)


This is a Blender add-on that generates node groups and helpers to visualize harmonic-oscillator-style wavefunctions.

## Features
- Creates Geometry/Shader node groups used to produce wavefunction-like patterns.
- Geo Nodes for: Full wavefunction.
- Material Nodes for: Glass, Backdrop, Light Environment, Point Cloud, Volume.
- Adds entries to Blender's Add Modifier menu for quick access.


## Requirements
- Blender (tested on Blender 5.x). This is a Blender add-on and runs using Blender's bundled Python/runtime; no external pip packages are required.

## Installation
1. Open Blender.
2. Preferences → Add-ons → Install...
3. Select this add-on folder (or a zip containing it) and click Install Add-on.
4. Enable the add-on in the Add-ons list.

Alternatively, copy the folder into Blender's addons directory (usually under `.../scripts/addons/`) and enable it in Preferences.

## Usage
1. Enable the add-on in Blender Preferences.
2. In Object Mode, open the Add / Modifier menu (the add-on appends its operators to the Add Modifier menu).
3. Choose one of the available operator (Full Wavefunction HO) to add the corresponding node groups / objects to the scene.

## License
This project is released under the GNU General Public License v3. See the included `LICENSE` file for full terms.

## Notes
- The code contains automatically-generated node-tree setup for Blender nodes; files may be large.
- If you encounter issues, check the Blender system console for traceback and ensure your Blender version is compatible.

---
If you'd like, I can also add a short example screenshot or a quick tutorial on using the Full Wavefunction operator.

## Living Glass Operator
This add-on includes a `Living Glass` operator that converts a 3D quantum harmonic oscillator wavefunction into a dynamic, glass-like spatial structure. It supports three representation modes and a range of controls to express amplitude, phase, symmetry and motion as form, refraction and animation.

Key controls
- **Quantum numbers:** choose spherical `n, l, m` (integers) to select the eigenstate. Defaults: `n=0, l=0, m=0`.
- **Volume Plot (default: ON):** renders a volumetric density cloud representing |ψ|^2. Fast and memory-friendly.
- **Particle Cloud (toggle):** when `Volume Plot` is off, generates a point cloud of instanced spheres. Each particle's radius (and optionally color) is proportional to local probability density.
- **Abstract Mesh (toggle, default: OFF):** generates an organic mesh from iso-surfaces of the probability density (uses metaballs / volume-to-mesh). Best for sculptural glass forms.
- **Particle Count / Density:** control how many particles are sampled when using the particle cloud representation (reasonable defaults provided for interactivity).
- **Detail / Resolution:** sets sampling resolution for volume and mesh extraction; higher values increase fidelity and cost.
- **Phase & Motion:** animate phase offset or time parameter to produce interference and living motion across the structure.
- **Material Presets:** includes a default glass material and a volumetric shader; you can apply custom materials for different refractive or absorption effects.

Representation notes
- Volume: uses 3D voxel sampling of |ψ(r)|^2 and a volume shader to visualize density. Good for viewport performance and for rendering volumetric glow/softness.
- Particle Cloud:  Particles are instanced spheres (geometry instancing) to keep memory use low.
- Abstract Mesh: extracts an iso-surface of the probability density and applies a smooth, organic surface operation (metaballs or `Volume to Mesh` + remesh). Apply the glass material for a water-like look.

Usage
1. Enable the add-on in Blender Preferences.
2. Run the `Living Glass` operator from the Add/Modifier menu or the add-on panel.
3. Select `n, l, m`, choose `Volume Plot` or untick it to use `Particle Cloud`, or enable `Abstract Mesh` for a sculptural glass object.
4. Adjust `Particle Count`, `Detail`, and `Material` and press `Generate`.
5. Use the `Phase` or `Animate` controls to add dynamic interference and motion.

Performance tips
- For real-time interactivity, keep `Particle Count` and `Detail` moderate (e.g., 2k–20k particles). Increase for final renders.
- Use GPU rendering (Cycles with GPU) for faster refraction/glass renders.
- Use lower voxel resolution while iterating, then increase resolution for final export.



