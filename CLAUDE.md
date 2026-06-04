# CLAUDE.md

This file provides guidance to Claude Code when working with code in this repository.

## Project

SDM & SOP Practice Games — a platform for hosting interactive learning games for child welfare practitioners. Built as plain HTML/CSS/JavaScript with no build tools, so files can be opened directly in a browser without any setup.

## No build tools

This project uses no npm, no React, no Vite, no bundler. Every file must work when opened as a local file (`file://`) in a browser. Do not add any dependencies that require a server or build step.

## Structure

```
index.html                  # Platform home — links to all games
games/
  [game-name]/
    index.html              # Each game is self-contained in its own folder
SPECS/
  [game-name].md            # One spec file per game
CLAUDE.md
TODO.md
```

## Adding a new game

1. Create a spec in `SPECS/[game-name].md` before writing any code.
2. Create `games/[game-name]/index.html` as a self-contained file.
3. Add a game card to `index.html` linking to the new game.
4. Update `TODO.md` when tasks are completed.

## Rules

### Spec-First Workflow
- Every game or feature must have a spec in `SPECS/` before code is written.
- If a spec is missing, add it first.
- If a feature fits an existing spec, update its Acceptance Criteria before coding.

### TODO Hygiene
- When a TODO is implemented, remove it from `TODO.md`.

### Data storage
- Games may use `localStorage` for persistence (scores, custom questions, game state).
- Use namespaced keys (e.g., `sopjeopardy_scores`) to avoid collisions between games.

### LLM Context
- Do not refer to `README.md` for context. That file is for end users only.
