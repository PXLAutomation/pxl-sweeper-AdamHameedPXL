# IMPLEMENTATION_PHASE1.md

## Phase 1: Project Setup

### Purpose
This blueprint captures the exact implementation strategy for Phase 1: setting up the static game shell and local build/test entrypoints. It is intentionally narrow: establish the browser-ready HTML/CSS/JS scaffold plus the repository-level package metadata required by the project constraints.

---

## 1. Architectural Design

### Data structures and state definitions
Phase 1 is primarily scaffolding, so the focus is on the initial static structure and a minimal runtime state container for future phases.

- `GameState`
  - `active` | `won` | `lost`
  - Used later by `main.js` to represent whether the game logic may run.

- `config` object
  - `gridSize: number` — fixed 10 for the initial default.
  - `mineCount: number` — fixed value for future phases.

- `domRefs` object
  - `gridContainer: HTMLElement`
  - `statusLabel: HTMLElement`
  - `resetButton: HTMLElement`

### Function signatures
Design minimal entrypoint functions so Phase 1 establishes the proper shape for later expansion.

- `function initGame(): void`
  - Called on module load.
  - Prepares static UI references and logs readiness.

- `function bindUI(): void`
  - Connects future event listeners.
  - In Phase 1 it may be a placeholder.

- `function renderShell(): void`
  - Ensures the grid container exists and can be styled.
  - Can optionally validate DOM structure.

- `function verifyLoad(): void`
  - Prints a console message to confirm the script is loaded successfully.

### File contract for future phases
Phase 1 should leave the codebase with the following structure and responsibilities clearly separated:

- `index.html`: page skeleton, header text, reset button placeholder, and the grid container placeholder.
- `styles.css`: page-level layout, grid container styles, and basic reset.
- `main.js`: startup script with minimal initialization logic and a simple load indicator.
- `package.json`: project metadata and a runnable `npm test` script.

---

## 2. File-Level Strategy

### Files to touch

1. `index.html`
   - Responsibility: page skeleton and DOM placeholders.
   - Include: `<header>`, `<section id="game">`, `<div id="grid"></div>`, `<button id="reset-button">Reset</button>`, and script/style links.

2. `styles.css`
   - Responsibility: global layout, centered viewport, and grid container styling.
   - Include: minimal reset, body centering, grid container dimensions, and a visual target for the tile area.

3. `main.js`
   - Responsibility: runtime entrypoint, initialization functions, and a console verification signal.
   - Include: `initGame()`, DOM lookups, and readiness logging.

4. `package.json`
   - Responsibility: repository metadata, ES module declaration, and test script.
   - Include: `type: "module"`, `scripts.test`, and minimal package identity fields.

---

## 3. Atomic Execution Steps

For each Phase 1 TODO item, this section breaks the work into Plan → Act → Validate.

### [ ] Create `index.html` with header and grid container div
- Plan
  - Define a lean HTML shell with a centered header and empty `#grid` placeholder.
  - Reference `styles.css` and `main.js`.
- Act
  - Create `index.html` with `<head>` metadata and `<body>` containing a header, status row, `div#grid`, and module script tag.
- Validate
  - Open `index.html` in a browser.
  - Confirm the page renders the header and an empty grid area.
  - Confirm there are no network or syntax errors in the browser console.

### [ ] Create `main.js` with basic console log to verify loading
- Plan
  - Add a small JS module that logs a ready message on import.
  - Add a bootstrap call such as `initGame()`.
- Act
  - Create `main.js` with `function initGame() { console.log('PXL Sweep loaded'); }` and invoke it.
- Validate
  - Refresh `index.html` in the browser.
  - Confirm the console shows the exact load message.
  - Confirm the script is fetched successfully without 404s.

### [ ] Create `styles.css` with grid container styling
- Plan
  - Define body centering and a fixed-size layout for the game shell.
  - Add a visible placeholder style for `#grid` so the grid region is obvious.
- Act
  - Create `styles.css` with a simple reset, body flex centering, and `#grid` styling.
- Validate
  - Refresh `index.html` and confirm the styles apply.
  - Verify the `#grid` block is centered and clearly visible.
  - Confirm no CSS parse errors in the browser.

### [ ] Create `package.json` with `type: 