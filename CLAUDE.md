# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the App

```bash
python app.py
```

Starts a Flask development server at http://localhost:5000 with debug mode enabled.

## Architecture

Minimal Flask app with two routes:
- `/` → `templates/index.html` — static landing page
- `/calculator` → `templates/calculator.html` — interactive 3D calculator

All calculator logic is client-side JavaScript in `calculator.html`. The Flask backend only serves templates — there is no API layer, database, or server-side processing.

### Calculator State Machine (`calculator.html`)

The calculator maintains four state variables:
- `current` — the number currently being entered
- `stored` — the left-hand operand held between operations
- `operator` — the pending operation (`+`, `-`, `*`, `/`)
- `justCalc` — flag to detect whether `=` was just pressed (clears state on next digit)

Key functions: `compute()` performs arithmetic, `fmt()` formats numbers with exponential notation for overflow, `highlightOp()` updates the active operator button styling.

The 3D tilt effect is driven by `mousemove` events on the calculator body, using CSS `perspective` and `rotateX`/`rotateY` transforms.

## Dependencies

No `requirements.txt` exists. The only dependency is Flask (`pip install flask`).
