# Neon Swarm Scanner

A free market scanner you build in about 2 minutes with Gemini 4 Neon in Antigravity. No code: you paste 2 pages and say "build my scanner".

9 agents watch every Nasdaq 100 stock and the top 100 coins, check every chart every hour, and only message you when a setup passes the math.

## What the swarm does

- **8 Hydrogen scouts** split the market and check every chart every hour.
- **4 checks** every setup has to pass: volume, trend, volatility and time of day.
- **Neon** gets only the survivors, recomputes the math itself and kills anything that fails.
- **Sizing first:** every trade is sized before you see it, never more than 1% of your account at risk.
- **Paper money first.** Nothing goes live until you reply `yes` to that exact trade.

## How to use it

1. Open Antigravity and pick Gemini 4 Neon.
2. Paste [`prompt/01-swarm.md`](prompt/01-swarm.md), then [`prompt/02-math-and-rules.md`](prompt/02-math-and-rules.md). Or paste [`PROMPT.md`](PROMPT.md), which is both pages in one file.
3. Say `build my scanner`.
4. Answer its questions (alerts by Telegram or desktop, data keys if a source needs one), then let it run one test scan on paper.

## The math in one look

| Check | Rule |
|---|---|
| Volume | z-score of the last hourly volume vs the previous 20 bars ≥ 2 |
| Trend | price above a rising EMA50 for longs, below a falling EMA50 for shorts |
| Volatility | 20-bar sigma of log returns between its own 20th and 80th percentile (90 days) |
| Time of day | stocks skip 09:30 to 10:00 ET and after 15:45 ET; coins skip their thinnest hours |
| Size | q = 0.01 · E / \|entry − stop\|, stop = 2 × ATR14 |

The full formulas are on page 2.

## Tune it

The thresholds are a starting point, not a secret edge. Change one at a time, run it on paper for at least 30 trades, and compare the weekly reports.

## Important

This is a tool for scanning and paper trading, not financial advice. It promises no returns. Markets can move past any stop, and past scans don't predict future results. Trade live only with money you can afford to lose, through a broker you connect yourself.

MIT License.
