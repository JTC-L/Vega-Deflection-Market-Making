# Vega Deflection Market Making

A single-page trainer for deflection market making in options. One HTML file, no build step, no dependencies beyond two Google Fonts.

**Explanation tab.** Quote depth Q (vega shown per one vega of edge), deflection depth D (vega that moves your vol fair one point), spreads, the OEV view, and how scoring works.

**Practise tab.** A seven-strike board at one expiry. Each game picks a random Q (multiple of 5, 10 to 50) and D (multiple of 5, 1.2 Q to 2.5 Q), implied vol from 15% to 80%, and runs a mix of steps:

- **Market:** quote a bid and offer for a stated size.
- **Sizing:** a customer offers a price; say how many lots you trade (0 if there is no edge).
- **Trade:** the customer hit or lifted you; enter your new vol fair.
- **Vol check:** state your current vol fair.

Sizing is linear (lots = Q × (edge/ν) / ν) or quadratic (position vega = Q × (edge/ν)², so lots = Q × (edge/ν)² / ν), chosen at the start of a game.

Scoring: each step allows three attempts worth 3, 2 or 1 points, multiplied by an accuracy multiplier, so a step pays up to 9. Markets score 3× if both sides are exact, 2× within ν/4 and 1× within ν/2. Sizing scores 3× exact, 2× within 10% and 1× within 20%. Vol scores 3× exact, 2× within 0.10 and 1× within 0.30. A near answer ends the step and shows the exact answer.

Sizes always carry between 0.5 and 2 vega of edge. Board vegas are rounded to 0.05. In OEV view, OEVs are rounded to 0.01 from the true vegas and the ATM straddle vega to a multiple of 0.05.

## Run it

Open `index.html` in a browser. Full screen is available from the header button.
