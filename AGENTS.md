# AGENTS.md

## Project

Vanilla HTML5 Canvas + JavaScript (ES6+) Asteroids clone. No framework, no bundler, no dependencies, no build step.

## Commands

- No toolchain configured: no `package.json`, no tests, no linter, no typecheck, no CI.
- Run locally: open `index.html` directly, or `npx serve .` → http://localhost:3000.
- No automated verification available. Manual playtest in a browser is the only check.

## Structure

- `index.html` — page shell only (canvas 800x600 + script tag).
- `game.js` — all game logic in one file: input, entities, state, update/draw loop.
- `favicon.svg` — static asset.

## Gotchas

- `game.js` is loaded as a **classic script** (`<script src="game.js">`, not `type="module"`). Do not add ES module imports/exports without changing the tag.
- Canvas is fixed at **800x600** (`W`/`H` constants in `game.js`); keep in sync with the canvas element size.
- Game loop uses `requestAnimationFrame` with delta-time (`dt` clamped to 0.05s). All updates are dt-based; do not switch to frame-count logic.
- Game states: `'playing' | 'dead' | 'gameover'`. `Space` restarts from the game-over screen.
- World wraps toroidally (edges are continuous).
- Code comments and `README.md` are in **Spanish**; keep new comments consistent.

## Verification

- Before finishing changes: serve (`npx serve .`) and playtest in a browser (rotation, thrust, shooting, collision, splitting, power-ups, game over).
