# Vega Deflection Market Making

A single-page trainer for deflection market making in options. One HTML file, no build step, no dependencies beyond two Google Fonts.

**Explanation tab.** Quote depth Q (vega shown per one vega of edge), deflection depth D (vega that moves your vol fair one point), linear and quadratic sizing, spreads, the OEV view, order implied volatility mode, and how scoring works.

**Practise tab.** A seven-strike board at one or two expiries. Each game picks a random Q (multiple of 5, 10 to 50) and D (multiple of 5, 1.2 Q to 2.5 Q), implied vol from 15% to 80%, and runs a mix of steps:

- **Market:** quote a bid and offer for a stated size.
- **Sizing:** a customer offers a price; say how many lots you trade (0 if there is no edge).
- **Trade:** the customer hit or lifted you; enter your new vol fair.
- **Vol check:** state your current vol fair.

Sizing is linear (lots = Q × (edge/ν) / ν) or quadratic (position vega = Q × (edge/ν)², so lots = Q × (edge/ν)² / ν), chosen at the start of a game.

Scoring: each step allows three attempts worth 3, 2 or 1 points, multiplied by an accuracy multiplier, so a step pays up to 9. Accuracy is judged by vega: an answer is worked back to the ν that would make it exactly right, and scores 3× within 10% of the true ν, 2× within 20% and 1× within 30%. A market's width and centre are both checked. A vol check with no trade scores 3× exact, 2× within 0.10 and 1× within 0.30. An answer that scores but isn't exact ends the step and shows the exact answer.

**Story.** Each game the market vol follows a path with at most one turn, at an uneven pace. Customers lean towards it, and a chart at the end shows it against the vol you carried.

**Clock.** 30 seconds per step, shown top centre. Running out ends the game; finishing early adds 3 points per full 10 seconds left.

**Order implied volatility mode.** No D. On your first or second market, a big customer arrives: they trade through one side of it if it scored (not if it scored 0), and leave large orders 0.5 to 1.5 vol points from the starting vol, shown on the board as 5.25 bid or 5.60 offer with the size, e.g. (x500), as a subscript. Later big orders follow the session's story. Rebase to the latest one and quote so it is your hedge. Each market allows three attempts; a sensible market (right width for Q, and the big order on the hedging side) scores 3, 2 or 1 by attempt, and one still not sensible after three gets traded on unless it was only too wide. A live PnL is marked at the latest big order's vol.

**Two expiries.** Optional second board on the same future and starting vol. Boards sit side by side across the top, questions below.

Sizes always carry between 0.5 and 2 vega of edge. Board vegas are rounded to 0.05. In OEV view, OEVs are rounded to 0.01 from the true vegas and the ATM straddle vega to a multiple of 0.05.

## Run it

Open `index.html` in a browser. Full screen is available from the header button.
