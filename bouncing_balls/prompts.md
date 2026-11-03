# Project: Bouncing Balls

> - **Files:** bouncing-balls.html
> - **Dates:** 2026-11-03 → 2026-11-03
> - **Defaults:** Kiro · Auto
> - **Status:** prototype
> - **Use:** none yet
> - **Reusability:** artifact TBD · prompt pattern TBD
> - **Tags:** single-file-html, canvas, physics
> - **Takeaway:** A p5.js sandbox of gravity, wall bounces, and elastic ball-to-ball collisions with live sliders.
> - **Story value:** TBD
> - **Surprises:** TBD

# Prompt 1 (p5.js bouncing balls):

> - **Tool:** Kiro · Auto · 2026-11-03
> - **Session:** fresh · attached: CONVENTIONS.md
> - **Verified:** syntax-checked
> - **Human edits:** none

Create a new folder. We are going to start with a project. I want to create a project where it uses p5.js to simulate bouncing balls. Keep it Vanilla HTML, CSS, and JS. Also, follow the CONVENTIONS.md.

## Output 1:

I built [bouncing-balls.html](bouncing-balls.html), a single self-contained file. It pulls p5.js from a CDN and keeps all the HTML, CSS, and JS in the one file. I checked that the markup parses and the p5 script is wired in, but I haven't watched it run in a browser yet.

**The simulation**
- Balls fall under gravity, bounce off all four walls, and collide with each other. Collisions are elastic with mass scaled by ball area, so bigger balls shove smaller ones around.
- A little ground friction and a floor cutoff let balls settle instead of jittering forever when gravity is on.
- Each ball gets a color from a fixed palette and a soft highlight for a bit of depth.

**Controls (top bar)**
- Balls: 1–60, re-seeds the scene.
- Gravity: 0 to 1.0. Set it to 0 for a zero-g, pool-table feel.
- Bounce: restitution from 0.50 to 1.00 (how much energy survives a bounce).
- Trails on/off: trails leave fading streaks; off clears each frame.
- Pause/Play and Reset.

**Interaction**
- Click to drop a new ball, or drag to aim and fling it.
- Space pauses, R resets.

The page follows your light or dark mode and resizes with the window.
