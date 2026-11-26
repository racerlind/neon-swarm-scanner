# Page 2 of 2: the math and the rules

Every setup must pass all 4 checks on the latest closed hourly bar. One failed check kills it. Log the check that killed it.

## Check 1: volume

```
z_V = (V_t - mean(V, 20)) / std(V, 20)
pass if z_V >= 2
```
V_t is the volume of the latest closed bar; the mean and standard deviation use the 20 bars before it.

## Check 2: trend

```
EMA_t = a * P_t + (1 - a) * EMA_(t-1),   a = 2 / (n + 1),   n = 50
long:  P_t > EMA50_t  and  EMA50_t > EMA50_(t-5)
short: P_t < EMA50_t  and  EMA50_t < EMA50_(t-5)
```
Stocks: long and short. Coins: long only.

## Check 3: volatility

```
r_i   = ln(P_i / P_(i-1))
sigma = std(r, last 20 bars)
pass if Q20 <= sigma <= Q80
```
Q20 and Q80 are the 20th and 80th percentiles of the same sigma over the last 90 days for that symbol. Too calm means no move; too wild means the stop gets hunted.

## Check 4: time of day

- Stocks: no new setups from 09:30 to 10:00 ET, after 15:45 ET, or outside regular hours.
- Coins: no new setups in the hours whose median volume over the last 30 days is in the bottom 20% for that coin.

## Sizing: never more than 1% of the account at risk

```
ATR14 = average true range of the last 14 bars
stop  = entry - 2 * ATR14   (long)      entry + 2 * ATR14   (short)
q     = (0.01 * E) / |entry - stop|
```
E is the account equity. Round q down. Never let one position be worth more than 20% of E.

## Portfolio limits

- At most 3 open trades and at most 3% of E at risk in total.
- At most 2 open trades from the same sector, and only 1 coin at a time besides BTC and ETH.
- If equity drops 5% from its high, stop opening trades and tell me.

## Paper first, then my yes

- Every trade starts on paper. Track it to the stop, to a target of entry plus or minus 3 * ATR14, or to 24 hours, whichever comes first.
- Nothing goes live until I reply `yes` and the ticker for that exact trade. One yes is one trade. Never assume a yes, and never reuse an old one.
- Live trading uses only a broker I connect myself. Never ask for my password and never move money.

## Your report every Sunday

Number of scans, setups found, survivors, paper results (win rate, average R, max drawdown) and which check kills the most setups. If paper results are negative after 30 trades, say so plainly and suggest which threshold to test next. Don't change thresholds yourself.

When both pages are built, run one test scan on paper, show me the log and wait.

Say "build my scanner" to start.
