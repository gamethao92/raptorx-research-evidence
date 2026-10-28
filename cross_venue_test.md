# Cross-venue replication test of the report's own indicator values
Executed 2026-10-28T14:12Z. Question under test: **can the numbers printed in the SOL 15m report be reproduced from public data?** The v2 report is timestamped `2026-10-27T21:07Z`, which falls inside every feed's 200-bar window, so this is a direct like-for-like check.

## Method
- RSI(14) is scale-free, so it is the clean replication target: the report prints the last nine values as **45 → 48 → 52 → 58 → 62 → 65 → 60 → 55 → 50**.
- Series tested: 15m closes for the 8 most liquid **Base** SOL pools (Aerodrome/Aero, PancakeSwap, Uniswap; USDC / WETH / cbBTC quotes) from GeckoTerminal, plus **Binance SOLUSDT** and **OKX SOL-USDT** klines.
- For each series: RSI(14) Wilder on closes up to the bar containing 21:07Z (bar open 21:00Z), take the last nine values, compare element-wise. Offsets of 0–5 bars were also scanned in case of a bar-alignment difference.
- MACD(12,26,9) histogram computed on the same closes for context (sign is comparable even though the report's magnitudes are normalised).

## Result at the report's bar (21:00Z)

| Series | Close | RSI last 9 (mine) | Max error vs report | Best error any offset | MACD hist |
|---|---|---|---|---|---|
| Aero SOL/USDC ($490k liq) | $100.58 | 49.8 55.1 58.7 51.3 51.5 49.4 46.4 48.8 49.8 | **15.6** | 9.6 (−3 bars) | −0.084 |
| Aerodrome SOL/USDC ($130k) | $100.56 | 50.9 50.1 53.3 53.1 53.2 50.7 54.7 49.5 50.2 | 14.3 | 11.8 (−1) | −0.041 |
| PancakeSwap SOL/USDC ($69k) | $100.54 | 50.4 49.4 53.1 59.1 52.4 50.4 53.8 49.5 49.5 | 14.6 | 8.9 (−2) | −0.044 |
| Uniswap SOL/USDC ($62k) | $100.23 | 56.5 57.0 56.7 53.7 54.1 55.6 50.5 50.5 49.2 | 11.5 | 8.0 (−4) | −0.035 |
| PancakeSwap SOL/cbBTC ($726k) | $100.96 | 58.1 55.8 58.4 58.0 58.5 62.2 52.6 55.6 54.5 | 13.1 | 8.0 (−5) | −0.020 |
| Aero SOL/cbBTC ($549k) | $101.09 | 55.8 54.0 56.0 55.8 57.2 53.3 51.9 54.8 56.8 | 11.7 | 9.1 (−1) | −0.019 |
| PancakeSwap SOL/WETH ($495k) | $101.04 | 58.1 55.3 57.1 58.5 58.9 54.6 50.1 52.7 56.1 | 13.1 | 8.5 (−5) | −0.028 |
| Aero SOL/WETH ($38k) | $100.99 | 61.1 55.3 57.1 57.6 58.1 54.9 50.1 52.5 54.7 | 16.1 | 7.6 (−5) | −0.032 |
| Binance SOLUSDT | $101.11 | 56.8 56.0 59.8 57.6 58.2 55.5 51.7 53.6 55.4 | 11.8 | 8.2 (−5) | −0.026 |
| OKX SOL-USDT | $101.10 | 56.8 56.0 59.9 57.9 58.3 55.6 51.8 53.6 55.2 | 11.8 | 8.2 (−5) | −0.027 |

Report: `45 48 52 58 62 65 60 55 50`, histogram `−0.001 → +0.002` ("just flipped positive"), MACD line `0.003` vs signal `0.001`.

## What the test shows

- **No series reproduces the printed RSI path.** Every candidate sits 7.6–16.1 RSI points away on at least one of the nine values, and the *shape* is wrong: the report's series climbs to 65 and then falls monotonically to 50, while every real series stays inside a 48–62 band with a different peak position.
- **The MACD sign is inverted.** The report says the histogram just flipped positive (+0.002); on all ten series at that bar the histogram is negative (−0.019 to −0.084).
- **The mismatch is not a quote-asset question.** WETH, USDC and cbBTC pools and two centralised exchanges all disagree with the report in the same direction, so the explanation is not "it charted SOL/WETH while claiming SOL/USDC".

## What it does not show (limits, stated plainly)

- TradingView's integration on the platform may aggregate venues in a way none of these single sources does, and its 15m bar alignment may differ from GeckoTerminal's. A different aggregation could in principle produce a different RSI path.
- The test therefore proves **non-reproducibility from public data we could source**, not fabrication.
- Combined with the pattern layer's own disclaimers in the same report ("detection parameters are mismatched to the actual price scale", "target should be disregarded", confidence 9.78%), the honest conclusion is: **the technical layer's provenance is unverified**, and the momentum and pattern layers cannot be treated as independent confirmations of each other — which is exactly the provenance question Q6 asked and the model never answered.

## Reproduce
`data/rsi_replication_2026-10-28.json` holds every series' close, computed RSI sequence, best offset/error, and MACD values. Pool OHLCV: `https://api.geckoterminal.com/api/v2/networks/base/pools/<pool>/ohlcv/minute?aggregate=15&limit=200&currency=usd`; CEX: `https://api.binance.com/api/v3/klines?symbol=SOLUSDT&interval=15m&limit=200` and `https://www.okx.com/api/v5/market/candles?instId=SOL-USDT&bar=15m&limit=200`.
