# Implementation Plan - Tic-Tac-Toe Win Modal

## Phase 1: HTML Structure
- Add modal overlay div (class: modal-overlay)
- Add modal container div (class: modal) with:
  - Victory heading (h2: "VICTORY!")
  - Winner text (p: "Player X Wins!" or "Player O Wins!")
  - Winner symbol display (animated X or O)
  - Score summary display
  - "Play Again" button

## Phase 2: CSS Styling
- Add modal overlay styles:
  - Fixed position, full screen, semi-transparent background
  - z-index: 100, display: none by default
  - backdrop-filter: blur(4px)
- Add modal container styles:
  - Centered with flexbox, max-width: 400px
  - Background: dark (#0a0f14), border with accent glow
  - Padding: 2rem, border-radius: 8px
- Add modal animations:
  - .modal-overlay.open: display: flex, fade in
  - .modal: scale from 0.9 to 1, opacity 0 to 1
  - Winner symbol: pulsing glow animation
- Add button styles:
  - Match existing reset-btn style
  - Hover glow effect

## Phase 3: JavaScript Logic
- Add DOM references:
  - modalOverlay, modal container elements
  - modalWinnerText, modalWinnerSymbol elements
  - modalScoreX, modalScoreO, modalScoreD elements
- Modify endGame(result) function:
  - When result.player exists (win, not draw):
    - Update modal winner text ("Player X Wins!" / "Player O Wins!")
    - Set modal winner symbol class (x or o) with animation
    - Update score display in modal
    - Show modal with .open class
  - When result is null (draw): do nothing (no modal)
- Add closeModal() function:
  - Hide modal (remove .open class)
  - Call resetGame()
- Add event listeners:
  - "Play Again" button click -> closeModal()
  - modalOverlay click (event.target === overlay) -> closeModal()
  - document keydown (Escape) -> if modal open, closeModal()
- Add focus management:
  - On modal open, focus "Play Again" button
  - Ensure keyboard trap within modal

## Phase 4: Testing & Refinement
- Test: Modal appears on X win
- Test: Modal appears on O win
- Test: Modal does NOT appear on draw
- Test: "Play Again" button resets game correctly
- Test: Clicking overlay resets game
- Test: Escape key resets game
- Test: Score persists after modal closes
- Test: Responsive design on mobile
- Test: Animations are smooth
- Verify no console errors
