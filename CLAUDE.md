# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

A vanilla HTML/CSS/JS Tic-Tac-Toe game. No build system, no package manager, no dependencies.

## Running the Game

Open `index.html` directly in a browser — no server required. For a local dev server:

```bash
npx serve .
# or
python3 -m http.server
```

## Architecture

Everything lives in a single file: `index.html`.

- **HTML** — game board (9 `.cell` divs), status display, scoreboard, reset button.
- **CSS** — all styles inline in `<style>`. Uses CSS custom properties (`--glow-x`, `--glow-o`, etc.) for the neon color theme. Animations are CSS-only.
- **JS** — all logic inline in `<script>` at the bottom:
  - `board[]` — 9-element array, `null | 'X' | 'O'`
  - `currentPlayer`, `gameOver`, `scores{}` — top-level state
  - `handleClick(index)` → `checkWinner()` / `checkDraw()` → `endGame()` / `switchPlayer()`
  - Win detection uses a static `WINS` array of all 8 combinations (3 rows, 3 cols, 2 diagonals)
  - `drawWinLine()` injects an SVG element over the board to animate the winning line
  - `resetGame()` tears down all DOM mutations and resets state (scores persist across resets)

## Docs

- `docs/plans/PRD.md` — product requirements
- `docs/plans/IMPLEMENTATION_PLAN.md` — original build plan (4 phases: HTML → CSS → JS → testing)
