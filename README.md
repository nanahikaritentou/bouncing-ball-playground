# Bouncing Ball Playground

Submission for the ROBA Labs
[Bouncing Ball Playground](https://creatorhub.robalabs.com/challenges/12) challenge.

The simulation runs inside ROBA Studio's auto-scaffolded MuJoCo viewer.
Pick a scene from the Studio's selector and tweak it from the simulation panel.

## Scenes (`scenes/`)

| Name | Gravity (m/s²) | Bounciness | Notes |
|---|---|---|---|
| `earth_normal` | -9.81 | medium | Baseline rubber ball on Earth |
| `low_gravity` | -1.62 | medium | Moon — long, slow bounces |
| `high_gravity` | -24.79 | medium | Heavy planet — quick decay |
| `super_bouncy` | -9.81 | very high | Stiff elastic, near 1.0 restitution |
| `dead_thud` | -9.81 | very low | Lossy clay-like ball, single thud |

Restitution is encoded in `solref` / `solimp` on the ball geom, since MuJoCo
expresses contact behavior through impedance rather than a direct restitution
parameter.

## Scene format

Each scene lives under `scenes/<name>/scene.xml` and is registered in
`scenes/index.json`. ROBA Studio's `generate_index.py` regenerates the index
from disk, but the file is hand-written here for clarity.

```
scenes/
├── index.json
├── earth_normal/scene.xml
├── low_gravity/scene.xml
├── high_gravity/scene.xml
├── super_bouncy/scene.xml
└── dead_thud/scene.xml
```

## Bonus: standalone demo (`index.html`)

`index.html` is a self-contained Three.js demo (gravity / restitution / damping
sliders) you can open directly in any browser without ROBA Studio:

```bash
python3 -m http.server 8000
# visit http://localhost:8000
```
