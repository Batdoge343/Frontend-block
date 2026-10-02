# The Last Path

**The Last Path** is a browser-first quantum puzzle game built around one idea: the quantum mechanics is the puzzle.

The Quantum Realm is collapsing because its probability pathways are losing coherence. You are a Pathkeeper. Shape a discrete-time coined quantum walk, use interference to concentrate amplitude at the Heart, and measure only when you can afford the collapse.

## Play

Open `index.html` in a modern browser. No build step, backend, API key, or external service is required. The visual layer uses system fonts, so the core game also works offline.

## Core simulation

The prototype implements a small state-vector simulator specialized for the game:

- complex amplitudes on position + direction channels
- local Grover-diffusion coin on variable-degree grid nodes
- Hadamard mixing for two-way junctions and a 4-way coin
- phase gates (`±π/2`) to change relative phase
- a Markov classical-walk mode for comparison
- probabilistic measurement / collapse
- per-step normalization checks

The renderer is deliberately separate from the simulator. Probability becomes brightness; phase becomes the diagnostic readout; measurement becomes a visible collapse.

## Controls

- **Run Walk** — execute the full walk.
- **Step** — execute one walk step.
- **Peek** — measure the current state, collapsing it and costing 20% coherence.
- **Quantum / Classical** — compare the two models on the same board.
- **Toolkit** — select a tile and click a board node to place it.
- **1–4** — quick-select unlocked tools.

## Project structure

```text
index.html
styles.css
src/
  game.js
  levels.js
  main.js
  quantum.js
  renderer.js
tests/
  level_sanity.js
  quantum.test.js
```

## Test the quantum core

```bash
npm test
```

The test suite verifies normalization in quantum and classical modes, measurement collapse, Hadamard branching, and machine-checked solutions for all five chapters.

## Publish with GitHub Pages

The repository includes a Pages workflow at `.github/workflows/pages.yml`. In the GitHub repository, open **Settings → Pages**, choose **GitHub Actions** as the source, then push/merge to `main`. The workflow publishes the static site.

## Design direction

The game follows the uploaded design brief: five story chapters; quantum random walk + interference + measurement as the central mechanics; a classical/quantum comparison; a measurement-cost mechanic; procedural visuals; a mathematically clean simulator under the graphics layer; and automated solvability/physics checks.

