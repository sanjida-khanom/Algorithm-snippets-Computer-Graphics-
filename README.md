# Algorithm Snippets — Computer Graphics

A collection of classic **computer graphics algorithms** implemented from scratch in Python, with every result plotted using `matplotlib`. These were written as course/lab exercises to understand how rasterization and 2D geometric transformations work at the coordinate level — without letting a graphics library do the math.

## Overview

Each script implements one algorithm end-to-end: it computes the points itself (no built-in drawing primitives), collects them into coordinate lists, and renders the result as a plot so the geometry can be verified visually.

## What's in here

| File | Algorithm | What it does |
|------|-----------|--------------|
| `DDA line algorithm` | Digital Differential Analyzer | Draws a line between two points using incremental floating-point steps along the dominant axis. Wrapped in a `DDA(x0, y0, x1, y1)` function that prints and plots each interpolated point. |
| `Bresenham_line Algorithm` | Bresenham's line drawing | Draws a line using only integer arithmetic via the decision parameter `pk = 2·dy − dx`, updating `pk` at each step to pick the next pixel. Prompts for both endpoints. |
| `Mid_point circle algorithm` | Midpoint circle | Draws a circle from centre `(xc, yc)` and radius `r`. Computes only the first octant using the decision parameter `p = 1 − r`, then mirrors those points into all 8 octants via a `plot8` helper. |
| `Geometric translation` | 2D translation | Takes three triangle vertices plus a translation vector `(tx, ty)` from user input, and plots the original and translated triangle together for comparison. |
| `Translation with multiple coordinate` | 2D translation (vector form) | Translates a hardcoded triangle along a direction vector (`V = 13I + 7J`), demonstrating translation applied across a coordinate list rather than vertex-by-vertex. |
| `Geometric Rotation` | 2D rotation | Rotates a triangle using the rotation matrix (`cos θ`, `sin θ` from the `math` module) and plots the before/after shapes. |

## Concepts covered

- **Rasterization** — converting continuous line/circle equations into discrete pixel positions
- **Incremental vs. integer-only algorithms** — DDA (floating point) compared against Bresenham (integers only, faster)
- **Decision parameters** — the core idea behind both Bresenham and midpoint circle
- **Symmetry exploitation** — 8-way symmetry in the circle algorithm cuts computation by 8×
- **Affine transformations** — translation and rotation applied to polygon vertices

## Requirements

- Python 3.7+
- `matplotlib`

```bash
pip install matplotlib
```

## How to run

The files have no `.py` extension, but the Python interpreter doesn't care — pass them directly:

```bash
python "DDA line algorithm"
python "Bresenham_line Algorithm"
python "Mid_point circle algorithm"
python "Geometric translation"
python "Geometric Rotation"
python "Translation with multiple coordinate"
```

Or rename them first if you want editor syntax highlighting:

```bash
mv "DDA line algorithm" dda_line.py
python dda_line.py
```

### Input

Some scripts prompt on the terminal, others use hardcoded values:

- **Prompt for input:** `Bresenham_line Algorithm`, `Geometric translation`
  ```
  Enter x1: 2
  Enter y1: 2
  Enter x2: 15
  Enter y2: 10
  ```
- **Hardcoded (edit the file to change):** `Geometric Rotation`, `Translation with multiple coordinate`, `Mid_point circle algorithm`

A `matplotlib` window opens with the plotted result. Close it to end the program.

## Notes

- The Bresenham implementation covers the case where `dx > dy` with a positive slope. Lines in other octants would need coordinate swapping/reflection first.
- These are teaching implementations — readability of the algorithm is prioritized over performance and edge-case handling.
