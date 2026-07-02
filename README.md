# Backcountry 4×4

A free-roam browser wheeling game. One self-contained `index.html` — Three.js for rendering, Rapier (WASM) for physics, both loaded from CDN. No build step, no server required.

Four maps — Rolling Hills, High Country (alpine), Red Rock (Utah slickrock), Dune Sea — and two rigs: the Crawler Jeep and a Trophy Truck (pick on the start menu). Every map has a 13-gate race course: press **Enter** to start the countdown, hit the orange gates in order, finish back home; best times are saved.

## Play

Play at **https://cmitt23.github.io/backcountry-4x4/**, or double-click `index.html` (or serve the folder and open it — jump straight into a map with `?biome=desert|mountain|hills`).

- **W A S D** drive · **Space** handbrake · **Shift** nitrous (5 s stints)
- **E / Q** suspension lift up / down — clearance vs. tip-over risk, live
- **X / Z** tire size up / down — bigger tires clear more rock but gear taller; steep climbs on 46s want 4-Lo
- **T** 2WD/4WD · **G** 4-Hi/4-Lo crawler gear
- **C** camera (chase / hood / free orbit — drag to look) · **L** lights
- **Enter** start / cancel the gate race
- **R** flip upright in place · **Backspace** reset to spawn · **H** help · **M** map select · **V** mute

## How it works

- Drive force is traction-limited (**F ≤ μN** per wheel, load from the suspension raycast). Sand demands run-ups; rock crawls. Nothing is scripted — rollover, wheelspin, high-centering all emerge from the rigid-body sim.
- Lift engages long-travel suspension: softer springs, heavier damping, and anti-roll bars that scale with ride height — a fully lifted rig soaks up rough ground and corners flat, at the cost of a taller CG on smooth pavement-style hardpack.
- One `surface(x,z)` function drives physics friction, the baked ground texture, dust color, track depth, and sound — visuals and handling can't disagree.
- Physics runs at a fixed 120 Hz with render interpolation; the terrain collider is built from the exact render-mesh vertices.
- Debug/automation hooks live on `window.GAME` (`stats()`, `drive()`, `tp()`, `flip()`).
