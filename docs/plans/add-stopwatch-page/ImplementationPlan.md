# Stopwatch Page - Implementation Plan

## Phase 1: Setup & Navigation

### 1.1 Add Tailwind CDN
- Add Tailwind CSS CDN link to <head> of index.html
- Verify Tailwind is working with test class

### 1.2 Create Navigation Structure
- Add view toggle buttons in header area
- Create stopwatch-view container (hidden by default)
- Add data attributes to track current view

### 1.3 Implement View Switching
- JavaScript function switchView(viewName)
- Toggle visibility of game container and stopwatch container
- Update active state on navigation buttons

## Phase 2: Stopwatch UI

### 2.1 Timer Display
- Create .stopwatch-display element
- Use Orbitron font with large size (clamp for responsiveness)
- Add neon glow effect matching --glow-x color
- Format: 00:00:00.00

### 2.2 Control Buttons
- Create Start/Stop button (toggles text/state)
- Create Reset button
- Style to match existing .reset-btn and .leaderboard-btn

### 2.3 Lap Section (Optional)
- Create lap times container
- Style lap entries with smaller text
- Add clear laps button if needed

## Phase 3: State Management

### 3.1 JavaScript State
\`\`\`javascript
let stopwatch = {
  isRunning: false,
  elapsedTime: 0,
  startTime: 0,
  intervalId: null,
  laps: []
};
\`\`\`

### 3.2 Timer Functions
- startStopwatch(): Set startTime, begin interval
- stopStopwatch(): Clear interval, calculate elapsed
- resetStopwatch(): Reset all values
- updateDisplay(): Format and render time

### 3.3 Display Update
- Use requestAnimationFrame or setInterval(10ms)
- Calculate: currentTime = elapsedTime + (now - startTime)
- Format with padZero helper

## Phase 4: Integration & Polish

### 4.1 Connect Navigation
- Wire up view toggle buttons
- Ensure smooth transitions
- Handle edge cases (stopwatch running when switching)

### 4.2 Visual Refinement
- Add subtle pulsing animation when running
- Match all existing CSS variables
- Test responsive behavior

### 4.3 Testing
- Test start/stop/resume cycle
- Test reset during running
- Test view switching preserves state
- Verify mobile responsiveness
