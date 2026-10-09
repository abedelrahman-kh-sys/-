---
name: video-editor
description: Build, edit, and render short-form vertical reels (TikTok/Reels/Shorts) using HyperFrames, HTML/CSS/JS, and FFmpeg.
---

# Video Editing Skill with HyperFrames & Claude Code

When instructed to edit a video or generate a reel from raw media:

## 1. System Setup & Requirements
- Verify `hyperframes` availability (`npx hyperframes`).
- Verify `ffmpeg` is installed and accessible in system PATH.
- Maintain project file structure:
  - `index.html` (DOM hierarchy & scene video containers)
  - `style.css` (Design tokens, fonts, colors, layouts)
  - `timeline.js` (GSAP animation timelines & state changes)
  - `storyboard.json` (Timecoded scene breakdowns & intent)

## 2. Editing Workflow
1. **Analyze Transcript:** Parse audio transcript timestamps and spoken key concepts.
2. **Generate Storyboard:** Plan cuts, title pop-ins, diagrams, and caption timing based on audio timestamps.
3. **Write Web Code:**
   - Define scene structure & HTML containers in `index.html`.
   - Apply typography, colors, and responsive properties in `style.css`.
   - Program timeline synchronization, captions, zoom cues, and graphic overlays in `timeline.js`.
4. **Render:** Execute `npx hyperframes render` to trigger FFmpeg compilation into `final.mp4`.
5. **Iterate:** Process refinement requests by editing code directly (e.g., adjusting easing curves or timing values).

## 3. Design System & Brand Rules
- **Typography:** High-legibility Sans-Serif fonts (e.g., Inter, Heebo, Montserrat), heavy weight for titles.
- **Captions:** Center-bottom alignment, high-contrast backgrounds/shadows for maximum readability.
- **Motion Vocabulary:** Smooth spring easings (`springEase(0.9)`), rapid pop-in cards for explanatory graphics, jump-cuts on pauses or vocal errors.
