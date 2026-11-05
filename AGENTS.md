# AGENTS.md

## What this repo is

Dependency-free Asteroids clone: `index.html` + all game logic in the single file `game.js`. No package.json, no build, no bundler, no tests, no linter. Don't add a framework or split files unless asked.

## Running / verifying

- Test changes by opening `index.html` in a browser, or `npx serve .` → `http://localhost:3000`. There is no programmatic test or lint step.
- No dev server config or env vars; plain static files.

## Gotchas in `game.js`

- `game.js` is a plain (non-module) script loaded at the end of `<body>`; it runs immediately and looks up `document.getElementById('canvas')`. The `W`/`H` constants (800×600) must stay in sync with the canvas `width`/`height` attributes in `index.html`.
- Space is toroidal: all position updates go through `wrap()`. New moving entities must wrap too, and collision checks near edges won't catch wrapped neighbors (known limitation).
- Size-tuned asteroid constants live in parallel arrays `RADII` / `SPEEDS` / `POINTS` (index 1=small, 2=medium, 3=large). Update them together.

## Conventions

- Code comments, README, and game strings are in Spanish — match that.
- Code is organized under `// ── Section ──` banner comments; place new code in a fitting section or add a new banner.
- ES6+, `'use strict'`, vanilla DOM APIs only.
