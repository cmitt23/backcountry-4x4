# Backcountry 4×4

A free-roam browser wheeling game. One self-contained `index.html` — Three.js for rendering, Rapier (WASM) for physics, both loaded from CDN. No build step, no server required.

## Play

Double-click `index.html` (or serve the folder and open it — jump straight into a map with `?biome=desert|mountain|hills`).

- **W A S D** drive · **Space** handbrake · **Shift** nitrous (5 s stints)
- **E / Q** suspension lift up / down — clearance vs. tip-over risk, live
- **T** 2WD/4WD · **G** 4-Hi/4-Lo crawler gear
- **C** camera (chase / hood / free orbit — drag to look) · **L** lights
- **R** flip upright in place · **Backspace** reset to spawn · **H** help · **M** map select · **V** mute

## How it works

- Drive force is traction-limited (**F ≤ μN** per wheel, load from the suspension raycast). Sand demands run-ups; rock crawls. Nothing is scripted — rollover, wheelspin, high-centering all emerge from the rigid-body sim.
- One `surface(x,z)` function drives physics friction, the baked ground texture, dust color, track depth, and sound — visuals and handling can't disagree.
- Physics runs at a fixed 120 Hz with render interpolation; the terrain collider is built from the exact render-mesh vertices.
- Debug/automation hooks live on `window.GAME` (`stats()`, `drive()`, `tp()`, `flip()`).
