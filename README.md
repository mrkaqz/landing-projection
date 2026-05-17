# Landing Projection — Directional Drilling

A browser-based calculator for projecting directional drilling surveys to a target depth (TD) using the **Minimum Curvature Method**.

Built for directional drillers and MWD engineers who need a fast, no-install tool to plan and verify the last leg of a horizontal well.

---

## Features

- **Minimum Curvature calculation** — industry-standard dogleg severity and build/turn rate computation
- **Three-station output** — Actual Survey → Projected Last Survey → Projection to TD
- **Interactive TD slider** — scrub the target depth ±100 ft/m with live recalculation
- **D&I sensor offset** — automatically accounts for sensor-to-bit distance and stick-up
- **DLS severity badge** — colour-coded dogleg severity (green / yellow / red) per leg
- **Dual unit support** — switch between imperial (ft, deg/100ft) and metric (m, deg/30m or deg/10m) at any time
- **Footage callout cards** — instant read of Bit → Proj Survey and Bit → TD distances
- **Zero dependencies** — single HTML file, runs entirely in the browser

---

## Usage

Open `index.html` in any modern browser — no server or installation required.

### Inputs

| Field | Description |
|---|---|
| Last Actual Survey | Depth, inclination, and azimuth of the most recent MWD survey |
| D&I Offset | Distance from the D&I sensor to the bit |
| Stick Up | Kelly/top-drive stick-up height above the rotary table |
| Current Bit Depth | Measured depth of the bit right now |
| Projected Last Survey | Expected inc/azi at the projected survey station (depth auto-calculated) |
| TD Specification | Target measured depth, inclination, and azimuth |

### Outputs

- **Build Rate** — change in inclination per unit depth (deg/100ft or deg/30m)
- **Turn Rate** — change in azimuth per unit depth
- **DLS** — Dogleg Severity via Minimum Curvature, colour-coded by severity
- **Footage** — distance drilled for each leg

---

## Files

| File | Description |
|---|---|
| `index.html` | Main application — self-contained, no build step |
| `Landing Projection.xlsx` | Reference spreadsheet with equivalent calculations |

---

## Method

Dogleg angle is computed using the spherical geometry formula:

```
cos(DL) = cos(I2 - I1) - sin(I1)·sin(I2)·(1 - cos(ΔAz))
```

DLS is then:

```
DLS = DL / ΔMD × unit_multiplier
```

This matches the SPE Minimum Curvature convention used in most directional drilling software.

---

## Development

Developed by [ronnarong.dev](https://www.ronnarong.dev) · Version 1.1 · Co-authored with Claude Code
