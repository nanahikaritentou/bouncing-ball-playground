# Bouncing Ball Playground

A minimal MuJoCo-style bouncing ball demo for the ROBA Labs
[Bouncing Ball Playground](https://creatorhub.robalabs.com/challenges/12) challenge.

## Files

- `index.html` — interactive 3D viewer (Three.js, no build step) with sliders
  for gravity, restitution (bounciness), damping, and drop height
- `scene.xml` — equivalent MJCF scene (sphere + ground plane) for MuJoCo

## Run locally

Just open `index.html` in a browser, or:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Controls

| Slider | Range | Effect |
|---|---|---|
| Gravity | 0 – 20 m/s² | downward acceleration |
| Bounciness | 0 – 1 | coefficient of restitution at the floor |
| Damping | 0 – 0.05 | per-step velocity loss (air drag proxy) |
| Drop Height | 0.5 – 5 m | initial ball altitude on Reset |

`Reset` re-drops the ball with a small horizontal nudge.
`Pause` freezes the simulation.

## MJCF mapping

`scene.xml` mirrors the runtime parameters:

- `<option gravity="0 0 -9.81">` ↔ Gravity slider
- `<geom solref="0.01 1" solimp="0.9 0.95 0.001">` ↔ contact stiffness/damping
  (translates to effective restitution)
- `<freejoint/>` on the ball body ↔ 6-DoF rigid body
