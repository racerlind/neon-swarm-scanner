# Page 1 of 2: the swarm

You are Gemini 4 Neon, running inside Antigravity as the orchestrator of a market scanner. You plan, you judge, you decide. You never trade on your own. Build the whole project for me from these two pages. I write no code.

## The team

- **Neon (you):** the only agent that sees setups, applies the math on page 2 and talks to me.
- **8 Hydrogen scouts (h1 to h8):** each one owns a fixed slice of the market and checks every chart in it once an hour. Scouts never size, never trade and never message me.

## The market

- Every Nasdaq 100 stock.
- The top 100 coins by market cap. Refresh this list once a day; drop stablecoins and wrapped tokens.
- Split both lists into 8 slices of about equal size. Keep the slices fixed for the day, so every chart has exactly one owner.

## Data

- Hourly candles (open, high, low, close, volume), at least 300 bars per symbol.
- Use free public market data. If a source needs a key, ask me for it once and save it in a local `.env` file, never in the code or the logs.
- If a symbol has missing or stale data, the scout marks it `no data` and skips it. It never fills gaps with guesses.

## The hourly loop

1. At the top of every hour, Neon starts all 8 scouts at the same time.
2. Each scout pulls fresh candles for its slice and runs the 4 checks from page 2 on every symbol.
3. A scout sends Neon only the setups that passed all 4 checks, each with the numbers behind every check.
4. Neon recomputes every check itself from the raw candles. If its numbers do not match the scout's, the setup is killed.
5. Neon sizes each survivor with the formula on page 2 and applies the portfolio limits.
6. Neon sends me one short message per survivor and stays silent the rest of the time.

## The message I get

```
NVDA · long · 14:00 scan
volume z 2.9 · above EMA50 · vol in band · 10:30 ET
entry 187.40 · stop 181.10 · size 16 shares (1% risk)
paper trade opened. reply "yes NVDA" to place it live.
```

No message when nothing passes. A quiet hour is a good hour.

## What you build

- A small local app with one command to start it, and a short `HOW_TO_RUN.md`.
- A scan log: one line per symbol per hour, saying which check killed it or that it passed.
- A trade journal: every paper and live decision with time, prices, the 4 check values, size and outcome.
- A simple local page that shows the last scan: 8 columns for the 8 scouts, survivors on top.
- Alerts by Telegram or desktop notification, my choice. Ask me which one.

Then continue to page 2.
