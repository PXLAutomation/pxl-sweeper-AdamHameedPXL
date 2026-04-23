# REQUIREMENTS.md

## 1. Project Overview
- A single-page web-based game inspired by Minesweeper with a minimal Minecraft-themed visual layer.
- The game replicates core Minesweeper mechanics with at most one minor variation.
- Design philosophy:
  - Simplicity over feature richness
  - Familiar gameplay over innovation
  - Minimal visual theming without impacting usability

---

## 2. Core Gameplay Requirements

### Game Rules
- The game consists of a rectangular grid of hidden tiles.
- A fixed number of mines (TNT) are randomly distributed across the grid.
- The player reveals tiles to avoid mines and clear the board.

### Grid Behavior
- Grid size: fixed (e.g., 10x10 or similar small size).
- Each tile has one of the following states:
  - Hidden
  - Revealed
  - Flagged
- Each tile contains:
  - A mine OR
  - A number indicating adjacent mines (0–8)

### Mine Placement Logic
- Mines are randomly placed at game start.
- The first clicked tile must never contain a mine.
- Adjacent mine counts must be calculated for all non-mine tiles.

### Reveal Mechanics
- Left-click reveals a tile.
- If a revealed tile contains:
  - A mine → immediate game over
  - A number > 0 → display number
  - A number = 0 → recursively reveal adjacent tiles

### Flagging System
- Right-click toggles flag state on a tile.
- Flagged tiles cannot be revealed unless unflagged.

### Win/Lose Conditions
- Win:
  - All non-mine tiles are revealed.
- Lose:
  - A mine is revealed.

---

## 3. Optional Twist

### Resource Tiles (Minimal Variation)
- Non-mine tiles may visually represent resources (e.g., stone, coal, iron).
- This is purely visual and does not affect gameplay logic.
- No additional mechanics (e.g., inventory, upgrades) are introduced.

Constraints:
- No impact on mine logic or reveal behavior
- No additional game systems

---

## 4. User Interface Requirements

### Layout
- Single static screen
- Centered game grid
- Optional header area for status (timer, reset button)

### Grid Rendering
- Grid displayed as a uniform matrix of square tiles
- Clear visual separation between tiles

### Visual States
Each tile must visually represent:
- Hidden (default block appearance)
- Revealed (cleared block)
- Flagged (marker indicator)
- Exploded (mine triggered)

### Feedback
- Immediate visual response on click
- Distinct visual state for win and loss
- Disable interaction after game ends

### Theming
- Minimal Minecraft-inspired styling:
  - Block textures/colors
  - TNT for mines
- No heavy graphics or animations

---

## 5. Functional Requirements

### Input Handling
- Left-click:
  - Reveal tile
- Right-click:
  - Toggle flag
- Prevent default browser context menu on right-click

### Game State Management
- Track:
  - Tile states
  - Mine positions
  - Game status (active, won, lost)

### Reset / Restart
- Reset button restarts the game:
  - Reinitialize grid
  - Re-randomize mines
  - Reset state

### Timer (Optional)
- Start on first click
- Stop on win or loss

### Score Tracking (Optional)
- Time-based score only
- No persistent storage required

---

## 6. Non-Functional Requirements

### Performance
- All interactions must respond within 50ms
- No noticeable delay in tile reveal or recursion

### Simplicity
- Codebase must remain small and readable
- Avoid unnecessary abstraction

### Maintainability
- Clear separation of concerns:
  - Game logic
  - Rendering
  - Input handling

### Responsiveness
- Optimized for desktop browsers
- Basic support for smaller screens (grid remains usable)

---

## 7. Technical Constraints

- Use only:
  - HTML
  - CSS
  - Vanilla JavaScript
- No backend services
- No frameworks (e.g., React, Vue)
- No external libraries unless strictly necessary
- Must run by opening index.html locally

---

## 8. Out of Scope

- Multiplayer functionality
- User accounts or authentication
- Persistent data storage
- Advanced animations
- Sound effects
- Multiple difficulty levels (optional but not required)
- Procedural level design beyond basic randomization
- Mobile-first optimization
- Accessibility features beyond basic usability

---

## 9. Definition of Done

- Game loads and runs in a browser via a single HTML file
- Grid renders correctly and consistently
- Mines are correctly placed with valid counts
- First click is always safe
- Reveal logic (including recursion) works correctly
- Flagging system works without conflicts
- Win and loss conditions trigger correctly
- Reset functionality fully reinitializes the game
- UI clearly communicates all tile states
- No console errors during gameplay
- Code is readable and logically structured

## Project Setup Requirements

- The project shall include a `package.json` file in the repository root.
- The `package.json` file shall define the project's runnable commands in a consistent way.
- The `package.json` file shall include at least a `test` script so the same test command can be run every time.
- If the project uses ES module imports in JavaScript, `package.json` shall set `"type": "module"`.
- The project shall remain compatible with a plain JavaScript, static-site workflow.