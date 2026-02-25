# Stopwatch Page - PRD

## 1. Project Overview
Add a functional stopwatch page to the existing yami-workflow-test project, providing users with a timing utility alongside the existing Tic-Tac-Toe game. The stopwatch will feature start/stop/reset functionality with a UI that matches the existing neon cyberpunk aesthetic.

## 2. User Experience

### 2.1 Navigation
- Add a simple toggle/tab system in the header area to switch between "TIC·TAC·TOE" and "STOPWATCH" views
- Smooth transition between views (hide/show mechanism)
- Preserve game state when switching views

### 2.2 Stopwatch Display
- Large, prominent time display (HH:MM:SS.ms format)
- Match the Orbitron font family and neon glow styling
- Centering consistent with existing game board

### 2.3 Controls
- **Start/Stop Button**: Toggle between running and stopped states
- **Reset Button**: Reset time to 00:00:00.00 (stops if running)
- Match existing button styling (neon hover effects, gradient backgrounds)

### 2.4 Lap Functionality (Optional Enhancement)
- Lap time recording with display below main timer
- Clear laps button

## 3. Functional Specification

### 3.1 State Management
- \`isRunning\` (boolean): Track stopwatch state
- \`elapsedTime\` (number): Milliseconds elapsed
- \`startTime\` (number): Timestamp when started
- \`lapTimes\` (array): Array of recorded lap times
- \`intervalId\`: RequestAnimationFrame or setInterval reference

### 3.2 Core Functions
- \`start()\`: Begin counting time, store start timestamp
- \`stop()\`: Pause counting, preserve elapsed time
- \`reset()\`: Clear all time to zero, stop if running
- \`recordLap()\`: Capture current time to lap array (optional)
- \`formatTime(ms)\`: Convert milliseconds to display format

### 3.3 Timer Precision
- Use \`performance.now()\` or \`Date.now()\` for accuracy
- Update display every 10ms for smooth milliseconds animation

## 4. Tailwind Integration

### 4.1 Approach
- Add Tailwind CSS via CDN to index.html (simplest for single-file project)
- Use Tailwind for layout primitives (flex, grid, spacing, typography)
- Keep custom CSS for neon effects, animations, and theme consistency

### 4.2 Tailwind Classes to Use
- \`flex\`, \`flex-col\`, \`items-center\`, \`justify-center\` for layout
- \`gap-4\`, \`p-4\`, \`m-4\` for spacing
- \`text-6xl\`, \`text-8xl\` for timer size
- \`font-mono\` for time display
- \`rounded\`, \`border\`, \`px\`, \`py\` for buttons

## 5. Acceptance Criteria

### Visual
- [ ] Stopwatch view matches existing neon aesthetic
- [ ] Fonts (Orbitron, Share Tech Mono) consistent with game
- [ ] Button hover effects match existing style
- [ ] Responsive on mobile devices

### Functional
- [ ] Start button begins timer
- [ ] Stop button pauses timer (preserves time)
- [ ] Reset button clears time to zero
- [ ] Time displays in HH:MM:SS.ms format
- [ ] Switching between Tic-Tac-Toe and Stopwatch works smoothly
- [ ] Game state preserved when switching views
