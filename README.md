# Bouncing Ball Playground

Submission for the ROBA Labs
[Bouncing Ball Playground](https://creatorhub.robalabs.com/challenges/12) challenge.

## Files

- `scene.xml` — MJCF scene: a sphere with a freejoint dropped onto a textured
  ground plane. Gravity, contact stiffness, and impedance are tuned so the ball
  bounces with a realistic decay
- `index.html` — standalone Three.js demo with sliders for gravity, restitution,
  damping and drop height. Useful for offline preview without ROBA Studio

## Run the standalone demo

```bash
python3 -m http.server 8000
# visit http://localhost:8000
```

## MJCF parameters

| Parameter | Where | Effect |
|---|---|---|
| `gravity="0 0 -9.81"` | `<option>` | downward acceleration |
| `solref="0.01 1"` | ball geom | contact time-constant / damping ratio |
| `solimp="0.9 0.95 0.001"` | ball geom | impedance: dmin, dmax, width |
| `mass="0.5"` | ball geom | ball mass (kg) |
| `friction="0.5 0.005 0.0001"` | ball geom | sliding / torsional / rolling |

Higher `solimp` `dmax` (toward 1.0) and lower `solref` first value make the
ball bouncier; raise the floor `friction` first value to kill horizontal slide.
