# Project: Blackjack

> - **Files:** blackjack.html
> - **Dates:** 2026-11-03 → 2026-11-03
> - **Defaults:** Kiro · Auto
> - **Status:** prototype
> - **Use:** none yet
> - **Reusability:** artifact TBD · prompt pattern TBD
> - **Tags:** single-file-html, canvas, game
> - **Takeaway:** A p5.js blackjack table with a 6-deck shoe, chip betting, and animated card dealing, all in one vanilla HTML file.
> - **Story value:** TBD
> - **Surprises:** TBD

# Prompt 1 (p5.js vanilla blackjack simulation):

> - **Tool:** Kiro · Auto · 2026-11-03
> - **Session:** fresh · attached: CONVENTIONS.md
> - **Verified:** syntax-checked
> - **Human edits:** none

Create a new folder. We are going to start with a project. I want to create a project where it uses p5.js to simulate black jack. Keep it Vanilla HTML, CSS, and JS and ensure it is optimized. Also, follow the CONVENTIONS.md.

## Output 1:

I built [blackjack.html](blackjack.html), a single self-contained file. It pulls p5.js from a CDN and keeps all the HTML, CSS, and JS in the one file. I verified the markup is well-formed and ran the inline JS through `node --check` (syntax OK), but I haven't watched it render in a browser yet.

**The game**
- A 6-deck shoe, shuffled with Fisher-Yates, that auto-reshuffles once it drops below 25% penetration.
- Standard rules: dealer stands on all 17, blackjack pays 3:2, double-down on the first two cards, pushes return the bet. Aces count soft (11) and drop to 1 automatically to avoid busting.
- Bankroll starts at $1000. Bet with $5 / $25 / $100 / $500 chips, then Deal. Bets are capped to the bankroll, and double is only offered when you can cover it.

**Table and cards**
- p5.js canvas draws a felt gradient table with hands centered and overlapping. Cards are vector-drawn (rank + suit pips, red/black suits, a latticed card back for the dealer's hole card).
- Dealing is animated: cards fly in from the shoe corner with an ease-out and a scale-up, staggered so the opening deal reads naturally. The dealer's draw-to-17 plays out one card at a time.
- Live totals show as badges (soft totals flagged), and a result banner reports win / lose / push with color.

**Controls**
- Chip buttons, Clear, Deal/New Hand, Hit, Stand, Double in the top bar. Buttons enable and disable to match the current phase.
- Keyboard: H hit, S stand, D double, Space deal.
- A stats panel shows shoe size and penetration, the current phase, and FPS.

**Optimization**
- Game state is kept in a plain model object, decoupled from a small animation list so dealing can stagger without blocking logic.
- Cards are drawn directly to the canvas each frame (no per-card DOM nodes or images), and the ace-adjustment loop runs only while a hand is over 21, so scoring stays cheap.
